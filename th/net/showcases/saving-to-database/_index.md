---
title: "การอัปเดต Aspose.GIS: การแก้ไขคุณสมบัติและรูปทรง และการบันทึกการเปลี่ยนแปลงไปยังฐานข้อมูล"
type: docs
url: /th/net/showcases/saving-changes-to-database/
description: "บทความนี้สำรวจการปรับปรุงล่าสุดในไลบรารี Aspose.GIS โดยเน้นที่ความสามารถใหม่ในการตรวจจับและบันทึกการเปลี่ยนแปลงรูปทรงและคุณสมบัติในแอปพลิเคชันแผนที่"
weight: 80
---
# การอัปเดต Aspose.GIS: การแก้ไขคุณสมบัติและรูปทรง และการบันทึกการเปลี่ยนแปลงไปยังฐานข้อมูล

## บทนำ

จากผลของการเปลี่ยนแปลงล่าสุดในไลบรารี [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis) สิ่งสำคัญคือต้องเน้นบางส่วนเพื่อให้ไม่ถูกมองข้าม ในบทความนี้ เราจะพูดถึงความสามารถใหม่ในการตรวจจับและบันทึกการเปลี่ยนแปลงรูปทรงและคุณสมบัติในฐานข้อมูล

เพื่อเป็นตัวอย่างสำหรับการสาธิต เราจะยังคงทำงานกับแอปพลิเคชันที่อธิบายไว้ในบทความ ["สร้างแผนที่ แผนที่เลื่อนพร้อมกระเบื้อง"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) และขยายเล็กน้อยโดยการเพิ่มฟังก์ชันการแก้ไขวัตถุบนแผนที่ ชุดข้อมูลยังคงเหมือนเดิมกับบทความก่อนหน้า

## ส่วนหน้า (Front-end)

สำหรับการสาธิตความสามารถในการปรับเปลี่ยนรูปทรง เราเลือกส่วนขยายโอเพนซอร์สยอดนิยมสำหรับ [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/)

เราเพิ่มไลบรารีนี้ผ่านไฟล์ libman.json:
![Libman](libman.png)

จากนั้น เราเชื่อมต่อรูปแบบและสคริปต์เข้ากับหน้าเว็บ:
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

เพื่อเป็นตัวอย่าง เราจะจำกัดความสามารถในการแก้ไขเฉพาะอาคารเท่านั้น เมื่อผู้ใช้คลิกปุ่มเมาส์ซ้ายบนแผนที่ หากมีอาคารในตำแหน่งนั้น อาคารจะถูกไฮไลต์และพร้อมสำหรับการแก้ไข นี่คือสิ่งที่ทำได้โดยการวางเลเยอร์เพิ่มเติมไว้ด้านบนกระเบื้อง

เมื่อผู้ใช้คลิกที่แผนที่ ไลบรารี Leaflet จะคำนวณพิกัดทางภูมิศาสตร์ของการคลิก เราส่งพิกัดเหล่านี้ไปยังส่วนหลัง และค้นหาฐานข้อมูลสำหรับรูปทรงที่ตัดกับจุดที่คลิก หากมีอาคารท่ามกลางรูปทรงเหล่านี้ เราจะคืนค่าพวกมัน

อาคารถูกส่งกลับจากส่วนหลังในรูปแบบ `GeoJSON` และเพิ่มลงในแผนที่เป็นเลเยอร์แยกสำหรับการแก้ไข นี่คือวิธีการจัดการการคลิก:
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

เรามีกลุ่มเลเยอร์ถาวรสำหรับรูปทรงที่แก้ไขได้ `featuresLayer` ซึ่งถูกเพิ่มลงในแผนที่ เราตรวจสอบว่าการคลิกเกิดขึ้นบนรูปทรงที่โหลดไว้แล้วหรือไม่ และหากไม่ใช่ เราจะส่งคำขอไปยังส่วนหลังเพื่อโหลดโพลีกอนที่เป็นตัวแทนของอาคาร เลเยอร์คุณสมบัติที่โหลดจะถูกเพิ่มลงใน featuresLayer และเปิดใช้งานโหมดแก้ไข

นี่คือลักษณะของฟังก์ชันสำหรับการโหลดคุณสมบัติและการแปลงจาก `GeoJSON`:
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

