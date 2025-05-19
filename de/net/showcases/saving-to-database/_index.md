---
title: "Aspose.GIS Updates: Editing Features and Geometries and saving changes to the database."
type: docs
url: /de/net/showcases/saving-changes-to-database/
description: "Dieser Artikel untersucht die jüngsten Verbesserungen in der Aspose.GIS-Bibliothek, wobei der Schwerpunkt auf den neuen Möglichkeiten zur Erkennung und Speicherung von Geometrieänderungen in einer Mapping-Anwendung liegt."
weight: 80
---
# Aspose.GIS Updates: Editing Features and Geometries and saving changes to the database.

## Introduction

Angesichts der jüngsten Änderungen in der [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis)-Bibliothek ist es wichtig, einige davon hervorzuheben, damit sie nicht unbemerkt bleiben. In diesem Artikel werden wir die neue Fähigkeit zur Erkennung und Speicherung von Änderungen an Geometrien und Features in der Datenbank diskutieren.

Als Beispiel für eine Demonstration werden wir weiterhin an der Anwendung arbeiten, die im Artikel ["Draw a map. A sliding map with tiles"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) beschrieben wird, und diese leicht erweitern, indem wir Funktionen zur Objekteditierung auf der Karte hinzufügen. Der Datensatz bleibt derselbe wie im vorherigen Artikel.

## Front-end

