---
title: "Aspose.GIS Updates: Editing Features and Geometries and saving changes to the database."
type: docs
url: /nl/net/showcases/saving-changes-to-database/
description: "Dit artikel onderzoekt de recente verbeteringen in de Aspose.GIS bibliotheek, met de focus op de nieuwe mogelijkheden voor het detecteren en opslaan van geometrie wijzigingen in een mapping applicatie."
weight: 80
---
# Aspose.GIS Updates: Editing Features and Geometries and saving changes to the database.

## Introduction

In het licht van de recente veranderingen in de [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis) bibliotheek, is het belangrijk om er een aantal te benadrukken zodat ze niet onopgemerkt blijven. In dit artikel bespreken we de nieuwe mogelijkheid om wijzigingen aan geometrieën en features in de database te detecteren en op te slaan.

Als voorbeeld voor demonstratie zullen we doorgaan met het werken aan de applicatie beschreven in het artikel ["Draw a map. A sliding map with tiles"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) en deze licht uitbreiden door object editing functionaliteiten op de kaart toe te voegen. De dataset blijft hetzelfde als in het vorige artikel.

## Front-end

Voor de demonstratie van geometrie modificatie mogelijkheden hebben we gekozen voor een populaire open-source extensie voor [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/).

We voegen deze bibliotheek toe via het libman.json bestand:
![Libman](libman.png)

Vervolgens verbinden we de stijlen en scripts met de pagina:
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

Voor demonstratiedoeleinden beperken we de editing mogelijkheden tot gebouwen alleen. De gebruiker klikt op de linker muisknop op de kaart, en als er een gebouw op die locatie is, wordt het gemarkeerd en beschikbaar voor bewerking. Dit wordt bereikt door een extra laag over de tegels heen te leggen.

Wanneer de gebruiker op de kaart klikt, berekent de Leaflet bibliotheek de geospatial coördinaten van de klik. We sturen deze coördinaten naar de back-end en zoeken in de database naar geometrieën die kruisen met het geklikte punt. Als er gebouwen tussen deze geometrieën zitten, retourneren we ze.

De gebouwen worden vanuit de back-end geretourneerd in `GeoJSON` formaat en toegevoegd aan de kaart als een aparte laag voor bewerking. Zo verwerken we de klik:
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

We hebben een permanente laag groep voor bewerkbare geometrieën, `featuresLayer`, die aan de kaart is toegevoegd. We controleren of er op een al geladen geometrie is geklikt, en zo niet, maken we een verzoek naar de back-end om de polygonen die gebouwen vertegenwoordigen te laden. De geladen feature lagen worden toegevoegd aan featuresLayer, en de bewerkingsmodus wordt geactiveerd.

Hier is hoe de functie voor het laden van features en converteren vanuit `GeoJSON` eruit ziet:
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

Na de bewerkingssessie klikt de gebruiker op een aangepaste `Save` knop:

![Save](save-btn.png)

Verfris de pagina en bekijk de wijzigingen:

![Changes](changes.png)

Helaas werkt de functie `tiles.redraw()` niet goed omdat eerder geladen tegels gecached zijn, waardoor een geforceerde refresh van de kaart vereist is via `Ctrl + F5`.

Hier is de handler voor het indrukken van de save knop:
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

Hier voegen we een nieuwe controller toe, `FeaturesController`, waar we een handler creëren voor het extraheren van huizen/features volgens de verzonden coördinaten.

De SQL request ziet er als volgt uit:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

De coördinaten worden getransformeerd naar een punt, wat de coordinate systeem van de originele client request (WGS 84) aangeeft, en vervolgens vertaald naar het systeem waarin de database data wordt gepresenteerd (Web Mercator). We zoeken naar kruisingen met dit punt voor geometrieën die als gebouwen zijn gemarkeerd.

De uitvoering van de request en het verzenden van data naar de client verloopt vergelijkbaar met wat we in het vorige artikel hebben besproken:
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
Met een klein verschil: we slaan onze InMemory layer op als GeoJSON in het geheugen als een stream, converteren deze vervolgens naar een string en sturen deze naar de client.

