---
title: به‌روزرسانی‌های Aspose.GIS ویرایش ویژگی‌ها و هندسه‌ها و ذخیره تغییرات در پایگاه داده.
type: docs
url: /fa/net/showcases/saving-changes-to-database/
description: این مقاله آخرین پیشرفت‌های کتابخانه Aspose.GIS را بررسی می‌کند، با تمرکز بر قابلیت‌های جدید برای تشخیص و ذخیره تغییرات هندسی در یک برنامه نقشه.
weight: 80
---
# به‌روزرسانی‌های Aspose.GIS: ویرایش ویژگی‌ها و هندسه‌ها و ذخیره تغییرات در پایگاه داده.

## مقدمه

با توجه به تغییرات اخیر در کتابخانه [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis)، مهم است که برخی از آن‌ها را برجسته کنیم تا نادیده گرفته نشوند. در این مقاله، قابلیت جدید تشخیص و ذخیره تغییرات هندسی و ویژگی‌ها در پایگاه داده را مورد بحث قرار خواهیم داد.

به عنوان مثال برای نمایش، به کار بر روی برنامه‌ای که در مقاله ["رسم نقشه. یک نقشه لغزنده با کاشی"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) توصیف شده است ادامه خواهیم داد و آن را با افزودن عملکردهای ویرایش اشیاء روی نقشه کمی گسترش می‌دهیم. مجموعه داده همانند مقاله قبلی باقی می‌ماند.

## Front-end

برای نمایش قابلیت‌های اصلاح هندسه، یک افزونه منبع باز محبوب برای [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/) را انتخاب کردیم.

این کتابخانه را از طریق فایل libman.json اضافه می‌کنیم:
![Libman](libman.png)

سپس سبک‌ها و اسکریپت‌ها را به صفحه متصل می‌کنیم:
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

برای اهداف نمایشی، قابلیت‌های ویرایش را به ساختمان‌ها محدود خواهیم کرد. کاربر روی دکمه چپ ماوس روی نقشه کلیک می‌کند و اگر ساختمانی در آن مکان وجود داشته باشد، برجسته شده و برای ویرایش در دسترس قرار می‌گیرد. این کار با پوشاندن یک لایه اضافی بر روی کاشی‌ها انجام می‌شود.

هنگامی که کاربر روی نقشه کلیک می‌کند، کتابخانه Leaflet مختصات جغرافیایی کلیک را محاسبه می‌کند. این مختصات را به Back-end ارسال می‌کنیم و در پایگاه داده برای هندسه‌هایی که با نقطه کلیک شده تلاقی دارند جستجو می‌کنیم. اگر ساختمان‌هایی در بین این هندسه‌ها وجود داشته باشد، آن‌ها را برمی‌گردانیم.

ساختمان‌ها از Back-end در قالب `GeoJSON` بازگردانده می‌شوند و به عنوان یک لایه جداگانه برای ویرایش به نقشه اضافه می‌شوند. نحوه رسیدگی به کلیک:
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

ما یک گروه لایه دائمی برای هندسه‌های قابل ویرایش، `featuresLayer` داریم که به نقشه اضافه شده است. بررسی می‌کنیم که آیا کلیک روی هندسه بارگذاری شده انجام شده است یا خیر و در غیر این صورت، درخواستی به Back-end ارسال می‌کنیم تا چند ضلعی‌هایی که نمایانگر ساختمان‌ها هستند را بارگیری کنیم. لایه‌های ویژگی بارگذاری شده به featuresLayer اضافه می‌شوند و حالت ویرایش فعال می‌شود.

در اینجا نحوه عملکرد بارگذاری ویژگی‌ها و تبدیل از `GeoJSON` است:
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

پس از جلسه ویرایش، کاربر روی دکمه `Save` سفارشی کلیک می‌کند:

![Save](save-btn.png)

صفحه را تازه‌سازی کنید و تغییرات را مشاهده کنید:

![Changes](changes.png)

متأسفانه، تابع `tiles.redraw()` به درستی کار نمی‌کند زیرا کاشی‌های بارگذاری شده قبلی حافظه پنهان می‌شوند که نیاز به تازه‌سازی اجباری نقشه از طریق `Ctrl + F5` دارد.

در اینجا هندلر برای فشار دادن دکمه ذخیره:
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

در اینجا یک کنترلر جدید، `FeaturesController` اضافه می‌کنیم که در آن هندلر برای استخراج خانه‌ها/ویژگی‌ها بر اساس مختصات ارسال شده ایجاد می‌شود.

درخواست SQL به شرح زیر است:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

مختصات به یک نقطه تبدیل می‌شوند، نشان دهنده سیستم مختصات درخواست اولیه مشتری (WGS 84) و سپس به سیستمی که داده‌های پایگاه داده در آن ارائه می‌شوند (Web Mercator) ترجمه می‌شوند. ما به دنبال تقاطع با این نقطه برای هندسه‌هایی هستیم که به‌عنوان ساختمان علامت‌گذاری شده‌اند.

اجرای درخواست و ارسال داده‌ها به مشتری مشابه آنچه قبلاً مورد بحث قرار گرفت:
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
با یک تفاوت کوچک: ما لایه InMemory خود را به‌عنوان GeoJSON در حافظه به صورت یک جریان ذخیره می‌کنیم، سپس آن را به یک رشته تبدیل کرده و به مشتری ارسال می‌کنیم.