หลังจากเสร็จสิ้นการแก้ไข ผู้ใช้จะคลิกปุ่ม `Save` ที่กำหนดเอง:

![Save](save-btn.png)

รีเฟรชหน้าเว็บและดูการเปลี่ยนแปลง:

![Changes](changes.png)

น่าเสียดายที่ฟังก์ชัน `tiles.redraw()` ไม่ทำงานอย่างถูกต้องเนื่องจากกระเบื้องที่โหลดไว้ก่อนหน้านี้ถูกแคช ซึ่งจำเป็นต้องรีเฟรชแผนที่โดยบังคับผ่าน `Ctrl + F5`

นี่คือตัวจัดการสำหรับการกดปุ่มบันทึก:
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

## ส่วนหลัง (Back-end)

ที่นี่เราเพิ่มคอนโทรลเลอร์ใหม่ `FeaturesController` โดยที่เราสร้างตัวจัดการสำหรับการดึงบ้าน/คุณสมบัติตามพิกัดที่ส่งมา

คำขอ SQL มีลักษณะดังนี้:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

พิกัดจะถูกแปลงเป็นจุด ระบุระบบพิกัดของคำขอไคลเอนต์เดิม (WGS 84) จากนั้นจึงแปลเป็นระบบที่ข้อมูลฐานข้อมูลนำเสนอ (Web Mercator) เรามองหาการตัดกับจุดนี้สำหรับรูปทรงที่ทำเครื่องหมายว่าเป็นอาคาร

การดำเนินการตามคำขอและการส่งข้อมูลไปยังไคลเอนต์เกิดขึ้นในลักษณะเดียวกับที่เราได้กล่าวถึงในบทความก่อนหน้า:
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
ด้วยความแตกต่างเล็กน้อย: เราบันทึกเลเยอร์ InMemory ของเราเป็น GeoJSON ในหน่วยความจำในรูปแบบสตรีม จากนั้นแปลงเป็นสตริงและส่งไปยังไคลเอนต์

