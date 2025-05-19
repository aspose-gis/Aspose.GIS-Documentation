---
title: "نقشه بکشید. نقشه لغزنده با کاشی‌ها."
type: docs
url: /fa/net/showcases/sliding-map-with-tiles/
description: "چگونگی رسم کاشی‌ها و ساخت یک نقشه لغزنده از آن‌ها."
weight: 80
aliases:
 - /fa/net/showcases/tiles/
---
# نقشه بکشید. نقشه لغزنده با کاشی‌ها.
در این مقاله، می‌خواهیم نشان دهیم که چگونه با استفاده از کتابخانه [Aspose.GIS](https://www.nuget.org/packages/Aspose.GIS/) و داده‌های عمومی، می‌توان یک نقشه لغزنده ساخت که به‌صورت لحظه‌ای تولید شود. به لطف ویژگی جدید کتابخانه، اکنون می‌توانیم داده‌های GIS را از پایگاه داده از طریق پرس‌وجوی SQL بازیابی کنیم. این نتیجه‌ای است که باید بدست آوریم:

![نتیجه](result.png)

مخزن کد منبع [اینجا](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest).

## آماده‌سازی داده‌ها.
اول از همه، به اطلاعات جغرافیایی نیاز داریم که بتوانیم آن را در پایگاه داده بارگیری کنیم. یکی از منابع محبوب این نوع اطلاعات `OpenStreetMap` است، بنابراین بیایید از آن استفاده کنیم. راحت‌ترین راه، به نظر من، استخراج داده‌ها در قالب pbf از منبع عمومی https://download.geofabrik.de/ است. برای مثال، بیایید [مجارستان](https://download.geofabrik.de/europe/hungary-latest.osm.pbf) را دانلود کنیم.

در مرحله بعدی، به یک نمونه کارکردن `PostGIS` نیاز داریم. البته می‌توانید از نسخه نصب شده محلی `PostgreSQL` استفاده کنید، اما من استفاده از کانتینرهای Docker را بسیار راحت می‌دانم. بیایید PostGIS را با استفاده از فایل docker compose نصب کنیم:

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

حجم `d:\local_folder:/usr/share/gisdata` برای بارگیری داده‌های GIS از ماشین محلی مورد نیاز است.

سپس، بیایید کانتینر خود را اجرا کنیم:

```bash
docker compose up
```

با استفاده از `pgAdmin` به نمونه پایگاه داده متصل شوید و پایگاه داده مجارستان را در آنجا ایجاد کنید:

![ایجاد DB](create_db.png)

یا از طریق دستور SQL:

```sql
CREATE DATABASE Hungary;
```

افزونه‌های لازم را به این پایگاه داده اضافه کنید:

![افزونه‌ها](add_extention.png)

اینها افزونه‌های `postgis` و `hstore` خواهند بود. hstore یک افزونه است که به شما امکان می‌دهد از نوع داده کلید-مقدار استفاده کنید. OpenStreetMap به‌طور گسترده از این نوع برای توصیف ویژگی‌هایی استفاده می‌کند که در دسته اصلی قرار نمی‌گیرند، بنابراین فیلدهای جداگانه‌ای برای آنها ایجاد نمی‌شود، اما در فیلد برچسب‌ها ذخیره می‌شوند.

همچنین یک نسخه شبیه به SQL از دستورات وجود دارد:

```sql
CREATE EXTENSION IF NOT EXISTS hstore;
CREATE EXTENSION IF NOT EXISTS postgis;
```

اکنون بیایید به کانتینر متصل شویم، در مورد من `local_folder-postgis-1` است:

```bash
docker exec -it local_folder-postgis-1 sh
```

و برنامه‌ای را که داده‌ها را از فایل `pbf` وارد پایگاه داده می‌کند نصب کنید:

```bash
apt-get update && apt-get install -y osm2pgsql
```

مطمئن شوید که فایل `hungary-latest.osm.pbf` در پوشه `local_folder` شما قرار دارد و سپس دستور import را اجرا کنید:

```bash
osm2pgsql --create --database=Hungary --user=gis --password --host=localhost --port=5432 --hstore /usr/share/gisdata/hungary-latest.osm.pbf
```

در مورد مجارستان، تکمیل این دستور یک و نیم دقیقه طول کشید. گزینه `--create` به معنای حالت ایجاد ساده پایگاه داده جدید است. به‌علاوه، علاوه بر همه موارد دیگر، حالت `--append` نیز وجود دارد که امکان به‌روزرسانی داده‌ها در صورت تغییر آنها را فراهم می‌کند:

```bash
osm2pgsql --append --slim OSMFILE
```

گزینه `--hstore` به برنامه می‌گوید که یک فیلد `tags` از نوع hstore را به‌طور اضافی برای ذخیره اطلاعات اضافی در مورد ویژگی‌ها و هندسه‌ها ایجاد کند.

## بک‌اند
بنابراین، داده‌های ما آماده استفاده هستند. مرحله بعدی در مسیر ایجاد نقشه، ایجاد بک‌اند است. هدف از بک‌اند ما تولید کاشی‌های خاص، معمولاً به اندازه `256*256` است که از آنها، مانند یک موزائیک، نقشه در مرورگر جمع می‌شود. هر کاشی به‌طور منحصربه‌فرد با ترکیبی از پارامترهایی مانند Z که درجه بزرگنمایی/کوچک‌نمایی نقشه است، X ردیف در آرایه کاشی و Y ستون شناسایی می‌شود. می‌توانید اطلاعات بیشتری در مورد ماهیت کاشی‌ها [اینجا](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames) بخوانید.

بک‌اند ما به‌طور متناوب بر روی ASP.NET Core خواهد بود، بنابراین بیایید با ایجاد پروژه شروع کنیم. پس بیایید پروژه‌ای را بر اساس الگوی از پیش نصب شده `ASP.NET Core MVC` در `Visual Studio` ایجاد کنیم.

سپس بسته NuGet `Aspose.GIS` را در پروژه‌ای که کاشی‌ها را تولید می‌کند نصب کنید:

```cmd
dotnet add package Aspose.GIS --version 24.6.0
```

پروژه را از فایل‌های غیرضروری پاک کنید. بنابراین ساختار آن تقریباً مانند تصویر زیر باشد:

![اکتشافگر راه حل](project.png)

سپس محتویات پوشه wwwroot/lib را حذف کنید، زیرا وابستگی‌های ما از طریق `libman` نصب می‌شوند. ساختار فایل `libman.json` در زیر آمده است:
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

وابستگی‌های کلاینت را در فایل `_Layout.cshtml` اضافه کنید:

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

و همچنین فایل `Index.cshtml` را ویرایش کنید:

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

در این مورد، `bootstrap-reboot.min.css` تنظیمات سبک پیش‌فرض را بازنشانی می‌کند و `leaflet.min.js` مسئول رندر کردن نقشه است، یعنی جمع‌آوری قطعات از کاشی‌ها در یک نقشه. بیایید ارتفاع بلوک نقشه را به ارتفاع کامل ناحیه قابل مشاهده در فایل `map.css` تنظیم کنیم:

```css
#map {
    min-height: 100vh;
}
```

محتوای فایل `map.js` نیز بسیار ساده است، اما کمی جالب‌تر:

```javascript
var map = L.map('map').setView([47.59995, 19.36623], 13);
const tiles = L.tileLayer('/tiles/{z}/{x}/{y}.png', {
    maxZoom: 19,
    minZoom: 11
}).addTo(map);
```

در اینجا ما از API کتابخانه leaflet استفاده می‌کنیم، جایی که شناسه بلوک نقشه `'map'` را مشخص می‌کنیم، سپس در روش `setView` مختصات مکانی را تنظیم می‌کنیم که بارگیری اولیه نقشه از آنجا شروع شود و همچنین مقیاس، به عنوان مثال 13. توجه داشته باشید که روش `tileLayer` یک الگوی رشته برای درخواست کاشی به سرور را می‌پذیرد. این آدرس می‌تواند مطلق برای دسترسی به سرورهای کاشی شخص ثالث یا نسبی باشد همانطور که در مورد ما است. مسیر `/tiles/{z}/{x}/{y}.png` هنوز توسط ما پیاده‌سازی نشده است و این مهم‌ترین بخش روایت ما است که هنوز باید آن را پیاده‌سازی کنیم.

برای پیاده‌سازی هندلر درخواست برای تولید کاشی‌ها، بیایید ابتدا یک مسیر جداگانه در فایل `Program.cs` تعریف کنیم:

```csharp
app.MapControllerRoute(name: "tiles",
  pattern: "tiles/{z}/{x}/{y}.png",
  defaults: new { controller = "Tiles", action = "Index" });

app.MapControllerRoute(
  name: "default",
  pattern: "{controller=Home}/{action=Index}");
```

و سپس کنترلر `Tiles` را اضافه کنید:

```csharp
using Microsoft.AspNetCore.Mvc;
using Aspose.GIS;
using Aspose.GIS.VectorLayers;
using Aspose.GIS.Rendering;
using System.IO;
using System.Threading.Tasks;
using Npgsql;

namespace YourProjectName.Controllers
{
    public class TilesController : Controller
    {
        [HttpGet("tiles/{z}/{x}/{y}.png")]
        public async Task<IActionResult> Index(int z, int x, int y)
        {
            // Logic to generate the tile here
            return File(...); // Return the image as a file result
        }
    }
}
```

خوب، اکنون می‌توانیم کد تولید کاشی را در کنترلر `Tiles` اضافه کنیم. این یک نمونه کد است:

```csharp
using Microsoft.AspNetCore.Mvc;
using Aspose.GIS;
using Aspose.GIS.VectorLayers;
using Aspose.GIS.Rendering;
using System.IO;
using System.Threading.Tasks;
using Npgsql;

namespace YourProjectName.Controllers
{
    public class TilesController : Controller
    {
        [HttpGet("tiles/{z}/{x}/{y}.png")]
        public async Task<IActionResult> Index(int z, int x, int y)
        {
            double scale = 1 / Math.Pow(2, z);
            double minX = x * scale;
            double minY = y * scale;
            double maxX = (x + 1) * scale;
            double maxY = (y + 1) * scale;

            VectorLayer inputLayer;
            using (var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary"))
            {
                var builder = new DatabaseDataSourceBuilder();

                builder
                    .FromQuery(query) // Your query here
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

                inputLayer = await builder.Build().ReadAsync(conn);
            }

            var map = new Map(256, 256);
            map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
            map.Extent = new Extent(minX, minY, maxX, maxY, SpatialReferenceSystem.WebMercator);

            // Add layers and render the map here

            using var pngStream = new MemoryStream();
            map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);
            pngStream.Seek(0, SeekOrigin.Begin);

            return File(pngStream, "image/png");
        }
    }
}
```

امیدوارانه توانسته‌ایم ایده‌ها و تکنیک‌های اساسی ساخت نقشه را به شما منتقل کنیم. ما برای آزمایشات شما آرزوی موفقیت داریم.