---
title: "Actualizaciones de Aspose.GIS: Editar características y geometrías y guardar los cambios en la base de datos."
type: docs
url: /es/net/showcases/saving-changes-to-database/
description: "Este artículo explora las recientes mejoras en la biblioteca Aspose.GIS, centrándose en las nuevas capacidades para detectar y guardar los cambios de geometría en una aplicación de mapeo."
weight: 80
---
# Actualizaciones de Aspose.GIS: Editar características y geometrías y guardar los cambios en la base de datos.

## Introducción

A la luz de los recientes cambios en la biblioteca [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis), es importante destacar algunos de ellos para que no pasen desapercibidos. En este artículo, discutiremos la nueva capacidad de detectar y guardar cambios a las geometrías y características en la base de datos.

Como ejemplo para demostración, continuaremos trabajando en la aplicación descrita en el artículo ["Dibujar un mapa. Un mapa deslizante con mosaicos"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) y lo expandiremos ligeramente agregando funcionalidades de edición de objetos al mapa. El conjunto de datos sigue siendo el mismo que en el artículo anterior.

## Front-end

Para la demostración de las capacidades de modificación de geometría, elegimos una extensión popular de código abierto para [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/).

Agregamos esta biblioteca a través del archivo libman.json:
![Libman](libman.png)

A continuación, conectamos los estilos y scripts a la página:
```razor
@section Styles {
    <link href="~/lib/leaflet/leaflet.min.css" rel="stylesheet" />
    <link href="~/lib/contagt/leaflet-geoman-free/dist/leaflet-geoman.min.css" rel="stylesheet" />
    <link href="~/css/map.css" rel="stylesheet" asp-append-version="true"/>
}

@section Scripts {
    <script src="~/lib/leaflet/leaflet.js"></script>
    <script src="~/lib/contagt/leaflet-geoman-free/dist/leaflet-geoman.min.js"></script>
    <script src="~/js/map.js" asp-append-version="true"></script>
}
```

Para fines de demostración, limitaremos las capacidades de edición solo a los edificios. El usuario hace clic en el botón izquierdo del mouse en el mapa y, si hay un edificio en esa ubicación, se resalta y se vuelve disponible para editar. Esto se logra superponiendo una capa adicional sobre los mosaicos.

Cuando el usuario hace clic en el mapa, la biblioteca Leaflet calcula las coordenadas geospaciales del clic. Enviamos estas coordenadas al back-end y buscamos en la base de datos geometrías que intersecten con el punto clickeado. Si hay edificios entre estas geometrías, los devolvemos.

Los edificios se devuelven desde el back-end en formato `GeoJSON` y se agregan al mapa como una capa separada para editar. Así es como manejamos el clic:
```javascript
var featuresLayer = L.featureGroup().addTo(map);

map.on('click', function (e) {
    var latlng = e.latlng;
    var featureFound = false;

    console.log(latlng.lat + ' ' + latlng.lng);

    featuresLayer.eachLayer(function (layer) {
        if (layer.getBounds && layer.getBounds().contains(latlng)) {
            featureFound = true;
            return;
        }
    });

    if (!featureFound) {
        loadGeoJSON(latlng.lat, latlng.lng)
            .then((addedFeatureLayer) => {
                if (addedFeatureLayer) {
                    addedFeatureLayer.addTo(featuresLayer);
                    addedFeatureLayer.pm.enable();
                    console.log('Feature added.');
                } else {
                    console.log('No feature to add.');
                }
            });
    }

    featureFound = false;
});
```

Tenemos un grupo de capas persistente para geometrías editables, `featuresLayer`, que se ha agregado al mapa. Verificamos si el clic se realizó en una geometría ya cargada y, si no, hacemos una solicitud al back-end para cargar los polígonos que representan edificios. Las capas de características cargadas se agregan a featuresLayer y se activa el modo de edición. 

