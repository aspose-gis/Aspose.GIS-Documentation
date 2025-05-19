---
title: "Aggiornamenti Aspose.GIS: Modifica di Feature e Geometrie e salvataggio delle modifiche nel database."
type: docs
url: /it/net/showcases/saving-changes-to-database/
description: "Questo articolo esplora i recenti miglioramenti nella libreria Aspose.GIS, concentrandosi sulle nuove funzionalità per il rilevamento e il salvataggio delle modifiche alla geometria in un'applicazione di mappatura."
weight: 80
---
# Aggiornamenti Aspose.GIS: Modifica di Feature e Geometrie e salvataggio delle modifiche nel database.

## Introduzione

Alla luce dei recenti cambiamenti nella libreria [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis), è importante evidenziarne alcuni per non farli passare inosservati. In questo articolo, discuteremo la nuova capacità di rilevare e salvare le modifiche a geometrie e feature nel database.

Come esempio dimostrativo, continueremo a lavorare sull'applicazione descritta nell'articolo ["Disegna una mappa. Una mappa scorrevole con tile"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) ed espanderemo leggermente aggiungendo funzionalità di modifica degli oggetti sulla mappa. Il dataset rimane lo stesso dell'articolo precedente.

## Front-end

Per la dimostrazione delle capacità di modifica della geometria, abbiamo scelto una popolare estensione open source per [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/).

Aggiungiamo questa libreria tramite il file libman.json:
![Libman](libman.png)

Successivamente, colleghiamo gli stili e gli script alla pagina:
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

A scopo dimostrativo, limiteremo le capacità di modifica solo agli edifici. L'utente fa clic sul pulsante sinistro del mouse sulla mappa e, se c'è un edificio in quella posizione, viene evidenziato e diventa disponibile per la modifica. Questo si ottiene sovrapponendo un ulteriore livello sopra i tile.

Quando l'utente fa clic sulla mappa, la libreria Leaflet calcola le coordinate geospaziali del clic. Inviamosi queste coordinate al back-end e cerchiamo nel database le geometrie che intersecano il punto cliccato. Se ci sono edifici tra queste geometrie, li restituiamo.

Gli edifici vengono restituiti dal back-end in formato `GeoJSON` e aggiunti alla mappa come un livello separato per la modifica. Ecco come gestiamo il clic:
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

Abbiamo un gruppo di livelli persistente per le geometrie modificabili, `featuresLayer`, che è stato aggiunto alla mappa. Verifichiamo se il clic è stato effettuato su una geometria già caricata e, in caso contrario, inviamo una richiesta al back-end per caricare i poligoni che rappresentano gli edifici. I livelli di feature caricati vengono aggiunti a featuresLayer e la modalità di modifica viene attivata.

Ecco come appare la funzione per il caricamento delle feature e la conversione da `GeoJSON`:
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

Dopo la sessione di modifica, l'utente fa clic su un pulsante `Salva` personalizzato:

![Save](save-btn.png)

Aggiorna la pagina e visualizza le modifiche:

![Changes](changes.png)

Sfortunatamente, la funzione `tiles.redraw()` non funziona correttamente poiché i tile caricati in precedenza vengono memorizzati nella cache, richiedendo un aggiornamento forzato della mappa tramite `Ctrl + F5`.

Ecco il gestore per la pressione del pulsante di salvataggio:
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

Qui aggiungiamo un nuovo controller, `FeaturesController`, dove creiamo un gestore per l'estrazione di case/feature in base alle coordinate inviate.

La richiesta SQL è la seguente:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

Le coordinate vengono trasformate in un punto, indicando il sistema di coordinate della richiesta originale del client (WGS 84) e quindi tradotte nel sistema in cui sono presentati i dati del database (Web Mercator). Cerchiamo le intersezioni con questo punto per le geometrie contrassegnate come edifici.

L'esecuzione della richiesta e l'invio dei dati al client avviene in modo simile a quanto discusso nell'articolo precedente:
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
Con una piccola differenza: salviamo il nostro layer InMemory come GeoJSON in memoria come stream, quindi lo convertiamo in una stringa e lo inviamo al client.