Nu komen we bij de essentie van de updates in Aspose.GIS — het opslaan van wijzigingen in de database. De `Edit()` methode behandelt dit. We lezen de request body om hem volledig in het geheugen te laden en lezen hem als een stream:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync();
Request.Body.Position = 0;
```
Vervolgens lezen we de bewerkte features in GeoJSON formaat:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
De volgende stap, van de verzonden set features extraheren we de attributen die unieke identifiers vertegenwoordigen van de overeenkomstige features in de database. We vormen een request om een speciale laag voor bewerking te vullen en construeren de corresponderende data source:
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
Let op de configurerende methode `AsTrackableForChanges`. Dit is een speciale methode die aangeeft dat er behoefte is aan het creëren van een specifieke data source die wijzigingen kan volgen. De eerste parameter geeft de tabel aan waarnaar change requests moeten worden verzonden. De tweede geeft aan welke attribuut als identifier voor het maken van wijzigingen in de database zal worden beschouwd. Het meest interessante deel is de derde parameter. Wanneer deze op True staat, geeft dit aan dat de laag duplicaten volgens de tweede parameter zal volgen en "overschrijven" van eerder geladen features met nieuwe. Echter, in het geval van bewerkingsresultaten, d.w.z. het toevoegen van een nieuw feature met dezelfde identifier, wordt een `UPDATE` command gegenereerd op basis van de wijzigingen ten opzichte van de oude waarde. Als duplicaten verschijnen tijdens de initialisatie van de laag vanuit de database, zal de laag ze stilzwijgend overschrijven met de laatste waarde. Als de derde parameter op false staat, wordt er een uitzondering gegenereerd bij het verschijnen van duplicaten, zowel tijdens de initialisatie als bewerking.

Attribuutnamen worden gebruikt als veldnamen in de bewerkbare tabel. Het is belangrijk om een cruciaal punt te noteren met betrekking tot change detection. Het is essentieel om het exacte datatype van het attribuut dat in de laag zal worden opgeslagen voor het volgen van wijzigingen nauwkeurig te specificeren, het moet accuraat zijn ten opzichte van nieuw toegevoegde of gewijzigde types. Als we bijvoorbeeld een nieuw feature toevoegen met een `osm_id` van type `Int32`, terwijl het gespecificeerde attribuuttype in de laag `Int64` is, zal dit worden behandeld als twee verschillende waarden omdat er geen overload van de `Equal`s methode is die lijkt op `Int64.Equals(Int32)`. In toekomstige versies zal dit gedrag worden herzien en gecorrigeerd indien mogelijk. Het type van de derde parameter wordt toegepast tijdens het opslaan van data als het doel datatype van de database tabel.

Vervolgens verbinden we met de database en lezen we data uit de tabel:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
Een belangrijk punt is dat voor de transactie correct op database niveau te werken, het noodzakelijk is om de huidige transactie als tweede parameter door te geven tijdens de read operatie.

Vervolgens moeten we een reeks transformaties uitvoeren voordat we de wijzigingen naar de database sturen:
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
Leaflet genereert geometrieën in het WGS 84 coordinate systeem, echter vereist de database schema opslag in Web Mercator. Om te transformeren naar het Web Mercator systeem creëren we een speciaal `transformer` object en gebruiken deze voor de conversie.

Daarnaast vult Leaflet de derde parameter van de geometrie coördinaten Z met een waarde van 0. Echter, deze parameter wordt niet meegenomen in ons database schema, dus verwijderen we zijn aanwezigheid door de waarde van `HasZ` op false te zetten.

Het laatste punt is het toepassen van wijzigingen door de bestaande feature te vervangen door degene die van de client is ontvangen en dezelfde osm_id heeft. Deze operatie zal leiden tot de detectie van wijzigingen ten opzichte van de oudere instanties van de feature. Op het moment dat `SubmitChangesAsync` wordt aangeroepen, vindt het change detection proces plaats, en de commands INSERT, DELETE en UPDATE worden naar de database gestuurd volgens uw wijzigingen.

Bedankt voor het lezen tot het einde. De volledige code is beschikbaar in de volgende repository: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)