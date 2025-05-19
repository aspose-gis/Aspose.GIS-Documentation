---
title: "Нарисуйте карту. Скользящая карта с тайлами."
type: docs
url: /ru/net/showcases/sliding-map-with-tiles/
description: "Как нарисовать тайлы и построить из них скользящую карту."
weight: 80
aliases:
 - /ru/net/showcases/tiles/
---
# Нарисуйте карту. Скользящая карта с тайлами.
В этой статье мы хотим показать, как с помощью библиотеки [Aspose.GIS](https://www.nuget.org/packages/Aspose.GIS/) и общедоступных данных можно построить скользящую карту, которая будет генерироваться в реальном времени. Благодаря новой функции библиотеки, теперь мы можем запрашивать ГИС-данные из базы данных через SQL-запрос. Вот что мы должны получить в результате:

![Результат](result.png)

Репозиторий с исходным кодом [здесь](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest).

## Подготовка данных.

Прежде всего, нам потребуется геопространственная информация, которую мы сможем загрузить в базу данных. Одним из популярных источников такой информации является `OpenStreetMap`, поэтому давайте воспользуемся им. Наиболее удобный способ, на мой взгляд, — это извлечь данные в формате pbf из общедоступного ресурса https://download.geofabrik.de/ . Например, скачаем [Венгрию](https://download.geofabrik.de/europe/hungary-latest.osm.pbf).

На следующем этапе нам потребуется работающий экземпляр `PostGIS`. Конечно, вы можете использовать локально установленную версию `PostgreSQL`, но мне очень удобно использовать Docker контейнеры. Давайте установим PostGIS с помощью docker compose файла:

```yaml
services:
  postgis:
    image: postgis/postgis
    environment:
      - POSTGRES_DB=gis
      - POSTGRES_USER=gis
      - POSTGRES_PASSWORD=password
    ports:
      - 5432:5432
    volumes:
      - d:\\local_folder:/usr/share/gisdata
```

Том `d:\local_folder:/usr/share/gisdata` необходим для загрузки ГИС-данных с локальной машины.

Далее давайте запустим наш контейнер:

```bash
docker compose up
```

Подключитесь к экземпляру базы данных, используя `pgAdmin`, и создайте там базу данных Венгрии:

![Создать БД](create_db.png)

или через SQL-команду:

```sql
CREATE DATABASE Hungary;
```

Добавьте необходимые расширения в эту базу данных:

![Расширения](add_extention.png)

Это будут расширения `postgis` и `hstore`. hstore — это расширение, которое позволяет использовать тип данных ключ-значение. OpenStreetMap широко использует этот тип для описания атрибутов, которые не попадают в категорию основных, поэтому для них не создаются отдельные поля, но они хранятся в поле tags.

Также есть версия команд, похожая на SQL:

```sql
CREATE EXTENSION IF NOT EXISTS hstore;
CREATE EXTENSION IF NOT EXISTS postgis;
```

Теперь давайте подключимся к контейнеру, в моем случае это `local_folder-postgis-1`:

```bash
docker exec -it local_folder-postgis-1 sh
```

И установите программу, которая будет импортировать данные из файла `pbf` в базу данных:

```bash
apt-get update && apt-get install -y osm2pgsql
```

Убедитесь, что файл `hungary-latest.osm.pbf` находится в вашей папке `local_folder`, а затем запустите команду импорта:

```bash
osm2pgsql --create --database=Hungary --user=gis --password --host=localhost --port=5432 --hstore /usr/share/gisdata/hungary-latest.osm.pbf
```

В случае Венгрии на выполнение этой команды у меня ушло полтора минуты. Опция `--create` означает простой режим создания новой базы данных. Кстати, помимо всего прочего, есть также режим `--append`, который позволяет обновлять данные, если они изменились:

```bash
osm2pgsql --append --slim OSMFILE
```

Опция `--hstore` сообщает приложению дополнительно создать поле `tags` типа hstore для хранения дополнительной информации о признаках и геометриях.

## Бэк-энд

Итак, наши данные готовы к использованию. Следующим шагом на пути к созданию карты является создание бэк-энда. Цель нашего бэк-энда — генерировать специальные `тайлы`, обычно размером `256*256`, из которых, как из мозаики, карта будет собираться в браузере. Каждый тайл уникально идентифицируется комбинацией таких параметров, как Z, который является степенью увеличения/уменьшения масштаба карты, X — это строка в массиве тайлов, а Y — это столбец. Больше о природе тайлов можно прочитать [здесь](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames).

Наш бэк-энд будет на ASP.NET Core соответственно, поэтому давайте начнем с создания проекта. Итак, давайте создадим проект на основе предустановленного шаблона `ASP.NET Core MVC` в `Visual Studio`.

Далее установите NuGet пакет `Aspose.GIS` в проект, который будет генерировать тайлы:

```cmd
dotnet add package Aspose.GIS --version 24.6.0
```

Очистите проект от ненужных файлов. Чтобы структура выглядела примерно так:

![Исследователь решений](project.png)

Затем удалите содержимое папки wwwroot/lib, поскольку мы будем устанавливать наши зависимости через `libman`. Ниже представлена ​​структура файла `libman.json`:
```json
{
  "version": "1.0",
  "defaultProvider": "cdnjs",
  "libraries": [
    {
      "library": "leaflet@1.9.4",
      "destination": "wwwroot/lib/leaflet/"
    },
    {
      "library": "bootstrap@5.3.3",
      "destination": "wwwroot/lib/bootstrap/",
      "files": [
        "css/bootstrap-reboot.min.css"
      ]
    }
  ]
}
```

Добавлены клиентские зависимости в файл `_Layout.cshtml`:

```razor
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>@ViewData["Title"] - Aspose.GIS.TilesTest</title>
    <link href="~/lib/bootstrap/css/bootstrap-reboot.min.css" rel="stylesheet" />
    @await RenderSectionAsync("Styles", required: false)
</head>
<body>
    @RenderBody()
    @await RenderSectionAsync("Scripts", required: false)
</body>
</html>
```

И также отредактируйте `Index.cshtml`:

```razor
@{
    ViewData["Title"] = "Home Page";
}

<div id="map"></div>

@section Styles {
    <link href="~/lib/leaflet/leaflet.min.css" rel="stylesheet" />
    <link href="~/css/map.css" rel="stylesheet" asp-append-version="true"/>
}

@section Scripts {
    <script src="~/lib/leaflet/leaflet.min.js"></script>
    <script src="~/js/map.js" asp-append-version="true"></script>
}
```

В этом случае `bootstrap-reboot.min.css` сбрасывает настройки стиля по умолчанию, а `leaflet.min.js` отвечает за рендеринг карты, то есть сборку частей из тайлов в карту.
Давайте установим высоту блока карты на полную высоту видимой области в файле `map.css`:

```css
#map {
    min-height: 100vh;
}
```

Содержимое файла `map.js` также довольно простое, но немного интереснее:

```javascript
var map = L.map('map').setView([47.59995, 19.36623], 13);
const tiles = L.tileLayer('/tiles/{z}/{x}/{y}.png', {
    maxZoom: 19,
    minZoom: 11
}).addTo(map);
```

Здесь мы используем API библиотеки leaflet, где указываем id блока карты `'map'`, затем в методе `setView` устанавливаем координаты места, с которого начнется начальная загрузка карты, а также масштаб, например, 13. Обратите внимание на метод `tileLayer`, он принимает строку шаблона для запроса тайла к серверу. Этот адрес может быть как абсолютным для доступа к сторонним серверам тайлов, так и относительным, как в нашем случае.

Чтобы реализовать обработчик запросов для генерации тайлов, давайте сначала определим отдельный маршрут в файле `Program.cs`:

```csharp
app.MapControllerRoute(name: "tiles",
  pattern: "tiles/{z}/{x}/{y}.png",
  defaults: new { controller = "Tiles", action = "Index" });

app.MapControllerRoute(
  name: "default",
  pattern: "{controller=Home}/{action=Index}/{id?}");
```

Здесь определены два маршрута, первый для тайлов, а второй — стандартный. В случае `MapControllerRoute` порядок имеет значение, поэтому чтобы избежать неожиданного поведения, стоит размещать маршрут для тайлов перед стандартным маршрутом.

Далее давайте перейдем к самому обработчику. Создайте контроллер `TilesController.cs`:

```csharp
public async Task<ActionResult> Index(int z, int x, int y)
```

И вот теперь у нас есть все необходимые данные для вычисления ограничивающего прямоугольника, охватываемого тайлом в соответствующей системе координат. В текущей реализации наши данные в базе данных хранятся в системе координат Web Mercator. OpenStreetMap по умолчанию предоставляет данные в этой системе координат. Web Mercator — это `projection`(форма системы координат) чаще всего используется для картографирования в различных популярных сервисах.

```csharp
VectorLayer inputLayer;
using (var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary"))
{
  var builder = new DatabaseDataSourceBuilder();

  builder
    .FromQuery(query)
    .GeometryField("way")
    .AddAttribute("osm_id", AttributeDataType.Long)
    .AddAttribute("addr:housenumber", AttributeDataType.String)
    .AddAttribute("building", AttributeDataType.String)
    .AddAttribute("name", AttributeDataType.String)
    .AddAttribute("source", AttributeDataType.String)
    .AddAttribute("admin_level", AttributeDataType.Integer)
    .AddAttribute("place", AttributeDataType.String)
    .AddAttribute("landuse", AttributeDataType.String)
    .AddAttribute("water", AttributeDataType.String);
  conn.Open();

  var inputLayer = await builder.Build().ReadAsync(conn);
}
```

Мы получили один слой, содержащий все геометрии, пересекающиеся с нашим тайлом.

Хорошо, теперь мы можем немного раскрасить карту, например, городами, водоемами или лесами. Для этого нам нужно разбить наш единственный слой на отдельные независимые слои, которые будут соответствовать определенным критериям, таким как леса или реки. Вот пример:

```csharp
var cities = inputLayer.Where(x => x.GetValue<string>("place") == "city");
citiesLayer = CopyToNewLayer(cities, inputLayer);

var forest = inputLayer.Where(x => x.GetValue<string>("landuse") == "forest");
forestLayer = CopyToNewLayer(forest, inputLayer);

var water = inputLayer.Where(x => !x.IsValueNull("water"));
waterLayer = CopyToNewLayer(water, inputLayer);
```

Ниже вы увидите, как мы будем использовать эти слои. Функция `CopyToNewLayer` является вспомогательной, она помогает создавать новые слои; для этой статьи она не имеет большого значения, вы можете посмотреть ее реализацию в репозитории, на который я ссылался в начале статьи.

И теперь нам просто нужно отрендерить все это в PNG тайл и вернуть его клиенту. Это пример кода:

```csharp
using var map = new Map(256, 256);
var pngStream = new MemoryStream();
var labeling = new RuleBasedLabeling
{
  { x => x.GetValue<string>("source") == "polygon",  new SimpleLabeling("addr:housenumber") },
  LabelingRule.CreateElseRule(new SimpleLabeling("name"))
};

map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);            
map.Add(citiesLayer, new SimpleFill { FillColor = Color.PeachPuff }, labeling);
map.Add(forestLayer, new SimpleFill { FillColor = Color.PaleGreen }, labeling);
map.Add(waterLayer, new SimpleFill { FillColor = Color.SkyBlue }, labeling);
map.Add(buildingsLayer, new SimpleFill { FillColor = Color.SandyBrown }, labeling);
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

pngStream.Seek(0, SeekOrigin.Begin);

return File(pngStream, "image/png");
```

Здесь создается объект `Map` со стандартным размером тайла 256x256. По сути, `Map` — это холст для рендеринга тайла. Далее мы инициализируем специальный объект для маркировки, в который передаются правила для рендеринга текста на отрисованных геометрических фигурах, например, номера домов, названия улиц и т. д. В этом случае, если это не полигон и/или атрибут `addr:housenumber` пуст, данные будут взяты из атрибута `name`.

Важным моментом является то, что объекту Map необходимо явно указать систему координат, в которой он будет рендерить:

```csharp
map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
```

Далее нам нужно установить фактическую область тайла, которая должна быть отрисована, а не расширенную область, которую мы запросили из базы данных. Для этого мы явно устанавливаем область рендеринга через свойство `Extent`:

```csharp
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);
```

И затем мы последовательно добавляем слои на тайл. Первый добавляется ниже всех, а последний — сверху.

И наконец, нам просто нужно отрендерить тайл в виде байтового потока в памяти, затем сбросить поток к началу и передать поток платформе ASP.NET Core для дальнейшей передачи клиенту:

```csharp
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

pngStream.Seek(0, SeekOrigin.Begin);

return File(pngStream, "image/png");
```

Надеемся, что нам удалось передать вам основные идеи и техники построения карт. Желаем удачи в ваших экспериментах.