Ora arriviamo all'essenza degli aggiornamenti in Aspose.GIS — salvare le modifiche nel database. Il metodo `Edit()` gestisce questo. Leggiamo il corpo della richiesta per caricarlo completamente in memoria e lo leggiamo come stream:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync();
Request.Body.Position = 0;
```
Successivamente, leggiamo le feature modificate in formato GeoJSON:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
Il passo successivo, dall'insieme di feature inviate, estraiamo gli attributi che rappresentano gli identificatori univoci delle corrispondenti feature nel database. Formiamo una richiesta per popolare un layer speciale per la modifica e costruiamo la corrispondente data source:
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
Nota il metodo di configurazione `AsTrackableForChanges`. Questo è un metodo speciale che indica la necessità di creare una data source specifica in grado di tracciare le modifiche. Il primo parametro specifica la tabella a cui devono essere inviate le richieste di modifica. Il secondo indica quale attributo sarà considerato l'identificatore per apportare modifiche al database. La parte più interessante è il terzo parametro. Quando impostato su True, indica che il layer traccerà l'occorrenza di duplicati in base al secondo parametro e "sovrascriverà" le feature precedentemente caricate con quelle nuove. Tuttavia, nel caso dei risultati della modifica, ovvero dell'aggiunta di una nuova feature con lo stesso identificatore, verrà generato un comando `UPDATE` in base alle modifiche rispetto al valore precedente. Se i duplicati compaiono durante l'inizializzazione del layer dal database, il layer li sovrascriverà silenziosamente con l'ultimo valore. Se il terzo parametro è impostato su false, verrà lanciata un'eccezione all'occorrenza di duplicati, sia durante l'inizializzazione che la modifica.

I nomi degli attributi verranno utilizzati come nomi dei campi nella tabella modificabile. È importante notare un punto cruciale riguardante il rilevamento delle modifiche. È essenziale specificare il tipo di dati esatto dell'attributo che verrà archiviato nel layer per il tracciamento delle modifiche, deve essere accurato rispetto ai tipi appena aggiunti o modificati. Ad esempio, se aggiungiamo una nuova feature con un `osm_id` di tipo `Int32`, mentre il tipo di attributo specificato nel layer è `Int64`, questo verrà trattato come due valori diversi poiché non esiste alcun overload del metodo `Equal`s che assomigli a `Int64.Equals(Int32)`. Nelle versioni future, questo comportamento verrà rivisto e corretto se possibile. Il tipo di parametro terzo verrà applicato durante il salvataggio dei dati come tipo di dati di destinazione della tabella del database.

Successivamente, ci connettiamo al database e leggiamo i dati dalla tabella:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
Un punto importante è che affinché la transazione funzioni correttamente a livello di database, è necessario passare la transazione corrente come secondo parametro durante l'operazione di lettura.

Successivamente, dobbiamo eseguire una serie di trasformazioni prima di inviare le modifiche al database:
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
Leaflet genera geometrie nel sistema di coordinate WGS 84, tuttavia lo schema del database richiede l'archiviazione in Web Mercator. Per trasformare nel sistema Web Mercator, creiamo un oggetto `transformer` speciale e lo utilizziamo per la conversione.

Inoltre, leaflet riempie il terzo parametro delle coordinate della geometria Z con un valore di 0. Tuttavia, questo parametro non viene considerato nel nostro schema del database, quindi rimuoviamo la sua presenza impostando il valore di `HasZ` su false.

Il punto finale è l'applicazione delle modifiche sostituendo la feature esistente con quella ricevuta dal client che ha lo stesso osm_id. Questa operazione porterà al rilevamento delle modifiche rispetto alle istanze precedenti della feature. Al momento della chiamata a `SubmitChangesAsync`, il processo di rilevamento delle modifiche avverrà e i comandi INSERT, DELETE e UPDATE verranno inviati al database in base alle tue modifiche.

Grazie per aver letto fino alla fine. L'intero codice sarà disponibile nel seguente repository: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)