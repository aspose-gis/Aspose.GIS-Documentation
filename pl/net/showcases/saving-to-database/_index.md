---
title: "Aktualizacje Aspose.GIS: Edycja obiektów i geometrii oraz zapisywanie zmian w bazie danych."
type: docs
url: /pl/net/showcases/saving-changes-to-database/
description: "Ten artykuł omawia niedawne ulepszenia biblioteki Aspose.GIS, skupiając się na nowych możliwościach wykrywania i zapisywania zmian geometrii w aplikacji mapowania."
weight: 80
---
# Aktualizacje Aspose.GIS: Edycja obiektów i geometrii oraz zapisywanie zmian w bazie danych.

## Wprowadzenie

W świetle ostatnich zmian w bibliotece [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis), ważne jest, aby podkreślić niektóre z nich, aby nie pozostały niezauważone. W tym artykule omówimy nową możliwość wykrywania i zapisywania zmian geometrii i obiektów w bazie danych.

Jako przykład demonstracyjny będziemy kontynuować pracę nad aplikacją opisaną w artykule ["Narysuj mapę. Mapa przesuwna z kafelkami"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) i nieco ją rozbudować, dodając funkcjonalność edycji obiektów na mapie. Zestaw danych pozostaje taki sam jak w poprzednim artykule.

## Front-end

Do demonstracji możliwości modyfikacji geometrii wybraliśmy popularne rozszerzenie open source dla [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/).

Dodajemy tę bibliotekę za pomocą pliku libman.json:
![Libman](libman.png)

Następnie podłączamy style i skrypty do strony:
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

W celach demonstracyjnych ograniczymy możliwości edycji tylko do budynków. Użytkownik klika lewym przyciskiem myszy na mapie, a jeśli w tym miejscu znajduje się budynek, zostaje on podświetlony i staje się dostępny do edycji. Osiągamy to poprzez nakładanie dodatkowej warstwy na kafelki.

Gdy użytkownik klika na mapę, biblioteka Leaflet oblicza współrzędne geograficzne kliknięcia. Wysyłamy te współrzędne do back-endu i szukamy w bazie danych geometrii, które przecinają się z klikniętym punktem. Jeśli wśród tych geometrii znajdują się budynki, zwracamy je.

Budynki są zwracane z back-endu w formacie `GeoJSON` i dodawane na mapie jako oddzielna warstwa do edycji. Oto jak obsługujemy kliknięcie:
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

Posiadamy trwałą grupę warstw dla edytowalnych geometrii, `featuresLayer`, która została dodana do mapy. Sprawdzamy, czy kliknięcie nastąpiło na już załadowaną geometrię, a jeśli nie, wysyłamy żądanie do back-endu w celu załadowania wielokątów reprezentujących budynki. Załadowane warstwy cech są dodawane do featuresLayer, a tryb edycji jest aktywowany.

Oto jak wygląda funkcja ładowania cech i konwersji z `GeoJSON`:
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

Po sesji edycji użytkownik klika niestandardowy przycisk `Zapisz`:

![Save](save-btn.png)

Odśwież stronę i zobacz zmiany:

![Changes](changes.png)

Niestety, funkcja `tiles.redraw()` nie działa prawidłowo, ponieważ wcześniej załadowane kafelki są pamiętane podręcznie, co wymaga wymuszonego odświeżenia mapy przez `Ctrl + F5`.

Oto handler dla naciśnięcia przycisku zapisz:
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

Dodajemy tutaj nowy kontroler, `FeaturesController`, gdzie tworzymy handler do wyodrębniania domów/cech zgodnie z wysłanymi współrzędnymi.

Zapytanie SQL wygląda następująco:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

Współrzędne są przekształcane w punkt wskazujący system współrzędnych oryginalnego żądania klienta (WGS 84), a następnie tłumaczone do systemu, w którym prezentowane są dane bazy danych (Web Mercator). Szukamy przecięć z tym punktem dla geometrii oznaczonych jako budynki.

Wykonanie zapytania i wysyłanie danych do klienta odbywa się podobnie jak omówiono w poprzednim artykule:
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
Z niewielką różnicą: zapisujemy naszą warstwę InMemory jako GeoJSON w pamięci jako strumień, następnie konwertujemy ją na ciąg znaków i wysyłamy do klienta.

