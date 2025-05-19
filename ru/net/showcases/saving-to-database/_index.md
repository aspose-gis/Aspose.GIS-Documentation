---
title: "Обновления Aspose.GIS: Редактирование объектов и геометрий и сохранение изменений в базе данных."
type: docs
url: /ru/net/showcases/saving-changes-to-database/
description: "В этой статье рассматриваются последние улучшения в библиотеке Aspose.GIS, уделяя особое внимание новым возможностям обнаружения и сохранения изменений геометрии в картографическом приложении."
weight: 80
---
# Обновления Aspose.GIS: Редактирование объектов и геометрий и сохранение изменений в базе данных.

## Введение

В свете последних изменений в библиотеке [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis), важно выделить некоторые из них, чтобы они не остались незамеченными. В этой статье мы обсудим новую возможность обнаружения и сохранения изменений геометрий и объектов в базе данных.

В качестве примера для демонстрации мы продолжим работать с приложением, описанным в статье ["Создание карты. Скользящая карта с тайлами"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) и немного расширим его, добавив функциональность редактирования объектов на карте. Набор данных остается таким же, как в предыдущей статье.

## Front-end

Для демонстрации возможностей модификации геометрии мы выбрали популярное расширение с открытым исходным кодом для [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/).

Мы добавляем эту библиотеку через файл libman.json:
![Libman](libman.png)

Затем мы подключаем стили и скрипты к странице:
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

Для демонстрационных целей мы ограничим возможности редактирования только зданиями. Пользователь нажимает левую кнопку мыши на карте, и если в этом месте есть здание, оно выделяется и становится доступным для редактирования. Это достигается путем наложения дополнительного слоя поверх тайлов.

Когда пользователь щелкает по карте, библиотека Leaflet вычисляет географические координаты щелчка. Мы отправляем эти координаты в бэкэнд и выполняем поиск в базе данных геометрий, пересекающихся с этой точкой щелчка. Если среди этих геометрий есть здания, мы возвращаем их.

Здания возвращаются из бэкэнда в формате `GeoJSON` и добавляются на карту как отдельный слой для редактирования. Вот как мы обрабатываем щелчок:
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

У нас есть постоянная группировка слоев для редактируемых геометрий, `featuresLayer`, которая была добавлена на карту. Мы проверяем, был ли щелчок сделан по уже загруженной геометрии, и если нет, мы делаем запрос в бэкэнд для загрузки полигонов, представляющих здания. Загруженные слои функций добавляются к featuresLayer, и активируется режим редактирования.

Вот как выглядит функция загрузки функций и преобразования из `GeoJSON`:
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

После сеанса редактирования пользователь нажимает специальную кнопку `Save`:

![Save](save-btn.png)

Обновите страницу и посмотрите изменения:

![Changes](changes.png)

К сожалению, функция `tiles.redraw()` не работает должным образом, поскольку ранее загруженные тайлы кэшируются, что требует принудительного обновления карты через `Ctrl + F5`.

Вот обработчик нажатия кнопки сохранения:
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

Здесь мы добавляем новый контроллер, `FeaturesController`, где создаем обработчик для извлечения домов/объектов в соответствии с отправленными координатами.

SQL запрос выглядит следующим образом:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

Координаты преобразуются в точку, указывающую систему координат исходного запроса клиента (WGS 84), а затем переводятся в систему, в которой представлены данные базы данных (Web Mercator). Мы ищем пересечения с этой точкой для геометрий, помеченных как здания.

Выполнение запроса и отправка данных клиенту происходит аналогично тому, что мы обсуждали в предыдущей статье:
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
С небольшой разницей: мы сохраняем наш InMemory слой в GeoJSON в памяти как поток, затем преобразуем его в строку и отправляем клиенту.

Теперь мы переходим к сути обновлений в Aspose.GIS — сохранению изменений в базе данных. Метод `Edit()` обрабатывает это. Мы читаем тело запроса, чтобы полностью загрузить его в память, и читаем его как поток:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync();
Request.Body.Position = 0;
```
Затем мы читаем отредактированные функции в формате GeoJSON:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
Следующий шаг, из отправленного набора функций, мы извлекаем атрибуты, представляющие уникальные идентификаторы соответствующих функций в базе данных. Мы формируем запрос для заполнения специального слоя для редактирования и создаем соответствующий источник данных:
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
Обратите внимание на метод конфигурации `AsTrackableForChanges`. Это специальный метод, который указывает необходимость создания определенного источника данных, способного отслеживать изменения. Первый параметр указывает таблицу, в которую следует отправлять запросы об изменении. Второй указывает, какой атрибут будет считаться идентификатором для внесения изменений в базу данных. Самая интересная часть — третий параметр. При установке значения True он указывает, что слой будет отслеживать появление дубликатов в соответствии со вторым параметром и «перезаписывать» ранее загруженные функции новыми. Однако в случае результатов редактирования, то есть добавления новой функции с тем же идентификатором, будет сгенерирована команда `UPDATE` в соответствии с изменениями по сравнению со старым значением. Если третий параметр установлен на false, при появлении дубликатов будет выброшено исключение, как во время инициализации, так и при редактировании.

Имена атрибутов будут использоваться в качестве имен полей в таблице для редактирования. Важно отметить важный момент относительно обнаружения изменений. Необходимо указать точный тип данных атрибута, который будет храниться в слое для отслеживания изменений, он должен быть точным в отношении вновь добавленных или измененных типов. Например, если мы добавляем новую функцию с `osm_id` типа `Int32`, а указанный тип атрибута в слое — `Int64`, это будет рассматриваться как два разных значения, поскольку нет перегрузки метода `Equal`s, которая выглядит как `Int64.Equals(Int32)`. В будущих версиях это поведение будет рассмотрено и исправлено, если это возможно. Тип третьего параметра будет применяться во время сохранения данных в качестве целевого типа данных таблицы базы данных.

Затем мы подключаемся к базе данных и читаем данные из таблицы:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
Важным моментом является то, что для правильной работы транзакции на уровне базы данных необходимо передать текущую транзакцию в качестве второго параметра во время операции чтения.

Затем нам нужно выполнить ряд преобразований перед отправкой изменений в базу данных:
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
Leaflet генерирует геометрии в системе координат WGS 84, однако схема базы данных требует хранения в Web Mercator. Чтобы преобразовать в систему Web Mercator, мы создаем специальный объект `transformer` и используем его для преобразования.

Кроме того, leaflet заполняет третий параметр координат геометрии Z значением 0. Однако этот параметр не учитывается в нашей схеме базы данных, поэтому мы удаляем его присутствие, установив значение `HasZ` равным false.

Финальным моментом является применение изменений путем замены существующей функции на ту, которая получена от клиента и имеет один и тот же osm_id. Эта операция приведет к обнаружению изменений по отношению к более старым экземплярам функции. В момент вызова `SubmitChangesAsync` произойдет процесс обнаружения изменений, и команды INSERT, DELETE и UPDATE будут отправлены в базу данных в соответствии с вашими изменениями.

Спасибо за чтение до конца. Весь код будет доступен в следующем репозитории: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)