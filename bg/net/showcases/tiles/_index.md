---
title: "Начертаване на карта. Плъзгаща се карта с плочки."
type: docs
url: /bg/net/showcases/sliding-map-with-tiles/
description: "Как да нарисувате плочки и да изградите плъзгаща се карта от тях."
weight: 80
aliases:
 - /bg/net/showcases/tiles/
---
# Начертаване на карта. Плъзгаща се карта с плочки.
В тази статия искаме да покажем как, използвайки библиотеката [Aspose.GIS](https://www.nuget.org/packages/Aspose.GIS/) и публични данни, можете да изградите плъзгаща се карта, която ще бъде генерирана в реално време. Благодарение на новата функция на библиотеката, вече можем да заявят GIS данни от базата данни чрез SQL заявка. Ето какво трябва да получим като резултат:

![Резултат](result.png)

Репозиториен код [тук](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest).

## Подготовка на данни.

Първо, ще ни е необходима геопространствена информация, която можем да заредим в базата данни. Един от популярните източници на такава информация е `OpenStreetMap`, така че нека го използваме. Най-удобният начин според мен е да извлечем данните във формат pbf от публичния ресурс https://download.geofabrik.de/ . Например, нека изтеглим [Унгария](https://download.geofabrik.de/europe/hungary-latest.osm.pbf).

На следващия етап ни трябва работещ екземпляр на `PostGIS`. Разбира се, можете да използвате локално инсталирана версия на `PostgreSQL`, но намирам за много удобно използването на Docker контейнери. Нека инсталираме PostGIS, като използваме docker compose файл:

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

Volume `d:\local_folder:/usr/share/gisdata` е необходим за зареждане на GIS данни от локалната машина.

След това нека стартираме нашия контейнер:

```bash
docker compose up
```

Свържете се с инстанцията на базата данни, като използвате `pgAdmin` и създайте базата данни Hungary там:

![Създаване на БД](create_db.png)

или чрез SQL команда:

```sql
CREATE DATABASE Hungary;
```

Добавете необходимите разширения към тази база данни:

![Разширения](add_extention.png)

Това ще бъдат разширенията `postgis` и `hstore`. hstore е разширение, което ви позволява да използвате типа данни ключ-стойност. OpenStreetMap широко използва този тип за описване на атрибути, които не попадат в категорията на основните, и следователно за тях не се създават отделни полета, но те се съхраняват в полето tags.

Има също така SQL-подобна версия на командите:

```sql
CREATE EXTENSION IF NOT EXISTS hstore;
CREATE EXTENSION IF NOT EXISTS postgis;
```

Сега нека се свържем с контейнера, в моя случай това е `local_folder-postgis-1`:

```bash
docker exec -it local_folder-postgis-1 sh
```

И инсталирайте програмата, която ще импортира данни от `pbf` файла в базата данни:

```bash
apt-get update && apt-get install -y osm2pgsql
```

Уверете се, че файлът `hungary-latest.osm.pbf` е разположен във вашата папка `local_folder` и след това изпълнете командата за импортиране:

```bash
osm2pgsql --create --database=Hungary --user=gis --password --host=localhost --port=5432 --hstore /usr/share/gisdata/hungary-latest.osm.pbf
```

В случая на Унгария, отне около минута и половина за завършване на тази команда. Опцията `--create` означава прост режим на създаване на нова база данни. Между другото, освен всичко останало, има също така режим `--append`, който позволява актуализиране на данните, ако са се променили:

```bash
osm2pgsql --append --slim OSMFILE
```

Опцията `--hstore` казва на приложението да създаде допълнително поле `tags` от тип hstore за съхранение на допълнителна информация за характеристиките и геометриите.

## Бек-енд

Така че, нашите данни са готови за използване. Следващата стъпка по пътя към създаването на карта е създаването на бек-енда. Целта на нашия бек-енд е да генерира специални `tiles`, обикновено с размер `256*256`, от които, като мозайка, картата ще бъде сглобена в браузъра. Всяка плочка е уникално идентифицирана чрез комбинация от такива параметри като Z, който е степента на приближаване/отдалечаване на картата, X е редът в масива от плочки и Y е колоната. Можете да прочетете повече за естеството на плочките [тук](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames).

Нашият бек-енд ще бъде на ASP.NET Core съответно, така че нека започнем със създаването на проекта. Така че нека създадем проект въз основа на предварително инсталирания шаблон `ASP.NET Core MVC` във `Visual Studio`.

След това инсталирайте NuGet пакета `Aspose.GIS` в проекта, който ще генерира плочките:

```cmd
dotnet add package Aspose.GIS --version 24.6.0
```

Почистете проекта от ненужни файлове. Така че структурата да изглежда приблизително както е показано по-долу:

![Прозорец на решението](project.png)

След това изтрийте съдържанието на папката wwwroot/lib, тъй като ще инсталираме нашите зависимости чрез `libman`. Структурата на файла `libman.json` е следната:
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

Добавени са клиентските зависимости в файла `_Layout.cshtml`:

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

И също така редактирайте `Index.cshtml`:

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

В този случай `bootstrap-reboot.min.css` нулира настройките по подразбиране на стила, а `leaflet.min.js` отговаря за рендирането на картата, т.е. сглобяването на частите от плочките в карта.
Нека зададем височината на блока на картата на пълната височина на видимата област във файла `map.css`:

```css
#map {
    min-height: 100vh;
}
```

Съдържанието на файла `map.js` също е доста просто, но малко по-интересно:

```javascript
var map = L.map('map').setView([47.59995, 19.36623], 13);
const tiles = L.tileLayer('/tiles/{z}/{x}/{y}.png', {
    maxZoom: 19,
    minZoom: 11
}).addTo(map);
```

Тук използваме API на библиотеката leaflet, където посочваме идентификатора на блока на картата `'map'`, след това в метода `setView` задаваме координатите на мястото, от което ще започне първоначалното зареждане на картата, и също така мащаба, например 13. Обърнете внимание на метода `tileLayer`, той приема низ за шаблон за заявка към сървъра. Този адрес може да бъде или абсолютен за достъп до сървъри на плочки от трети страни, или относителен както в нашия случай.

За да реализираме обработчика на заявки за генериране на плочки, трябва първо да създадем бек-енд:

```csharp
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

Получихме един слой, който съдържа всички геометрии, пресичащи нашата плочка.

Добре, сега можем да оцветим картата малко, като градове, водни басейни или гори. За да направим това, трябва да разделим нашия единичен слой на отделни независими слоеве, които ще отговарят на специфични критерии, като гори или реки. Ето пример:

```csharp
var cities = inputLayer.Where(x => x.GetValue<string>("place") == "city");
citiesLayer = CopyToNewLayer(cities, inputLayer);

var forest = inputLayer.Where(x => x.GetValue<string>("landuse") == "forest");
forestLayer = CopyToNewLayer(forest, inputLayer);

var water = inputLayer.Where(x => !x.IsValueNull("water"));
waterLayer = CopyToNewLayer(water, inputLayer);
```

По-долу ще видите как ще използваме тези слоеве. Функцията `CopyToNewLayer` е спомагателна, тя помага да се създават нови слоеве; за тази статия тя не е от голямо значение, можете да разгледате нейната реализация в хранилището, което посочих в началото на статията.

И сега просто трябва да рендираме всичко това в PNG плочка и да я върнем на клиента. Това е примерен код:

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

Тук се създава обект `Map` със стандартен размер на плочката 256x256. По същество `Map` е платно за рендиране на плочката. След това инициализираме специален обект за маркиране, към който се предават правила за рендиране на текст върху нарисуваните геометрични форми, например номера на къщи, имена на улици и т.н. В този случай, ако не е многоъгълник и/или атрибутът `addr:housenumber` е празен, данните ще бъдат взети от атрибута `name`.

Важна точка е, че обектът Map трябва изрично да посочи координатна система, в която ще рендира:

```csharp
map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
```

След това трябва да зададем действителната област на плочката, която трябва да бъде рендирана, а не разширената област, която поискахме от базата данни. За да направим това, изрично задаваме областта на рендиране чрез свойството `Extent`:

```csharp
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);
```

И след това последователно добавяме слоеве към плочката. Първият се добавя под всички останали, а последният е отгоре.

И накрая просто трябва да рендираме плочката като байтов поток в паметта, след което да нулираме потока до началото и да предадем потока на платформата ASP.NET Core за по-нататъшно прехвърляне към клиента:

```csharp
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

pngStream.Seek(0, SeekOrigin.Begin);

return File(pngStream, "image/png");
```

Надяваме се, че успяхме да предадем основните идеи и техники за изграждане на картата на вас. Пожелаваме ви успех в експериментите си.