ตอนนี้เรามาถึงสาระสำคัญของการอัปเดตใน Aspose.GIS — การบันทึกการเปลี่ยนแปลงไปยังฐานข้อมูล วิธี `Edit()` จัดการสิ่งนี้ เราอ่านเนื้อหาคำขอเพื่อโหลดทั้งหมดลงในหน่วยความจำ และอ่านเป็นสตรีม:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync(); 
Request.Body.Position = 0;
```
จากนั้น เราอ่านคุณสมบัติที่แก้ไขในรูปแบบ GeoJSON:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
ขั้นตอนถัดไป จากชุดคุณสมบัติที่ส่งมา เราจะดึงแอตทริบิวต์ที่เป็นตัวแทนของตัวระบุที่ไม่ซ้ำกันสำหรับคุณสมบัติที่เกี่ยวข้องในฐานข้อมูล เราสร้างคำขอเพื่อเติมเลเยอร์พิเศษสำหรับการแก้ไขและสร้างแหล่งข้อมูลที่สอดคล้องกัน:
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
โปรดทราบวิธีการกำหนดค่า `AsTrackableForChanges` นี่คือวิธีพิเศษที่บ่งชี้ถึงความจำเป็นในการสร้างแหล่งข้อมูลเฉพาะที่สามารถติดตามการเปลี่ยนแปลงได้ พารามิเตอร์แรกระบุตารางที่จะส่งคำขอเปลี่ยนแปลงไปยัง พารามิเตอร์ที่สองระบุแอตทริบิวต์ที่จะถือว่าเป็นตัวระบุสำหรับการทำการเปลี่ยนแปลงในฐานข้อมูล ส่วนที่น่าสนใจที่สุดคือพารามิเตอร์ที่สาม เมื่อตั้งค่าเป็น True จะบ่งชี้ว่าเลเยอร์จะติดตามการปรากฏของรายการซ้ำตามพารามิเตอร์ที่สองและ "เขียนทับ" คุณสมบัติที่โหลดไว้ก่อนหน้านี้ด้วยคุณสมบัติใหม่ อย่างไรก็ตาม ในกรณีของการแก้ไขผลลัพธ์ เช่น การเพิ่มคุณสมบัติใหม่ที่มีตัวระบุเดียวกัน คำสั่ง `UPDATE` จะถูกสร้างขึ้นตามการเปลี่ยนแปลงเมื่อเทียบกับค่าเดิม หากพารามิเตอร์ที่สามตั้งค่าเป็น false ข้อยกเว้นจะถูกโยนเมื่อรายการซ้ำปรากฏขึ้น ไม่ว่าจะระหว่างการเริ่มต้นหรือการแก้ไข

ชื่อแอตทริบิวต์จะถูกใช้เป็นชื่อฟิลด์ในตารางที่สามารถแก้ไขได้ สิ่งสำคัญคือต้องทราบประเด็นสำคัญเกี่ยวกับการตรวจจับการเปลี่ยนแปลง จำเป็นอย่างยิ่งที่จะต้องระบุประเภทข้อมูลที่แน่นอนของแอตทริบิวต์ที่จะเก็บไว้ในเลเยอร์สำหรับการติดตามการเปลี่ยนแปลง ต้องมีความแม่นยำเกี่ยวกับชนิดที่เพิ่มหรือปรับเปลี่ยนใหม่ ตัวอย่างเช่น หากเราเพิ่มคุณสมบัติใหม่ที่มี `osm_id` เป็นชนิด `Int32` ในขณะที่ชนิดแอตทริบิวต์ที่ระบุในเลเยอร์คือ `Int64` สิ่งนี้จะถูกมองว่าเป็นสองค่าที่แตกต่างกันเนื่องจากไม่มีการโอเวอร์โหลดของวิธีการ `Equal`s ที่ดูเหมือน `Int64.Equals(Int32)` ในเวอร์ชันอนาคต พฤติกรรมนี้จะได้รับการตรวจสอบและแก้ไขหากเป็นไปได้ ชนิดพารามิเตอร์ที่สามจะถูกนำไปใช้ในระหว่างการบันทึกข้อมูลเป็นชนิดข้อมูลเป้าหมายของตารางฐานข้อมูล

จากนั้น เราเชื่อมต่อกับฐานข้อมูลและอ่านข้อมูลจากตาราง:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
ประเด็นสำคัญคือเพื่อให้การทำธุรกรรมทำงานอย่างถูกต้องในระดับฐานข้อมูล จำเป็นต้องส่งธุรกรรมปัจจุบันเป็นพารามิเตอร์ที่สองระหว่างการดำเนินการอ่าน

จากนั้น เราต้องทำการเปลี่ยนแปลงหลายครั้งก่อนที่จะส่งการเปลี่ยนแปลงไปยังฐานข้อมูล:
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
Leaflet สร้างรูปทรงในระบบพิกัด WGS 84 อย่างไรก็ตาม สคีมาฐานข้อมูลต้องการการจัดเก็บใน Web Mercator เพื่อแปลงเป็นระบบ Web Mercator เราสร้างออบเจ็กต์ `transformer` พิเศษและใช้เพื่อทำการแปลง

นอกจากนี้ Leaflet จะเติมพารามิเตอร์ที่สามของพิกัดรูปทรง Z ด้วยค่า 0 อย่างไรก็ตาม พารามิเตอร์นี้ไม่ได้คำนึงถึงในสคีมาฐานข้อมูลของเรา ดังนั้นเราจึงลบการปรากฏตัวโดยตั้งค่าค่า `HasZ` เป็นเท็จ

จุดสุดท้ายคือการใช้การเปลี่ยนแปลงโดยการแทนที่คุณสมบัติที่มีอยู่ด้วยคุณสมบัติที่ได้รับจากไคลเอนต์ที่มี `osm_id` เดียวกัน การดำเนินการนี้จะนำไปสู่การตรวจจับการเปลี่ยนแปลงเมื่อเทียบกับอินสแตนซ์เก่าของฟีเจอร์ ในช่วงเวลาของการเรียก `SubmitChangesAsync` กระบวนการตรวจจับการเปลี่ยนแปลงจะเกิดขึ้น และคำสั่ง INSERT, DELETE และ UPDATE จะถูกส่งไปยังฐานข้อมูลตามการเปลี่ยนแปลงของคุณ

ขอขอบคุณที่อ่านจนจบ โค้ดทั้งหมดจะมีอยู่ในที่เก็บต่อไปนี้: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)