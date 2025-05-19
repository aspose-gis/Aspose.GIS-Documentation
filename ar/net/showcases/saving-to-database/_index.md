---
title: "تحديثات Aspose.GIS: تحرير المعالم والهندسات وحفظ التغييرات في قاعدة البيانات."
type: docs
url: /ar/net/showcases/saving-changes-to-database/
description: "تتناول هذه المقالة التحسينات الأخيرة في مكتبة Aspose.GIS مع التركيز على القدرات الجديدة لاكتشاف التغييرات الهندسية وحفظها في تطبيق الخريطة."
weight: 80
---
# تحديثات Aspose.GIS: تحرير المعالم والهندسات وحفظ التغييرات في قاعدة البيانات.

## مقدمة

نظرًا للتغييرات الأخيرة في [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis) ، من المهم تسليط الضوء على بعضها حتى لا تمر مرور الكرام. في هذه المقالة، سنناقش القدرة الجديدة على اكتشاف وحفظ التغييرات في الهندسات والمعالم في قاعدة البيانات.

كمثال للتوضيح، سنستمر في العمل على التطبيق الموجود في المقالة ["رسم الخريطة. خريطة متحركة مع البلاط"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) ونوسعه قليلاً من خلال إضافة وظائف تحرير الكائنات على الخريطة. يظل مجموع البيانات هو نفسه الذي تمت مناقشته في المقالة السابقة.

## الواجهة الأمامية

لتوضيح قدرات تعديل الهندسة، اخترنا ملحقًا مفتوح المصدر شهيرًا لـ [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/).

نضيف هذه المكتبة عبر ملف libman.json:
![Libman](libman.png)

بعد ذلك، نوصل الأنماط والنصوص إلى الصفحة:
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

لأغراض التوضيح، سنقيد قدرات التحرير للمباني فقط. ينقر المستخدم بزر الماوس الأيسر على الخريطة، وإذا كانت هناك مبنى في تلك الموقع، يتم تحديده ويصبح متاحًا للتحرير. يتم ذلك عن طريق تغطية طبقة إضافية أعلى البلاط.

عندما ينقر المستخدم على الخريطة، تحسب مكتبة Leaflet الإحداثيات الجغرافية للنقرة. ثم نرسل هذه الإحداثيات إلى الخلفية ونبحث في قاعدة البيانات عن الهندسات التي تتلاقى مع النقطة المنقرة. إذا كانت هناك مبانٍ ضمن هذه الهندسات، فإننا نعود بها.

تُرجع المباني من الخلفية بتنسيق `GeoJSON` وتُضاف إلى الخريطة كطبقة منفصلة للتحرير. إليك كيف نتعامل مع النقرة:
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

يوجد لدينا مجموعة الطبقات المستمرة للهندسات القابلة للتحرير، `featuresLayer`، التي تمت إضافتها إلى الخريطة. نتحقق مما إذا كان النقر تم على هندسة محملة بالفعل، وإذا لم يكن كذلك، نقوم باستدعاء الخلفية لتحميل المضلعات التي تمثل المباني. تتم إضافة الطبقات المحملة إلى `featuresLayer`، وتُفعّل وضع التحرير.

ها هي الدالة التي تبدو عملية تحميل المعالم والتحويل من `GeoJSON`:
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

بعد جلسة التحرير، يقوم المستخدم بالنقر فوق زر `حفظ` المخصص:

![حفظ](save-btn.png)

قم بتحديث الصفحة وانظر التغييرات:

![تغييرات](changes.png)

لسوء الحظ، دالة `tiles.redraw()` لا تعمل بشكل صحيح حيث يتم تخزين البلاطات المحملة سابقًا، مما يتطلب تحديثًا قسريًا للخريطة عبر `Ctrl + F5`.

وها هو المعالج لضغط زر الحفظ:
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

## الخلفية

هنا نضيف وحدة تحكم جديدة، `FeaturesController`، حيث نقوم بإنشاء معالج لاستخراج منازل/معالم وفقًا للإحداثيات المرسلة.

تظهر الاستعلام SQL على النحو التالي:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

تتم تحويل الإحداثيات إلى نقطة، تشير إلى نظام الإحداثيات لطلب العميل الأصلي (WGS 84)، ثم تترجم إلى النظام الذي تُقدم به البيانات في قاعدة البيانات (Web Mercator). نبحث عن التقاطع مع هذه النقطة للهندسات المعروضة باعتبارها مبانٍ.

تتم عملية تنفيذ الاستعلام وإرسال البيانات إلى العميل بالطريقة نفسها التي تم مناقشتها في المقالة السابقة:
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

بفارق بسيط: نحفظ طبقة InMemory لدينا باعتبارها GeoJSON في الذاكرة كجريان، ثم نحولها إلى سلسلة ونرسلها إلى العميل.

الآن نأتي إلى جوهر تحديثات Aspose.GIS — حفظ التغييرات في قاعدة البيانات. تتعامل الطريقة `Edit()` مع هذا. نقوم بقراءة جسم الطلب لتحميله بالكامل في الذاكرة وقراءته كجريان:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync(); 
Request.Body.Position = 0;
```

ثم، نقوم بقراءة المعالم المحررة بتنسيق GeoJSON:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```

الخطوة التالية، من المجموعة المرسلة من المعالم، نستخرج السمات التي تمثل المعرفات الفريدة للمعالم المقابلة في قاعدة البيانات. نشكل طلبًا لملء طبقة خاصة للتحرير ونشكل مصدر البيانات المقابل:
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

لاحظ الطريقة التكوينية `AsTrackableForChanges`. هذه هي طريقة خاصة تشير إلى ضرورة إنشاء مصدر بيانات محدد قادر على تتبع التغييرات. يحدد المعامل الأول الجدول الذي يجب إرسال طلبات التغيير إليه. يشير المعامل الثاني إلى السمة التي سيتم اعتبارها المعرف لإجراء التغييرات على قاعدة البيانات. الجزء الأكثر إثارة للاهتمام هو المعامل الثالث. عند تعيينه إلى True، يشير إلى أن الطبقة ستتتبع ظهور النسخ المكررة وفقًا للمعرف الثاني و"سيُطلق" الهندسات المحملة سابقًا بالجديدة. ومع ذلك، في حالة نتائج التحرير، أي إضافة ميزة جديدة بنفس المعرف، سيتم إنشاء أمر `UPDATE` وفقًا للتغييرات مقارنة بالقيمة القديمة. إذا ظهرت نسخ مكررة أثناء تهيئة الطبقة من قاعدة البيانات، سيقوم الطبقة بمسحها بصمت باستبدالها بالقيمة الأخيرة. إذا تم تعيين المعامل الثالث إلى false، فسيتم رمي استثناء عند ظهور النسخ المكررة، سواء أثناء التهيئة أو التحرير. 

سيتم استخدام أسماء السمات كأسماء حقول في الجدول القابل للتحرير. من المهم أن نلاحظ نقطة حاسمة بخصوص اكتشاف التغييرات. من الضروري تحديد نوع البيانات الدقيق للسمة التي سيتم تخزينها في الطبقة لتتبع التغييرات، يجب أن يكون دقيقًا فيما يتعلق بأنواع البيانات المضافة حديثًا أو المعدلة. على سبيل المثال، إذا أضفنا ميزة جديدة بـ `osm_id` من نوع `Int32`، بينما كان نوع السمة المحدد في الطبقة هو `Int64`، سيُعامل ذلك على أنه قيمتان مختلفتان لأن