اکنون به اصل به‌روزرسانی‌ها در Aspose.GIS می‌رسیم — ذخیره تغییرات در پایگاه داده. روش `Edit()` این کار را انجام می‌دهد. ما بدنه درخواست را برای بارگیری کامل آن در حافظه می‌خوانیم و آن را به‌عنوان یک جریان می‌خوانیم:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync(); 
Request.Body.Position = 0;
```
سپس ویژگی‌های ویرایش شده را در قالب GeoJSON می‌خوانیم:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
مرحله بعدی، از مجموعه ویژگی‌های ارسال شده، صفات نشان دهنده شناسه های منحصر به فرد ویژگی های مربوطه در پایگاه داده را استخراج می‌کنیم. ما یک درخواست برای پر کردن یک لایه ویژه برای ویرایش ایجاد می‌کنیم و منبع داده مربوطه را می‌سازیم:
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
نکته قابل توجه، روش پیکربندی `AsTrackableForChanges` است. این یک روش ویژه است که نشان می‌دهد نیاز به ایجاد منبع داده خاصی وجود دارد که قادر به ردیابی تغییرات باشد. پارامتر اول جدول را مشخص می‌کند که درخواست‌های تغییر باید به آن ارسال شوند. دومی نشان می‌دهد کدام صفت به‌عنوان شناسه برای ایجاد تغییرات در پایگاه داده در نظر گرفته شود. جالب‌ترین قسمت، پارامتر سوم است. هنگامی که روی True تنظیم می‌شود، نشان می‌دهد که لایه تکرارها را بر اساس پارامتر دوم ردیابی کرده و ویژگی‌های بارگذاری شده قبلی را با موارد جدید "بازنویسی" می‌کند. با این حال، در مورد نتایج ویرایش، یعنی افزودن یک ویژگی جدید با همان شناسه، دستور `UPDATE` بر اساس تغییرات نسبت به مقدار قدیمی تولید می‌شود. اگر تکرارها در هنگام مقداردهی اولیه لایه از پایگاه داده ظاهر شوند، لایه به‌طور خاموشانه آن‌ها را با آخرین مقدار بازنویسی می‌کند. اگر پارامتر سوم روی false تنظیم شود، هنگام بروز تکرارها، چه در هنگام مقداردهی اولیه یا ویرایش، یک استثنا ایجاد می‌شود.

نام صفات به‌عنوان نام فیلد در جدول قابل ویرایش استفاده می‌شوند. مهم است که یک نکته حیاتی در مورد تشخیص تغییرات را یادآوری کنیم. ضروری است که نوع داده دقیق صفت ذخیره شده در لایه برای ردیابی تغییرات مشخص شود، باید با انواع اضافه یا اصلاح شده جدید مطابقت داشته باشد. به عنوان مثال، اگر ویژگی جدیدی با `osm_id` از نوع `Int32` اضافه کنیم، در حالی که نوع صفت مشخص شده در لایه `Int64` است، این مورد به‌عنوان دو مقدار متفاوت در نظر گرفته می‌شود زیرا هیچ سرباری از روش `Equal`s وجود ندارد که شبیه به `Int64.Equals(Int32)` باشد. در نسخه‌های آینده، این رفتار بررسی و در صورت امکان اصلاح خواهد شد. نوع پارامتر سوم به‌عنوان نوع داده هدف جدول پایگاه داده هنگام ذخیره داده‌ها اعمال می‌شود.

سپس، ما به پایگاه داده متصل می‌شویم و داده‌ها را از جدول می‌خوانیم:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
یک نکته مهم این است که برای کار صحیح تراکنش در سطح پایگاه داده، لازم است تراکنش فعلی را به‌عنوان پارامتر دوم در هنگام عملیات خواندن ارسال کنید.

سپس، باید قبل از ارسال تغییرات به پایگاه داده، یک سری تبدیل‌ها انجام دهیم:
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
Leaflet هندسه‌ها را در سیستم مختصات WGS 84 تولید می‌کند، با این حال، طرح پایگاه داده نیاز به ذخیره سازی در Web Mercator دارد. برای تبدیل به سیستم Web Mercator، یک شیء `transformer` خاص ایجاد می‌کنیم و از آن برای تبدیل استفاده می‌کنیم.

علاوه بر این، leaflet پارامتر سوم مختصات هندسه Z را با مقدار 0 پر می‌کند. با این حال، این پارامتر در طرح پایگاه داده ما در نظر گرفته نمی‌شود، بنابراین حضور آن را با تنظیم مقدار `HasZ` به false حذف می‌کنیم.

نقطه نهایی اعمال تغییرات با جایگزینی ویژگی موجود با ویژگی دریافتی از مشتری است که شناسه یکسانی دارد. این عملیات منجر به تشخیص تغییرات نسبت به نمونه‌های قدیمی‌تر ویژگی می‌شود. در زمان فراخوانی `SubmitChangesAsync`، فرآیند تشخیص تغییرات رخ می‌دهد و دستورالعمل‌های INSERT، DELETE و UPDATE بر اساس تغییرات شما به پایگاه داده ارسال می‌شوند.

از اینکه تا انتها مطالعه کردید سپاسگزاریم. کل کد در مخزن زیر موجود خواهد بود: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)