Así es como se ve la función para cargar características y convertir desde `GeoJSON`:
```javascript
function loadGeoJSON(lat, lng) {
    return fetch(`/features?lat=${lat}&lng=${lng}`)
        .then(response => response.json())
        .then(data => {
            if (data && data.features && data.features.length > 0) {
                return L.geoJSON(data);
                
            } else {
                return null;
            }
        })
        .catch(error => console.error('Error loading a feature:', error));
}
```

Después de la sesión de edición, el usuario hace clic en un botón `Guardar` personalizado:

![Save](save-btn.png)

Actualiza la página y ve los cambios:

![Changes](changes.png)

Desafortunadamente, la función `tiles.redraw()` no funciona correctamente ya que los mosaicos cargados previamente se almacenan en caché, lo que requiere una actualización forzada del mapa a través de `Ctrl + F5`.

Aquí está el controlador para presionar el botón guardar:
```javascript
function saveResult() {
    if (featuresLayer.getLayers().length === 0) {
        console.log('There are no layers to send to the server.');
        return;
    }
    sendGeoJSONToServer()
        .then(() => {
            console.log('clear and update map');
            featuresLayer.clearLayers();
            tiles.redraw();
        });
}

function sendGeoJSONToServer() {
    var geojsonData = featuresLayer.toGeoJSON();

    return fetch('/features', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/geo+json'
        },
        body: JSON.stringify(geojsonData)
    })
        .then(data => {
            console.log('The data has been successfully sent to the server.');
        })
        .catch(error => {
            console.error('Error when sending GeoJSON:', error);
        });
}
```

## Back-end

Aquí agregamos un nuevo controlador, `FeaturesController`, donde creamos un manejador para extraer casas/características según las coordenadas enviadas. 

La solicitud SQL se ve así:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

Las coordenadas se transforman en un punto, que indica el sistema de coordenadas de la solicitud original del cliente (WGS 84) y luego se traducen al sistema en el que se presentan los datos de la base de datos (Web Mercator). Buscamos intersecciones con este punto para geometrías marcadas como edificios.

La ejecución de la solicitud y el envío de datos al cliente ocurre de manera similar a lo que discutimos en el artículo anterior:
```csharp
VectorLayer inputLayer;

using (var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary"))
{
    var dataSource = Drivers.PostGis
        .FromQuery(query)
        .GeometryField("way")
        .AddAttribute("osm_id", AttributeDataType.Long)
        .AddAttribute("name", AttributeDataType.String)
        .AddAttribute("building", AttributeDataType.String)
        .Build();

    conn.Open();

    inputLayer = await dataSource.ReadAsync(conn);
}

var jsonStream = new MemoryStream();

inputLayer.SaveTo(AbstractPath.FromStream(jsonStream), Drivers.GeoJson);

var result = Encoding.UTF8.GetString(jsonStream.ToArray());

return new ContentResult()
{
    Content = result,
    ContentType = "application/geo+json"
};
```
Con una pequeña diferencia: guardamos nuestra capa InMemory como GeoJSON en la memoria como un stream, luego lo convertimos a una cadena y lo enviamos al cliente.

Ahora llegamos a la esencia de las actualizaciones en Aspose.GIS — guardar los cambios en la base de datos. El método `Edit()` maneja esto. Leemos el cuerpo de la solicitud para cargarlo completamente en la memoria y lo leemos como un stream:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync(); 
Request.Body.Position = 0;
```
A continuación, leemos las características editadas en formato GeoJSON:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
El siguiente paso es que del conjunto de características enviadas, extraemos los atributos que representan los identificadores únicos de las características correspondientes en la base de datos. Formamos una solicitud para poblar una capa especial para editar y construimos la fuente de datos correspondiente:
```csharp
var ids = string.Join(", ", inputLayer.Select(x => x.GetValue<long>("osm_id")));

var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
               FROM public.planet_osm_polygon
               WHERE osm_id IN ({ids});";

var dataSource = Drivers.PostGis
    .FromQuery(query)
    .GeometryField("way")
    .AddAttribute("osm_id", AttributeDataType.Integer, System.Data.DbType.Int64)
    .AddAttribute("name", AttributeDataType.String)
    .AddAttribute("building", AttributeDataType.String)
    .AsTrackableForChanges("public.planet_osm_polygon", "osm_id", true)
    .Build();
