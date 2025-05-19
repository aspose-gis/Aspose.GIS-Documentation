---
title: "Актуализации на Aspose.GIS: Редактиране на обекти и геометрии и запазване на промените в базата данни."
type: docs
url: /bg/net/showcases/saving-changes-to-database/
description: "Тази статия изследва последните подобрения в библиотеката Aspose.GIS, фокусирайки се върху новите възможности за откриване и запазване на промени в геометриите във приложение за картографиране."
weight: 80
---
# Актуализации на Aspose.GIS: Редактиране на обекти и геометрии и запазване на промените в базата данни.

## Въведение

В светлината на последните промени в библиотеката [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis), е важно да подчертаем някои от тях, за да не останат незабелязани. В тази статия ще обсъдим новата възможност за откриване и запазване на промени в геометриите и характеристиките в базата данни.

Като пример за демонстрация, ще продължим да работим върху приложението, описано в статията ["Начертайте карта. Плъзгаща се карта с плочки"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) и леко ще го разширим, като добавим функционалности за редактиране на обекти на картата. Наборът от данни остава същият като в предишната статия.

## Front-end

За демонстрация на възможностите за модификация на геометриите избрахме популярно приложение с отворен код за [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/).

Добавяме тази библиотека чрез файла libman.json:
![Libman](libman.png)

След това свързваме стиловете и скриптовете към страницата:
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

За демонстрационни цели ще ограничим възможностите за редактиране само до сгради. Потребителят щраква върху левия бутон на мишката върху картата и ако има сграда на това място, тя се подчертава и става достъпна за редактиране. Това се постига чрез наслагване на допълнителен слой върху плочките.

Когато потребителят щракне върху картата, библиотеката Leaflet изчислява геопространствените координати на кликването. Изпращаме тези координати към back-end и търсим в базата данни за геометрии, които се пресичат с кликнатия момент. Ако има сгради сред тези геометрии, ние ги връщаме.

Сградите се връщат от back-end във формат `GeoJSON` и се добавят към картата като отделен слой за редактиране. Ето как обработваме кликването:
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

Имаме постоянен слой група за редактируеми геометрии, `featuresLayer`, който е добавен към картата. Проверяваме дали кликването е направено върху вече заредена геометрия и ако не, правим заявка към back-end, за да заредим полигоните, представляващи сгради. Заредените слоеве от характеристики се добавят към featuresLayer и режимът на редактиране се активира.

Ето какво е функцията за зареждане на характеристики и преобразуване от `GeoJSON`:
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

След сесията на редактиране, потребителят щраква върху персонализиран бутон `Save`:

![Save](save-btn.png)

Опресняване на страницата и виждане на промените:

![Changes](changes.png)

За съжаление, функцията `tiles.redraw()` не работи правилно, тъй като предишно заредените плочки са кеширани, което изисква принудително опресняване на картата чрез `Ctrl + F5`.

Ето обработчикът за натискане на бутона save:
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

Тук добавяме нов контролер, `FeaturesController`, където създаваме обработчик за извличане на къщи/характеристики според изпратените координати.

SQL заявката изглежда така:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

Координатите се трансформират в точка, обозначаваща координатна система на първоначалната заявка на клиента (WGS 84) и след това се превеждат в системата, в която са представени данните от базата данни (Web Mercator). Търсим пресичания с тази точка за геометрии, маркирани като сгради.

Изпълнението на заявката и изпращането на данни към клиента се извършва подобно на това, което обсъждахме в предишната статия:
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
С малка разлика: запазваме нашия InMemory слой като GeoJSON в паметта като поток, след това го преобразуваме в низ и го изпращаме на клиента.

Сега стигаме до същността на актуализациите в Aspose.GIS — запазване на промените в базата данни. Методът `Edit()` се справя с това. Четем тялото на заявката, за да го заредим изцяло в паметта и го четем като поток:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync(); 
Request.Body.Position = 0;
```
След това четем редактираните характеристики във формат GeoJSON:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
Следващата стъпка, от изпратения набор от характеристики, извличаме атрибутите, представляващи уникалните идентификатори на съответните характеристики в базата данни. Съставяме заявка за попълване на специален слой за редактиране и конструираме съответния източник на данни:
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
Забележете конфигуриращия метод `AsTrackableForChanges`. Това е специален метод, който показва необходимостта от създаване на специфичен източник на данни, способен да проследява промените. Първият параметър определя таблицата, към която трябва да бъдат изпратени заявките за промяна. Вторият посочва кой атрибут ще бъде считан за идентификатор за извършване на промени в базата данни. Най-интересната част е третият параметър. Когато е зададен на True, той показва, че слойът ще проследява появата на дубликати според втория параметър и „презаписва“ предишно заредени характеристики с нови. Въпреки това, в случай на редактиране на резултатите, т.е. добавяне на нова характеристика със същия идентификатор, ще бъде генерирана команда `UPDATE` според промените спрямо старата стойност. Ако дубликати се появят по време на инициализацията на слоя от базата данни, слойът тихо ще ги презапише с последната стойност. Ако третият параметър е зададен на false, при поява на дубликати ще бъде хвърлен изключение, независимо дали по време на инициализация или редактиране.

Имената на атрибутите ще бъдат използвани като имена на полетата в таблицата за редактиране. Важно е да се отбележи ключов момент относно откриването на промени. Необходимо е да се посочи точният тип данни на атрибута, който ще бъде съхранен в слоя за проследяване на промените, той трябва да е точен по отношение на новодобавените или модифицирани типове. Например, ако добавим нова характеристика с `osm_id` от тип `Int32`, докато посоченият тип атрибут в слоя е `Int64`, това ще бъде третирано като два различни стойности, тъй като няма претоварване на метода `Equal`s, което изглежда като `Int64.Equals(Int32)`. В бъдещите версии това поведение ще бъде прегледано и коригирано, ако е възможно. Типът на третия параметър ще се прилага по време на запазването на данните като целеви тип данни на таблицата в базата данни.

След това свързваме към базата данни и четем данни от таблицата:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
Важна точка е, че за да работи транзакцията правилно на ниво база данни, е необходимо да се предаде текущата транзакция като втори параметър по време на операцията на четене.

След това трябва да извършим серия от трансформации, преди да изпратим промените в базата данни:
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
Leaflet генерира геометрии в координатна система WGS 84, но схемата на базата данни изисква съхранение в Web Mercator. За да се трансформира към системата Web Mercator, създаваме специален обект `transformer` и го използваме за преобразуването.

Освен това leaflet попълва третия параметър на координатите на геометрията Z със стойност 0. Въпреки това този параметър не се отчита в нашата схема на база данни, така че премахваме присъствието му, като зададем стойността на `HasZ` на false.

Финалната точка е прилагането на промените чрез замяна на съществуващата характеристика с тази, получена от клиента, която има един и същ osm_id. Тази операция ще доведе до откриване на промени спрямо по-старите екземпляри на характеристиката. В момента на извикване на `SubmitChangesAsync`, процесът на откриване на промените ще се извърши и командите INSERT, DELETE и UPDATE ще бъдат изпратени към базата данни според вашите промени.

Благодарим ви, че прочетохте до края. Целият код ще бъде достъпен в следното хранилище: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)