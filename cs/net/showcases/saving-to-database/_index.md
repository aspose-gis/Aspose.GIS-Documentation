---
title: "Aktualizace Aspose.GIS: Úpravy prvků a geometrií a ukládání změn do databáze."
type: docs
url: /cs/net/showcases/saving-changes-to-database/
description: "Tento článek se zabývá nedávnými vylepšeními knihovny Aspose.GIS, zaměřuje se na nové možnosti detekce a ukládání změn geometrie v mapové aplikaci."
weight: 80
---
# Aktualizace Aspose.GIS: Úpravy prvků a geometrií a ukládání změn do databáze.

## Úvod

Vzhledem k nedávným změnám v knihovně [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis) je důležité některé z nich zdůraznit, aby nezůstaly nepovšimnuty. V tomto článku probereme novou možnost detekce a ukládání změn geometrie a prvků do databáze.

Jako příklad pro demonstraci budeme pokračovat v práci na aplikaci popsané v článku ["Vytvořit mapu. Posuvná mapa s dlaždicemi"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) a mírně ji rozšíříme o funkce úpravy objektů na mapě. Datový soubor zůstává stejný jako v předchozím článku.

## Front-end

Pro demonstraci možností modifikace geometrie jsme si vybrali oblíbené open-source rozšíření pro [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/).

Tuto knihovnu přidáme přes soubor libman.json:
![Libman](libman.png)

Následně připojíme styly a skripty ke stránce:
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

Pro demonstrační účely omezíme možnosti úprav na budovy pouze. Uživatel klikne levým tlačítkem myši na mapu a pokud se v daném místě nachází budova, ta se zvýrazní a bude dostupná pro editaci. Toho dosáhneme překrytím další vrstvy přes dlaždice.

Když uživatel klikne na mapu, knihovna Leaflet vypočítá zeměpisné souřadnice kliknutí. Tyto souřadnice odešleme do backendu a vyhledáme v databázi geometrie, které protínají kliknutý bod. Pokud se mezi těmito geometriemi nacházejí budovy, vrátíme je.

Budovy jsou vráceny z backendu ve formátu `GeoJSON` a přidány na mapu jako samostatná vrstva pro editaci. Zde je způsob, jakým zpracováváme kliknutí:
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

Máme trvalou vrstvovou skupinu pro upravitelné geometrie, `featuresLayer`, která byla přidána na mapu. Zkontrolujeme, zda bylo kliknutí provedeno na již načtenou geometrii, a pokud ne, odešleme požadavek do backendu k načtení polygonů představujících budovy. Načtené vrstvy prvků jsou přidány do featuresLayer a je aktivován režim editace.

Zde je funkce pro načítání prvků a převod z `GeoJSON`:
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

Po relaci editace uživatel klikne na vlastní tlačítko `Uložit`:

![Save](save-btn.png)

Obnovte stránku a uvidíte změny:

![Changes](changes.png)

Bohužel funkce `tiles.redraw()` nefunguje správně, protože dříve načtené dlaždice jsou uloženy v mezipaměti, což vyžaduje vynucené obnovení mapy pomocí `Ctrl + F5`.

Zde je obslužný program pro stisknutí tlačítka uložit:
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

## Backend

Zde přidáme nový kontroler, `FeaturesController`, kde vytvoříme obslužný program pro extrakci domů/prvků podle odeslaných souřadnic.

SQL požadavek vypadá takto:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

Souřadnice jsou transformovány do bodu, označujícího souřadnicový systém původního požadavku klienta (WGS 84) a poté převedeny do systému, ve kterém jsou uložena data databáze (Web Mercator). Hledáme průsečíky s tímto bodem pro geometrie označené jako budovy.

Provedení požadavku a odeslání dat klientovi probíhá podobně jako v předchozím článku:
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
S malým rozdílem: ukládáme naši InMemory vrstvu jako GeoJSON do paměti jako stream, poté ji převedeme na řetězec a odešleme klientovi.

Nyní se dostáváme k podstatě aktualizací v Aspose.GIS — ukládání změn do databáze. Metoda `Edit()` to zpracovává. Přečteme tělo požadavku, abychom jej plně načetli do paměti a přečetli jako stream:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync();
Request.Body.Position = 0;
```
Následně přečteme upravené prvky ve formátu GeoJSON:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
Dalším krokem je, že z odeslané sady prvků extrahujeme atributy představující jedinečné identifikátory odpovídajících prvků v databázi. Vytvoříme požadavek na naplnění speciální vrstvy pro editaci a sestavíme odpovídající zdroj dat:
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
Poznamenejte si konfigurační metodu `AsTrackableForChanges`. Jedná se o speciální metodu, která označuje potřebu vytvořit specifický zdroj dat schopný sledovat změny. První parametr určuje tabulku, do které by měly být zaslány požadavky na změnu. Druhý udává, který atribut bude považován za identifikátor pro provádění změn v databázi. Nejdůležitější částí je třetí parametr. Když je nastaven na True, označuje to, že vrstva bude sledovat výskyt duplikátů podle druhého parametru a „přepíše“ dříve načtené prvky novými. V případě úpravných výsledků, tj. přidání nového prvku se stejným identifikátorem, však bude vygenerován příkaz `UPDATE` podle změn ve srovnání se starou hodnotou. Pokud je třetí parametr nastaven na false, při výskytu duplikátů během inicializace vrstvy nebo editace bude vyvolána výjimka.

Názvy atributů budou použity jako názvy polí v upravitelné tabulce. Je důležité poznamenat zásadní bod týkající se detekce změn. Je nezbytné určit přesný datový typ atributu, který bude uložen ve vrstvě pro sledování změn, musí být přesný vzhledem k nově přidaným nebo upraveným typům. Například pokud přidáme nový prvek s `osm_id` typu `Int32`, zatímco určený typ atributu ve vrstvě je `Int64`, bude to považováno za dvě různé hodnoty, protože neexistuje žádné přetížení metody `Equal`s, které by vypadalo jako `Int64.Equals(Int32)`. V budoucích verzích bude toto chování přezkoumáno a v případě potřeby opraveno. Typ třetího parametru bude použit během ukládání dat jako cílový typ dat tabulky databáze.

Následně se připojíme k databázi a přečteme data z tabulky:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
Důležitým bodem je, že aby transakce správně fungovala na úrovni databáze, je nezbytné předat aktuální transakci jako druhý parametr během operace čtení.

Následně musíme provést řadu transformací před odesláním změn do databáze:
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
Leaflet generuje geometrie v souřadnicovém systému WGS 84, nicméně databáze vyžaduje ukládání ve Web Mercatoru. Pro transformaci do systému Web Mercator vytvoříme speciální objekt `transformer` a použijeme jej pro převod.

Dále Leaflet vyplňuje třetí parametr souřadnic geometrie Z hodnotou 0. Tento parametr však není zohledněn v našem schématu databáze, takže odstraníme jeho přítomnost nastavením hodnoty `HasZ` na false.

Finálním bodem je aplikování změn nahrazením existujícího prvku tím, který byl přijat od klienta a má stejné osm_id. Tato operace povede k detekci změn vzhledem ke starším instancím prvku. V okamžiku volání `SubmitChangesAsync` dojde k procesu detekce změn a příkazy INSERT, DELETE a UPDATE budou odeslány do databáze podle vašich změn.

Děkujeme za přečtení až do konce. Celý kód bude k dispozici v následujícím repozitáři: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)
---