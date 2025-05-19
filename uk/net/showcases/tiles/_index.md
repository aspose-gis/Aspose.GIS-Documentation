---
title: "Намалюйте карту. Ковзна карта з плитками."
type: docs
url: /uk/net/showcases/sliding-map-with-tiles/
description: "Як малювати плитки та будувати ковзну карту з них."
weight: 80
aliases:
 - /uk/net/showcases/tiles/
---
# Намалюйте карту. Ковзна карта з плитками.
У цій статті ми хочемо показати, як за допомогою бібліотеки [Aspose.GIS](https://www.nuget.org/packages/Aspose.GIS/) та загальнодоступних даних можна побудувати ковзну карту, яка генеруватиметься в реальному часі. Завдяки новій функції бібліотеки ми тепер можемо запитувати геоінформаційні дані з бази даних через SQL-запит. Ось що ми повинні отримати в результаті:

![Результат](result.png)

Репозиторій вихідного коду [тут](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest).

## Підготовка даних.

Насамперед нам знадобиться геопросторова інформація, яку ми можемо завантажити в базу даних. Одним із популярних джерел такої інформації є `OpenStreetMap`, тож давайте використаємо його. Найзручніший спосіб, на мою думку, — це витягувати дані у форматі pbf з загальнодоступного ресурсу https://download.geofabrik.de/ . Наприклад, завантажимо [Угорщину](https://download.geofabrik.de/europe/hungary-latest.osm.pbf).

На наступному етапі нам потрібен робочий екземпляр `PostGIS`. Звичайно, ви можете використовувати локально встановлену версію `PostgreSQL`, але я вважаю дуже зручним використання Docker-контейнерів. Давайте встановимо PostGIS за допомогою файлу docker compose:

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

Том `d:\local_folder:/usr/share/gisdata` потрібен для завантаження геоінформаційних даних з локальної машини.

Далі давайте запустимо наш контейнер:

```bash
docker compose up
```

Підключіться до екземпляра бази даних, використовуючи `pgAdmin`, і створіть там базу даних Угорщини:

![Створити БД](create_db.png)

або через SQL-команду:

```sql
CREATE DATABASE Hungary;
```

Додайте необхідні розширення до цієї бази даних:

![Розширення](add_extention.png)

Це будуть розширення `postgis` та `hstore`. hstore — це розширення, яке дозволяє використовувати тип даних ключ-значення. OpenStreetMap широко використовує цей тип для опису атрибутів, які не входять до категорії основних, тому для них не створюються окремі поля, але вони зберігаються в полі tags.

Також є версія команд, подібна до SQL:

```sql
CREATE EXTENSION IF NOT EXISTS hstore;
CREATE EXTENSION IF NOT EXISTS postgis;
```

Тепер давайте підключимося до контейнера, у моєму випадку це `local_folder-postgis-1`:

```bash
docker exec -it local_folder-postgis-1 sh
```

І встановіть програму, яка імпортуватиме дані з файлу `pbf` в базу даних:

```bash
apt-get update && apt-get install -y osm2pgsql
```

Переконайтеся, що файл `hungary-latest.osm.pbf` знаходиться у вашій папці `local_folder`, а потім запустіть команду імпорту:

```bash
osm2pgsql --create --database=Hungary --user=gis --password --host=localhost --port=5432 --hstore /usr/share/gisdata/hungary-latest.osm.pbf
```

У випадку Угорщини на завершення цієї команди у мене пішло півтори хвилини. Опція `--create` означає простий режим створення нової бази даних. До речі, крім усього іншого, існує також режим `--append`, який дозволяє оновлювати дані, якщо вони змінилися:

```bash
osm2pgsql --append --slim OSMFILE
```

Опція `--hstore` повідомляє програмі додатково створити поле `tags` типу hstore для зберігання додаткової інформації про об’єкти та геометрії.

## Бек-енд

Отже, наші дані готові до використання. Наступним кроком на шляху до створення карти є створення бек-енду. Мета нашого бек-енду — генерувати спеціальні `tiles`, зазвичай розміром `256*256`, з яких, як мозаїка, карта буде зібрана в браузері. Кожна плитка унікально ідентифікується комбінацією таких параметрів, як Z, що є ступенем збільшення/зменшення масштабу карти, X — це рядок у масиві плиток, а Y — це стовпець. Більше про природу плиток можна прочитати [тут](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames).

Наш бек-енд буде на ASP.NET Core відповідно, тож давайте почнемо зі створення проєкту. Отже, давайте створимо проєкт на основі попередньо встановленого шаблону `ASP.NET Core MVC` у `Visual Studio`.

Далі встановіть NuGet пакет `Aspose.GIS` у проект, який генеруватиме плитки:

```cmd
dotnet add package Aspose.GIS --version 24.6.0
```

Очистіть проєкт від непотрібних файлів. Щоб структура виглядала приблизно так, як показано нижче:

![Провідник рішень](project.png)

Потім видаліть вміст папки wwwroot/lib, оскільки ми встановлюватимемо наші залежності через `libman`. Нижче наведена структура файлу `libman.json`:
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


Додано залежності клієнта у файл `_Layout.cshtml`:

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

І також відредагуйте `Index.cshtml`:

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

У цьому випадку `bootstrap-reboot.min.css` скидає налаштування стилю за замовчуванням, а `leaflet.min.js` відповідає за рендеринг карти, тобто збирання частин із плиток у карту. Давайте встановимо висоту блоку карти на повну висоту видимої області у файлі `map.css`:

```css
#map {
    min-height: 100vh;
}
```

Вміст файлу `map.js` також досить простий, але трохи цікавіший:

```javascript
var map = L.map('map').setView([47.59995, 19.36623], 13);
const tiles = L.tileLayer('/tiles/{z}/{x}/{y}.png', {
    maxZoom: 19,
    minZoom: 11
}).addTo(map);
```

Тут ми використовуємо API бібліотеки leaflet, де вказується ідентифікатор блоку карти `'map'`, потім у методі `setView` встановлюються координати місця, з якого почнеться початкове завантаження карти, а також масштаб, наприклад, 13. Зверніть увагу на метод `tileLayer`, він приймає рядковий шаблон для запиту плитки до сервера. Ця адреса може бути абсолютною для отримання доступу до сторонніх серверів плиток або відносною, як у нашому випадку.

Щоб реалізувати обробник запитів для генерації плиток, давайте спочатку визначимо окремий маршрут у файлі `Program.cs`:

```csharp
app.MapControllerRoute(name: "tiles",
  pattern: "tiles/{z}/{x}/{y}.png",
  defaults: new { controller = "Tiles", action = "Index" });

app.MapControllerRoute(
  name: "default",
  pattern: "{controller=Home}/{action=Index}/{id?}");
```

Ми вказали, що передані координати відповідають системі координат 3857 (Web Mercator).

Важливий момент полягає в тому, що на поточному етапі інтеграції бази даних бібліотека може читати геометрії у форматі `WKB`, але краще використовувати `EWKB`, тобто Extended Well-Known Binary, тоді не потрібно буде передавати інформацію про просторову систему координат як окреме поле, оскільки вона вже буде вбудована в інформацію про геометрію. Для цих цілей ми використовуємо функцію `ST_AsEWKB`.

Функція `ST_ClipByBox2D` використовується для обрізання геометрій, які виходять за межі кордонів обмежувального прямокутника.

Добре, тепер нам просто потрібно відрендерити все це в PNG-плитку та повернути її клієнту. Це приклад коду:

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

Сподіваємося, нам вдалося передати вам основні ідеї та методи побудови карти. Бажаємо успіхів у ваших експериментах.