```
Tenga en cuenta el método de configuración `AsTrackableForChanges`. Este es un método especial que indica la necesidad de crear una fuente de datos específica capaz de rastrear los cambios. El primer parámetro especifica la tabla a la que se deben enviar las solicitudes de cambio. El segundo indica qué atributo se considerará el identificador para realizar cambios en la base de datos. La parte más interesante es el tercer parámetro. Cuando se establece en True, indica que la capa rastreará la aparición de duplicados según el segundo parámetro y "sobrescribirá" las características previamente cargadas con nuevas. Sin embargo, en caso de resultados de edición, es decir, agregar una nueva característica con el mismo identificador, se generará un comando `UPDATE` según los cambios en comparación con el valor anterior. Si los duplicados aparecen durante la inicialización de la capa desde la base de datos, la capa sobrescribirá silenciosamente los últimos valores. Si el tercer parámetro está configurado como falso, se lanzará una excepción al aparecer duplicados, ya sea durante la inicialización o la edición.

Los nombres de los atributos se utilizarán como nombres de campo en la tabla editable. Es importante tener en cuenta un punto crucial con respecto a la detección de cambios. Es esencial especificar el tipo de datos exacto del atributo que se almacenará en la capa para rastrear los cambios, debe ser preciso con respecto a los tipos recién agregados o modificados. Por ejemplo, si agrega una nueva característica con un `osm_id` de tipo `Int32`, mientras que el tipo de atributo especificado en la capa es `Int64`, esto se tratará como dos valores diferentes ya que no hay sobrecarga del método `Equal`s que parezca `Int64.Equals(Int32)`. En versiones futuras, este comportamiento se revisará y corregirá si es posible. El tipo de parámetro tercero se aplicará durante el guardado de datos como el tipo de datos de destino de la tabla de base de datos.

A continuación, nos conectamos a la base de datos y leemos los datos de la tabla:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
Un punto importante es que para que la transacción funcione correctamente a nivel de base de datos, es necesario pasar la transacción actual como el segundo parámetro durante la operación de lectura.

A continuación, debemos realizar una serie de transformaciones antes de enviar los cambios a la base de datos:
```csharp
var transformer = SpatialReferenceSystem.Wgs84.CreateTransformationTo(SpatialReferenceSystem.WebMercator);

foreach (var feature in inputLayer)
{
    feature.Geometry = transformer.Transform(feature.Geometry);
    ((Geometry)feature.Geometry).HasZ = false;
}

foreach (var feature in inputLayer)
{
    var replacingId = feature.GetValue<long>("osm_id");
    var toReplaceIndex = editLayer.TakeWhile(x => x.GetValue<long>("osm_id") != replacingId).Count();
    editLayer.ReplaceAt(toReplaceIndex, feature);
}

await dataSource.SubmitChangesAsync(editLayer, conn, transaction);

transaction.Commit();
```
Leaflet genera geometrías en el sistema de coordenadas WGS 84, sin embargo, el esquema de la base de datos requiere almacenamiento en Web Mercator. Para transformar al sistema Web Mercator, creamos un objeto `transformer` especial y lo usamos para la conversión.

Además, leaflet llena el tercer parámetro de las coordenadas de la geometría Z con un valor de 0. Sin embargo, este parámetro no se tiene en cuenta en nuestro esquema de base de datos, por lo que eliminamos su presencia configurando el valor de `HasZ` a falso.

El punto final es aplicar cambios reemplazando la característica existente con la recibida del cliente que tenga el mismo osm_id. Esta operación conducirá a la detección de cambios en relación con las instancias anteriores de la característica. En el momento de llamar a `SubmitChangesAsync`, se producirá el proceso de detección de cambios y los comandos INSERT, DELETE y UPDATE se enviarán a la base de datos según sus cambios.

Gracias por leer hasta el final. Todo el código estará disponible en el siguiente repositorio: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)
---