Für die Demonstration von Geometrieänderungsfunktionen haben wir uns für eine beliebte Open-Source-Erweiterung für [leaflet](https://leafletjs.com/) entschieden — [leaflet-geoman](https://geoman.io/).

Wir fügen diese Bibliothek über die libman.json-Datei hinzu:
![Libman](libman.png)

Als Nächstes verbinden wir die Stile und Skripte mit der Seite:
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

Für Demonstrationszwecke beschränken wir die Bearbeitungsfunktionen auf Gebäude. Der Benutzer klickt mit der linken Maustaste auf die Karte, und wenn sich an dieser Stelle ein Gebäude befindet, wird es hervorgehoben und bearbeitbar. Dies wird durch das Überlagern einer zusätzlichen Ebene über die Kacheln erreicht.

Wenn der Benutzer auf die Karte klickt, berechnet die Leaflet-Bibliothek die geodätischen Koordinaten des Klicks. Wir senden diese Koordinaten an den Back-End und suchen in der Datenbank nach Geometrien, die sich mit dem angeklickten Punkt schneiden. Wenn es sich unter diesen Geometrien um Gebäude handelt, geben wir sie zurück.

Die Gebäude werden vom Back-End im `GeoJSON`-Format zurückgegeben und als separate Ebene zur Bearbeitung auf die Karte hinzugefügt. So behandeln wir den Klick:
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

Wir haben eine permanente Layer-Gruppe für bearbeitbare Geometrien, `featuresLayer`, die der Karte hinzugefügt wurde. Wir prüfen, ob der Klick auf eine bereits geladene Geometrie erfolgte, und wenn nicht, stellen wir eine Anfrage an den Back-End, um die Polygone zu laden, die Gebäude darstellen. Die geladenen Feature-Layer werden zu featuresLayer hinzugefügt, und der Bearbeitungsmodus wird aktiviert.

Hier ist, wie die Funktion zum Laden von Features und Konvertieren aus `GeoJSON` aussieht:
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

Nach der Bearbeitungssitzung klickt der Benutzer auf eine benutzerdefinierte Schaltfläche `Speichern`:

![Save](save-btn.png)

Aktualisieren Sie die Seite und sehen Sie die Änderungen:

![Changes](changes.png)

Leider funktioniert die Funktion `tiles.redraw()` nicht richtig, da zuvor geladene Kacheln zwischengespeichert werden, was ein erzwungenes Aktualisieren der Karte über `Ctrl + F5` erforderlich macht.

Hier ist der Handler für das Drücken der Speichern-Schaltfläche:
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

Hier fügen wir einen neuen Controller, `FeaturesController`, hinzu, in dem wir einen Handler zum Extrahieren von Häusern/Features gemäß den gesendeten Koordinaten erstellen.

Die SQL-Anfrage sieht wie folgt aus:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

Die Koordinaten werden in einen Punkt umgewandelt, der das Koordinatensystem der ursprünglichen Clientanfrage (WGS 84) angibt und dann in das System übersetzt wird, in dem die Datenbankdaten dargestellt werden (Web Mercator). Wir suchen nach Schnittmengen mit diesem Punkt für Geometrien, die als Gebäude gekennzeichnet sind.

Die Ausführung der Anfrage und das Senden von Daten an den Client erfolgt ähnlich wie im vorherigen Artikel:
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
Mit einem kleinen Unterschied: Wir speichern unsere InMemory-Schicht als GeoJSON im Speicher als Stream, konvertieren sie dann in einen String und senden ihn an den Client.

Nun kommen wir zum Wesen der Updates in Aspose.GIS — dem Speichern von Änderungen in der Datenbank. Die Methode `Edit()` behandelt dies. Wir lesen den Request Body, um ihn vollständig in den Speicher zu laden und als Stream zu lesen:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync();
Request.Body.Position = 0;
```
Als Nächstes lesen wir die bearbeiteten Features im GeoJSON-Format:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
Der nächste Schritt besteht darin, aus dem gesendeten Feature-Set die Attribute zu extrahieren, die die eindeutigen Kennungen der entsprechenden Features in der Datenbank darstellen. Wir bilden eine Anfrage zum Auffüllen einer speziellen Schicht für die Bearbeitung und konstruieren die entsprechende Datenquelle:
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
Bemerkenswert ist die Konfigurationsmethode `AsTrackableForChanges`. Dies ist eine spezielle Methode, die angibt, dass eine bestimmte Datenquelle erstellt werden muss, die Änderungen verfolgen kann. Der erste Parameter gibt die Tabelle an, an die Änderungsanfragen gesendet werden sollen. Der zweite gibt an, welches Attribut als Kennung für Änderungen in der Datenbank betrachtet wird. Der interessanteste Teil ist der dritte Parameter. Wenn er auf True gesetzt ist, zeigt dies an, dass die Schicht Duplikate gemäß dem zweiten Parameter verfolgen und zuvor geladene Features mit neuen überschreiben wird. Im Falle von Bearbeitungsergebnissen, d. h. das Hinzufügen eines neuen Features mit derselben Kennung, wird jedoch ein `UPDATE`-Befehl entsprechend den Änderungen im Vergleich zum alten Wert generiert. Wenn der dritte Parameter auf False gesetzt ist, wird beim Auftreten von Duplikaten eine Ausnahme ausgelöst, sowohl während der Initialisierung als auch bei der Bearbeitung.

Attributnamen werden als Feldnamen in der bearbeitbaren Tabelle verwendet. Es ist wichtig, einen entscheidenden Punkt bezüglich der Änderungsdetektion zu beachten. Es ist unerlässlich, den genauen Datentyp des Attributs anzugeben, das für die Verfolgung von Änderungen in der Schicht gespeichert wird, er muss im Hinblick auf neu hinzugefügte oder geänderte Typen genau sein. Wenn wir beispielsweise ein neues Feature mit einer `osm_id` vom Typ `Int32` hinzufügen, während der angegebene Attributtyp in der Schicht `Int64` ist, wird dies als zwei verschiedene Werte behandelt, da es keine Überladung der Methode `Equal`s gibt, die wie `Int64.Equals(Int32)` aussieht. In zukünftigen Versionen wird dieses Verhalten überprüft und gegebenenfalls korrigiert. Der Typ des dritten Parameters wird beim Speichern von Daten als Zieldatentyp der Datenbanktabelle angewendet.

Als Nächstes verbinden wir uns mit der Datenbank und lesen Daten aus der Tabelle:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
Ein wichtiger Punkt ist, dass für die korrekte Funktion der Transaktion auf Datenbankebene es notwendig ist, die aktuelle Transaktion als zweiten Parameter während des Lesevorgangs zu übergeben.

Als Nächstes müssen wir eine Reihe von Transformationen durchführen, bevor wir die Änderungen an die Datenbank senden:
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
Leaflet generiert Geometrien im Koordinatensystem WGS 84, die Datenbankschema erfordert jedoch eine Speicherung in Web Mercator. Um in das Web Mercator-System zu transformieren, erstellen wir ein spezielles `transformer`-Objekt und verwenden es für die Konvertierung.

Darüber hinaus füllt Leaflet den dritten Parameter der Geometrie-Koordinaten Z mit einem Wert von 0. Dieser Parameter wird jedoch nicht im Datenbankschema berücksichtigt, daher entfernen wir seine Präsenz, indem wir den Wert von `HasZ` auf False setzen.

Der letzte Punkt ist das Anwenden von Änderungen durch Ersetzen des vorhandenen Features durch das vom Client empfangene Feature, das die gleiche osm_id hat. Diese Operation führt zur Erkennung von Änderungen im Verhältnis zu den älteren Instanzen des Features. Im Moment des Aufrufs von `SubmitChangesAsync` erfolgt der Prozess der Änderungsdetektion, und die Befehle INSERT, DELETE und UPDATE werden entsprechend Ihren Änderungen an die Datenbank gesendet.

Vielen Dank für das Lesen bis zum Ende. Der gesamte Code ist im folgenden Repository verfügbar: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)