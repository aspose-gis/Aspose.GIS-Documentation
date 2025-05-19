---
title: "Cómo Dibujar Geometría en un Mapa"
type: docs
url: /es/net/how-to-draw-geometry
weight: 70
---

Para crear y mostrar objetos geométricos en un mapa, primero debes **crear un objeto de geometría**. Hay dos métodos que puedes usar:

- **Constructor para Cada Tipo de Característica de Geometría**
Este método implica el uso de un constructor personalizado para cada tipo de característica de geometría. Por ejemplo, para crear un punto, usarías el siguiente código:

```
Point point = new Point(40.7128, -74.006);
```

Sin embargo, este método puede volverse desafiante y engorroso de administrar al crear objetos complejos como polilíneas o colecciones. Como resultado, el desarrollador puede necesitar agregar muchas líneas de código, lo que hace que la legibilidad del código disminuya. Asegurar la integridad de los datos durante la inicialización también puede ser difícil. Por ejemplo, considera el siguiente ejemplo que crea un polígono con un agujero en su interior:

```
Polygon polygon = new Polygon();

LinearRing ring = new LinearRing();
ring.AddPoint(50.02, 36.22);
ring.AddPoint(49.99, 36.26);
ring.AddPoint(49.97, 36.23);
ring.AddPoint(49.98, 36.17);
ring.AddPoint(50.02, 36.22);

LinearRing hole = new LinearRing();
hole.AddPoint(50.00, 36.22);
hole.AddPoint(49.99, 36.20);
hole.AddPoint(49.98, 36.23);
hole.AddPoint(50.00, 36.24);
hole.AddPoint(50.00, 36.22);

polygon.ExteriorRing = ring;
polygon.AddInteriorRing(hole);
```

Otra desventaja de este enfoque es la falta de uniformidad de los datos para la inicialización. No puedes crear un repositorio de constantes o archivos dentro de tu proyecto.

- **WKT (Texto Bien Conocido)**
Este método implica generar geometría desde WKT (Texto Bien Conocido), que ofrece una forma estandarizada de crear geometrías. El siguiente código demuestra cómo crear un punto y una línea:

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

Si bien este enfoque puede reducir ligeramente el rendimiento debido a la necesidad de analizar la cadena, simplifica la creación de objetos más complejos.

Puedes encontrar más detalles sobre WKT en el siguiente artículo: "Exportación e Importación de Datos desde/hacia WKT y WKB".

Mostrar Objetos Geométricos en el Mapa
Una vez que hayas creado un objeto geométrico, el siguiente paso es mostrarlo en el mapa. Si bien el mapa puede mostrar capas cargadas de varias fuentes y formatos, la capa InMemoryLayer es una capa que no requiere una fuente.

**Para mostrar tu objeto geométrico**, puedes crear una InMemoryLayer y agregar el objeto a ella:

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

Ahora puedes **mostrar esta capa en el mapa y crear un archivo en uno de los formatos compatibles**, como SVG, con el siguiente código:

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

Una vez que hayas agregado la capa y la hayas mostrado en el mapa, puedes guardarla en cualquiera de los formatos compatibles. En este ejemplo, se elige el formato SVG para evitar posibles problemas con el soporte de Bitmap. Es importante tener en cuenta que Net 6.0 tiene un soporte limitado de Bitmap, lo que puede resultar en restricciones como la incapacidad de renderizar imágenes de Bitmap utilizando Blazor WebAsm en el lado del cliente. Por lo tanto, al elegir un formato para guardar tu mapa, es importante considerar las limitaciones de la plataforma de destino y seleccionar un formato que sea compatible con ella.

El artículo explica cómo crear y mostrar objetos geométricos en un mapa con un estilo predeterminado y sencillo. Sin embargo, la biblioteca Aspose ofrece una amplia gama de opciones de estilo que se pueden personalizar para adaptarse a tus necesidades. Para explorar estas opciones, te recomendamos consultar la [documentación de Aspose.MapRendering]( https://docs.aspose.com/gis/net/map-rendering/), que proporciona información detallada sobre cómo utilizar diferentes técnicas de estilo para mejorar el atractivo visual de tu mapa.

**En resumen**, para crear objetos geométricos en un mapa, puedes usar un constructor para cada tipo de característica de geometría o generar geometría desde WKT. Para mostrar el objeto, colócalo en una capa y muestra la capa en un mapa con un estilo predeterminado del mapa. Guarda el mapa en un formato compatible, como SVG, y utiliza nuestra biblioteca para explorar las opciones de estilo. Además, nuestra biblioteca proporciona una oportunidad para ver un ejemplo terminado haciendo clic en el [enlace]( https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer) proporcionado en la documentación, lo que puede ayudarte a comprender cómo implementar estas técnicas en tus propios proyectos.