Przechodzimy teraz do sedna aktualizacji w Aspose.GIS — zapisywania zmian w bazie danych. Metoda `Edit()` obsługuje to. Czytamy treść żądania, aby w pełni załadować ją do pamięci i odczytać jako strumień:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync();
Request.Body.Position = 0;
```
Następnie czytamy edytowane cechy w formacie GeoJSON:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
Kolejnym krokiem jest wyodrębnienie z wysłanego zestawu cech atrybutów reprezentujących unikalne identyfikatory odpowiednich cech w bazie danych. Tworzymy żądanie wypełnienia specjalnej warstwy do edycji i konstruujemy odpowiednie źródło danych:
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
Zwróć uwagę na konfigurującą metodę `AsTrackableForChanges`. Jest to specjalna metoda, która wskazuje potrzebę utworzenia konkretnego źródła danych zdolnego do śledzenia zmian. Pierwszy parametr określa tabelę, do której mają być wysyłane żądania zmian. Drugi wskazuje, który atrybut będzie traktowany jako identyfikator wprowadzania zmian w bazie danych. Najciekawsza część to trzeci parametr. Ustawiony na True, wskazuje, że warstwa będzie śledzić pojawianie się duplikatów zgodnie z drugim parametrem i „nadpisywać” wcześniej załadowane cechy nowymi. Jednak w przypadku wyników edycji, tj. dodania nowej cechy o tym samym identyfikatorze, zostanie wygenerowane polecenie `UPDATE` zgodnie ze zmianami w porównaniu do starej wartości. Jeśli trzeci parametr jest ustawiony na false, wyjątek zostanie rzucony po pojawieniu się duplikatów, zarówno podczas inicjalizacji, jak i edycji.

Nazwy atrybutów zostaną użyte jako nazwy pól w edytowalnej tabeli. Ważne jest zauważenie kluczowego punktu dotyczącego wykrywania zmian. Niezbędne jest określenie dokładnego typu danych atrybutu, który będzie przechowywany w warstwie do śledzenia zmian, musi być dokładny w odniesieniu do nowo dodanych lub zmodyfikowanych typów. Na przykład, jeśli dodamy nową cechę z `osm_id` typu `Int32`, podczas gdy określony typ atrybutu w warstwie to `Int64`, zostanie to potraktowane jako dwie różne wartości, ponieważ nie ma przeciążenia metody `Equal`s, które wygląda jak `Int64.Equals(Int32)`. W przyszłych wersjach to zachowanie zostanie przeanalizowane i poprawione, jeśli to możliwe. Typ trzeciego parametru będzie stosowany podczas zapisywania danych jako docelowy typ danych tabeli bazy danych.

Następnie łączymy się z bazą danych i odczytujemy dane z tabeli:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
Ważnym punktem jest to, że aby transakcja działała prawidłowo na poziomie bazy danych, konieczne jest przekazanie bieżącej transakcji jako drugiego parametru podczas operacji odczytu.

Następnie musimy wykonać serię transformacji przed wysłaniem zmian do bazy danych:
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
Leaflet generuje geometrie w systemie współrzędnych WGS 84, jednak schemat bazy danych wymaga przechowywania w Web Mercator. Aby przekształcić do systemu Web Mercator, tworzymy specjalny obiekt `transformer` i używamy go do konwersji.

Dodatkowo leaflet wypełnia trzeci parametr współrzędnych geometrii Z wartością 0. Jednak ten parametr nie jest uwzględniany w naszym schemacie bazy danych, więc usuwamy jego obecność ustawiając wartość `HasZ` na false.

Ostatnim punktem jest zastosowanie zmian poprzez zastąpienie istniejącej cechy nową otrzymaną od klienta, która ma taki sam osm_id. Ta operacja doprowadzi do wykrycia zmian w stosunku do starszych instancji cechy. W momencie wywołania `SubmitChangesAsync` nastąpi proces wykrywania zmian, a polecenia INSERT, DELETE i UPDATE zostaną wysłane do bazy danych zgodnie z Twoimi zmianami.

Dziękujemy za przeczytanie do końca. Cały kod będzie dostępny w następnym repozytorium: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)