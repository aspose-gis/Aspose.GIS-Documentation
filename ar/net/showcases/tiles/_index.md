---
title: "رسم خريطة. خريطة منزلقة مع مربعات."
type: docs
url: /ar/net/showcases/sliding-map-with-tiles/
description: "كيفية رسم المربعات وبناء خريطة منزلقة منها."
weight: 80
aliases:
 - /ar/net/showcases/tiles/
---
# رسم خريطة. خريطة منزلقة مع مربعات.
في هذا المقال، نريد أن نوضح كيف أنه باستخدام مكتبة [Aspose.GIS](https://www.nuget.org/packages/Aspose.GIS/) والبيانات العامة، يمكنك بناء خريطة منزلقة سيتم إنشاؤها في الوقت الفعلي. بفضل ميزة المكتبة الجديدة، يمكننا الآن الاستعلام عن بيانات GIS من قاعدة البيانات عبر استعلام SQL. إليك ما يجب أن نحصل عليه كنتيجة:

![النتيجة](result.png)

المستودع المصدر [هنا](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest).

## تجهيز البيانات.

أولاً، سنحتاج إلى معلومات جغرافية يمكننا تحميلها في قاعدة البيانات. أحد المصادر الشائعة لمثل هذه المعلومات هو `OpenStreetMap` ، لذلك دعونا نستخدمه. الطريقة الأكثر ملاءمة، في رأيي، هي استخراج البيانات بتنسيق pbf من المورد العام https://download.geofabrik.de/ . على سبيل المثال، لنقم بتنزيل [المجر](https://download.geofabrik.de/europe/hungary-latest.osm.pbf).

في المرحلة التالية، نحتاج إلى مثيل عامل لـ `PostGIS`. بالطبع، يمكنك استخدام نسخة مثبتة محليًا من `PostgreSQL` ، لكنني أجد أنه من المريح جدًا استخدام حاويات Docker. دعنا نقوم بتثبيت PostGIS باستخدام ملف docker compose:

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

الحجم `d:\local_folder:/usr/share/gisdata` مطلوب لتحميل بيانات GIS من الجهاز المحلي.

بعد ذلك، دعنا نقوم بتشغيل الحاوية الخاصة بنا:

```bash
docker compose up
```

اتصل بمثيل قاعدة البيانات باستخدام `pgAdmin` وقم بإنشاء قاعدة بيانات المجر هناك:

![إنشاء DB](create_db.png)

أو من خلال أمر SQL:

```sql
CREATE DATABASE Hungary;
```

أضف الامتدادات الضرورية إلى هذه القاعدة البيانات:

![الامتدادات](add_extention.png)

ستكون هذه امتدادات `postgis` و `hstore`. hstore هو امتداد يسمح لك باستخدام نوع بيانات المفتاح والقيمة. يستخدم OpenStreetMap على نطاق واسع هذا النوع لوصف السمات التي لا تقع ضمن فئة العناصر الرئيسية، وبالتالي لا يتم إنشاء حقول منفصلة لها، ولكن يتم تخزينها في حقل العلامات.

هناك أيضًا نسخة شبيهة بـ SQL من الأوامر:

```sql
CREATE EXTENSION IF NOT EXISTS hstore;
CREATE EXTENSION IF NOT EXISTS postgis;
```

الآن دعنا نتصل بالحاوية، في حالتي هي `local_folder-postgis-1`:

```bash
docker exec -it local_folder-postgis-1 sh
```

وقم بتثبيت البرنامج الذي سيستورد البيانات من ملف `pbf` إلى قاعدة البيانات:

```bash
apt-get update && apt-get install -y osm2pgsql
```

تأكد من أن ملف `hungary-latest.osm.pbf` موجود في مجلد `local_folder` الخاص بك ثم قم بتشغيل أمر الاستيراد:

```bash
osm2pgsql --create --database=Hungary --user=gis --password --host=localhost --port=5432 --hstore /usr/share/gisdata/hungary-latest.osm.pbf
```

في حالة المجر، استغرق مني الأمر دقيقة ونصف لإكمال هذا الأمر. يشير الخيار `--create` إلى وضع الإنشاء البسيط لقاعدة بيانات جديدة. بالمناسبة، بالإضافة إلى كل شيء آخر، هناك أيضًا وضع `--append` ، والذي يسمح بتحديث البيانات إذا تغيرت:

```bash
osm2pgsql --append --slim OSMFILE
```

يشير الخيار `--hstore` إلى أن التطبيق سيقوم بإنشاء حقل `tags` من نوع hstore إضافي لتخزين معلومات إضافية حول الميزات والهندسة.

## الواجهة الخلفية

إذن، بياناتنا جاهزة للاستخدام. الخطوة التالية في طريق إنشاء الخريطة هي إنشاء الواجهة الخلفية. هدف الواجهة الخلفية لدينا هو إنشاء `tiles` خاصة ، عادةً بحجم `256 * 256` ، والتي سيتم تجميعها مثل فسيفساء في المتصفح. يتم تحديد كل مربع بشكل فريد من خلال مجموعة من المعلمات مثل Z ، وهي درجة التكبير / التصغير للخريطة ، و X هو الصف في مصفوفة المربعات ، و Y هو العمود. يمكنك قراءة المزيد حول طبيعة المربعات [هنا](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames).

ستكون الواجهة الخلفية لدينا على ASP.NET Core وفقًا لذلك، لذا دعنا نبدأ بإنشاء المشروع. إذن لنقم بإنشاء مشروع بناءً على قالب `ASP.NET Core MVC` المثبت مسبقًا في `Visual Studio`.

بعد ذلك ، قم بتثبيت حزمة NuGet `Aspose.GIS` في المشروع الذي سيقوم بإنشاء المربعات:

```cmd
dotnet add package Aspose.GIS --version 24.6.0
```

نظف المشروع من الملفات غير الضرورية. بحيث يبدو الهيكل كما هو موضح أدناه:

![مستكشف الحل](project.png)

ثم احذف محتويات مجلد wwwroot / lib ، حيث سنقوم بتثبيت تبعياتنا من خلال `libman`. فيما يلي هيكل ملف `libman.json`:
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

تمت إضافة تبعيات العميل في ملف `_Layout.cshtml`:

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

وقم أيضًا بتحرير `Index.cshtml`:

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

في هذه الحالة ، يقوم `bootstrap-reboot.min.css` بإعادة تعيين إعدادات النمط الافتراضية ، و `leaflet.min.js` مسؤول عن عرض الخريطة ، أي تجميع القطع من المربعات في خريطة. دعنا نحدد ارتفاع كتلة الخريطة إلى الارتفاع الكامل للمنطقة المرئية في ملف `map.css`:

```css
#map {
    min-height: 100vh;
}
```

محتوى ملف `map.js` بسيط جدًا ، ولكنه أكثر إثارة للاهتمام:

```javascript
var map = L.map('map').setView([47.59995, 19.36623], 13);
const tiles = L.tileLayer('/tiles/{z}/{x}/{y}.png', {
    maxZoom: 19,
    minZoom: 11
}).addTo(map);
```

هنا نستخدم واجهة برمجة تطبيقات مكتبة leaflet ، حيث نحدد معرف كتلة الخريطة `'map'` ، ثم في طريقة `setView` نحدد إحداثيات المكان الذي سيبدأ منه تحميل الخريطة الأولي، ومقياسًا أيضًا، على سبيل المثال 13. لاحظ طريقة `tileLayer` ، فهي تقبل سلسلة نمط لطلب المربعات للخادم. يمكن أن يكون هذا العنوان مطلقًا للوصول إلى خوادم المربعات التابعة لطرف ثالث أو نسبيًا كما هو الحال في حالتنا.

لتنفيذ معالج الطلب لتوليد المربعات، دعنا نحدد أولاً مسارًا منفصلاً في ملف `Program.cs`:

```csharp
app.MapControllerRoute(name: "tiles",
  pattern: "tiles/{z}/{x}/{y}.png",
  defaults: new { controller = "Tiles", action = "Index" });

app.MapControllerRoute(
  name: "default",
  pattern: "{controller=Home}/{action=Index}/{id?}");
```

هنا ، يتم تعريف مسارين ، الأول للمربعات والثاني هو المسار القياسي. في حالة `MapControllerRoute` ، يكون الترتيب مهمًا ، لذلك لتجنب السلوك غير المتوقع ، يجدر وضع المسار الخاص بالمربعات قبل المسار القياسي.

بعد ذلك ، دعنا ننتقل إلى المعالج نفسه. قم بإنشاء وحدة التحكم `TilesController.cs`:

```csharp
using Aspose.GIS;
using Microsoft.AspNetCore.Mvc;
using Npgsql;
using System.Data;
using System.IO;

namespace YourProjectName.Controllers
{
    public class TilesController : Controller
    {
        [HttpGet("tiles/{z}/{x}/{y}.png")]
        public async Task<IActionResult> Index(int z, int x, int y)
        {
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

            var cities = inputLayer.Where(x => x.GetValue<string>("place") == "city");
            citiesLayer = CopyToNewLayer(cities, inputLayer);

            var forest = inputLayer.Where(x => x.GetValue<string>("landuse") == "forest");
            forestLayer = CopyToNewLayer(forest, inputLayer);

            var water = inputLayer.Where(x => !x.IsValueNull("water"));
            waterLayer = CopyToNewLayer(water, inputLayer);

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
            map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

            pngStream.Seek(0, SeekOrigin.Begin);

            return File(pngStream, "image/png");
        }
    }
}
```

هنا ، يتم إنشاء كائن `Map` بحجم المربعات القياسي 256x256. بشكل أساسي ، `Map` هو لوحة رسم للمربع. بعد ذلك ، نقوم بتهيئة كائن خاص للتسمية ، والذي يتم تمرير إليه قواعد لعرض النص على الأشكال الهندسية المرسومة ، مثل أرقام المنازل أو أسماء الشوارع وما إلى ذلك. في هذه الحالة ، إذا لم يكن مضلعًا و / أو كانت سمة `addr: housenumber` فارغة ، فسيتم أخذ البيانات من سمة `name`.

نقطة مهمة هي أن كائن الخريطة يحتاج إلى تحديد نظام الإحداثيات الذي سيرسم به بشكل صريح:

```csharp
map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
```

بعد ذلك ، نحتاج إلى تعيين المنطقة الفعلية للمربع التي يجب عرضها ، وليس المنطقة الموسعة التي طلبناها من قاعدة البيانات. للقيام بذلك ، نقوم بتعيين منطقة العرض بشكل صريح من خلال خاصية `Extent`:

```csharp
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);
```

ثم نضيف ببساطة الطبقات بالتسلسل إلى المربع. الأولى تضاف أسفل الكل ، والأخيرة في الأعلى.

وأخيرًا نحتاج فقط إلى عرض المربع كتدفق بايت في الذاكرة ، ثم إعادة تعيين التدفق إلى البداية ، وتمرير التدفق إلى منصة ASP.NET Core لمزيد من النقل إلى العميل:

```csharp
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

pngStream.Seek(0, SeekOrigin.Begin);

return File(pngStream, "image/png");
```

نأمل أن نتمكن من نقل الأفكار والتقنيات الأساسية لبناء الخريطة إليك. نتمنى لك حظًا سعيدًا في تجاربك.