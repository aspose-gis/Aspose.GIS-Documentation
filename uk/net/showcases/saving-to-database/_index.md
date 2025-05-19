---
title: "Оновлення Aspose.GIS: редагування об'єктів та геометрій і збереження змін у базі даних."
type: docs
url: /uk/net/showcases/saving-changes-to-database/
description: "У цій статті досліджуються останні покращення в бібліотеці Aspose.GIS, зосереджуючись на нових можливостях виявлення та збереження змін геометрії у картографічному додатку."
weight: 80
---
# Оновлення Aspose.GIS: редагування об'єктів та геометрій і збереження змін у базі даних.

## Вступ

У світлі нещодавніх змін у бібліотеці [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis) важливо виділити деякі з них, щоб вони не залишилися непоміченими. У цій статті ми обговоримо нову можливість виявлення та збереження змін геометрії та об'єктів у базі даних.

В якості прикладу для демонстрації ми продовжимо працювати над додатком, описаним у статті ["Намалюйте карту. Ковзна карта з тайлами"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) і трохи розширимо її, додавши функціональність редагування об'єктів на карті. Набір даних залишається таким самим, як у попередній статті.

## Front-end

Для демонстрації можливостей модифікації геометрії ми обрали популярне розширення з відкритим кодом для [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/).

Ми додаємо цю бібліотеку через файл libman.json:
![Libman](libman.png)

Наступним кроком є підключення стилів та скриптів до сторінки:
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

Для демонстраційних цілей ми обмежимо можливості редагування лише будівлями. Користувач натискає ліву кнопку миші на карті, і якщо в цьому місці є будівля, вона виділяється та стає доступною для редагування. Це досягається шляхом накладання додаткового шару поверх тайлів.

Коли користувач клацає по карті, бібліотека Leaflet обчислює геопросторові координати кліку. Ми надсилаємо ці координати в бекенд і шукаємо в базі даних геометрії, які перетинаються з натиснутою точкою. Якщо серед цих геометрій є будівлі, ми повертаємо їх.

Будівлі повертаються з бекенду у форматі `GeoJSON` та додаються на карту як окремий шар для редагування. Ось як ми обробляємо клік:
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

У нас є постійний груповий шар для редагованих геометрій, `featuresLayer`, який був доданий до карти. Ми перевіряємо, чи було зроблено клік на вже завантажену геометрію, і якщо ні, ми робимо запит до бекенду, щоб завантажити багатокутники, що представляють будівлі. Завантажені шари функцій додаються до featuresLayer, і активується режим редагування.

Ось як виглядає функція для завантаження об'єктів та перетворення з `GeoJSON`:
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

Після сеансу редагування користувач натискає спеціальну кнопку `Save`:

![Save](save-btn.png)

Оновіть сторінку та перегляньте зміни:

![Changes](changes.png)

На жаль, функція `tiles.redraw()` не працює належним чином, оскільки попередньо завантажені тайли кешуються, що вимагає примусового оновлення карти через `Ctrl + F5`.

Ось обробник для натискання кнопки збереження:
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

Тут ми додаємо новий контролер, `FeaturesController`, де створюємо обробник для вилучення будинків/об'єктів відповідно до надісланих координат.

SQL запит виглядає наступним чином:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

Координати перетворюються на точку, що вказує систему координат оригінального запиту клієнта (WGS 84), а потім переводяться в систему, в якій представлені дані бази даних (Web Mercator). Ми шукаємо перетини з цією точкою для геометрій, позначених як будівлі.

Виконання запиту та надсилання даних клієнту відбувається подібно до того, що ми обговорювали у попередній статті:
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
З невеликою відмінністю: ми зберігаємо наш InMemory шар як GeoJSON в пам'яті у вигляді потоку, потім перетворюємо його на рядок і надсилаємо клієнту.

Тепер ми підходимо до суті оновлень в Aspose.GIS — збереження змін у базі даних. Метод `Edit()` обробляє це. Ми читаємо тіло запиту, щоб повністю завантажити його в пам'ять і прочитати як потік:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync(); 
Request.Body.Position = 0;
```
Наступним кроком є читання відредагованих об'єктів у форматі GeoJSON:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
Наступний крок, з надісланого набору об'єктів, ми витягуємо атрибути, що представляють унікальні ідентифікатори відповідних об'єктів у базі даних. Ми формуємо запит для заповнення спеціального шару для редагування та будуємо відповідне джерело даних:
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
Зверніть увагу на метод конфігурації `AsTrackableForChanges`. Це спеціальний метод, який вказує необхідність створення певного джерела даних, здатного відстежувати зміни. Перший параметр визначає таблицю, до якої слід надсилати запити змін. Другий вказує, який атрибут буде вважатися ідентифікатором для внесення змін до бази даних. Найцікавіша частина — третій параметр. При встановленні значення True він вказує, що шар відстежуватиме появу дублікатів відповідно до другого параметра та "перезаписуватиме" попередньо завантажені об'єкти новими. Однак у випадку редагування результатів, тобто додавання нового об’єкта з тим самим ідентифікатором, буде створено команду `UPDATE` відповідно до змін порівняно зі старим значенням. Якщо дублікати виникають під час ініціалізації шару з бази даних, шар тихо перезапише їх останнім значенням. Якщо третій параметр встановлено на false, при появі дублікатів буде викинуто виключення, чи то під час ініціалізації, чи то редагування.

Імена атрибутів будуть використані як імена полів у таблиці для редагування. Важливо відзначити важливий момент щодо виявлення змін. Необхідно точно вказати тип даних атрибуту, який буде зберігатися в шарі для відстеження змін, він повинен бути точним щодо доданих або змінених типів. Наприклад, якщо ми додаємо новий об’єкт з `osm_id` типу `Int32`, тоді як зазначений тип атрибуту в шарі є `Int64`, це буде розглядатися як два різні значення, оскільки немає перевантаження методу `Equal`s, який виглядає як `Int64.Equals(Int32)`. У майбутніх версіях ця поведінка буде переглянута та виправлена, якщо можливо. Тип третього параметра буде застосовано під час збереження даних як цільовий тип даних таблиці бази даних.

Наступним кроком є підключення до бази даних і читання даних з таблиці:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
Важливим моментом є те, що для правильної роботи транзакції на рівні бази даних необхідно передати поточну транзакцію як другий параметр під час операції читання.

Наступним кроком нам потрібно виконати серію перетворень перед надсиланням змін до бази даних:
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
Leaflet генерує геометрії в системі координат WGS 84, однак схема бази даних вимагає зберігання у Web Mercator. Щоб перетворити на систему Web Mercator, ми створюємо спеціальний об’єкт `transformer` і використовуємо його для перетворення.

Крім того, leaflet заповнює третій параметр координат геометрії Z значенням 0. Однак цей параметр не враховується в нашій схемі бази даних, тому ми видаляємо його присутність, встановивши значення `HasZ` на false.

Останньою точкою є застосування змін шляхом заміни існуючого об’єкта тим, що отримано від клієнта, який має той самий osm_id. Ця операція призведе до виявлення змін щодо старих екземплярів об’єкта. У момент виклику `SubmitChangesAsync` відбудеться процес виявлення змін, і команди INSERT, DELETE та UPDATE будуть надіслані в базу даних відповідно до ваших змін.

Дякуємо за прочитання до кінця. Весь код буде доступний у наступному репозиторії: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)