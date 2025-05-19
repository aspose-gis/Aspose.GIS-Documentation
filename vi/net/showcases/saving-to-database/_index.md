---
title: "Cập nhật Aspose.GIS: Chỉnh sửa các đối tượng và hình học và lưu thay đổi vào cơ sở dữ liệu."
type: docs
url: /vi/net/showcases/saving-changes-to-database/
description: "Bài viết này khám phá những cải tiến gần đây trong thư viện Aspose.GIS, tập trung vào khả năng mới để phát hiện và lưu các thay đổi hình học trong một ứng dụng bản đồ."
weight: 80
---
# Cập nhật Aspose.GIS: Chỉnh sửa các đối tượng và hình học và lưu thay đổi vào cơ sở dữ liệu.

## Giới thiệu

Trước những thay đổi gần đây trong thư viện [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis), điều quan trọng là phải làm nổi bật một số thay đổi đó để chúng không bị bỏ qua. Trong bài viết này, chúng ta sẽ thảo luận về khả năng mới để phát hiện và lưu các thay đổi đối với hình học và các đối tượng trong cơ sở dữ liệu.

Ví dụ để minh họa, chúng ta sẽ tiếp tục làm việc trên ứng dụng được mô tả trong bài ["Vẽ bản đồ. Bản đồ trượt có ô"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) và mở rộng nó một chút bằng cách thêm chức năng chỉnh sửa đối tượng trên bản đồ. Tập dữ liệu vẫn giữ nguyên như trong bài viết trước.

## Giao diện người dùng

Để chứng minh khả năng sửa đổi hình học, chúng tôi đã chọn một tiện ích mở rộng nguồn mở phổ biến cho [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/).

Chúng ta thêm thư viện này thông qua tệp libman.json:
![Libman](libman.png)

Tiếp theo, chúng ta kết nối các kiểu và tập lệnh với trang:
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

Để minh họa, chúng ta sẽ giới hạn khả năng chỉnh sửa chỉ cho các tòa nhà. Người dùng nhấp vào nút chuột trái trên bản đồ và nếu có một tòa nhà tại vị trí đó, nó sẽ được làm nổi bật và có thể chỉnh sửa. Điều này đạt được bằng cách phủ thêm một lớp bổ sung lên trên các ô.

Khi người dùng nhấp vào bản đồ, thư viện Leaflet tính toán tọa độ địa lý của lần nhấp. Chúng ta gửi những tọa độ này đến backend và tìm kiếm cơ sở dữ liệu để tìm các hình học giao với điểm đã nhấp. Nếu có tòa nhà trong số những hình học đó, chúng ta sẽ trả về chúng.

Các tòa nhà được trả về từ backend ở định dạng `GeoJSON` và được thêm vào bản đồ dưới dạng một lớp riêng biệt để chỉnh sửa. Đây là cách chúng ta xử lý lần nhấp:
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

Chúng ta có một nhóm lớp cố định cho các hình học có thể chỉnh sửa, `featuresLayer`, đã được thêm vào bản đồ. Chúng ta kiểm tra xem lần nhấp có được thực hiện trên một hình học đã tải hay không và nếu không, chúng ta sẽ gửi yêu cầu đến backend để tải các đa giác đại diện cho các tòa nhà. Các lớp tính năng đã tải được thêm vào featuresLayer và chế độ chỉnh sửa được kích hoạt.

Đây là cách hàm tải các tính năng và chuyển đổi từ `GeoJSON` trông như thế này:
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

Sau phiên chỉnh sửa, người dùng nhấp vào nút `Lưu` tùy chỉnh:

![Save](save-btn.png)

Làm mới trang và xem các thay đổi:

![Changes](changes.png)

Thật không may, hàm `tiles.redraw()` không hoạt động chính xác vì các ô đã tải trước được lưu trong bộ nhớ cache, yêu cầu làm mới bản đồ bằng cách buộc `Ctrl + F5`.

Đây là trình xử lý cho việc nhấn nút lưu:
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

## Backend

Ở đây, chúng ta thêm một bộ điều khiển mới, `FeaturesController`, nơi chúng ta tạo một trình xử lý để trích xuất nhà/tính năng theo tọa độ được gửi.

Yêu cầu SQL trông như sau:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

Các tọa độ được chuyển đổi thành một điểm, chỉ ra hệ thống tọa độ của yêu cầu khách ban đầu (WGS 84) và sau đó được dịch sang hệ thống mà dữ liệu cơ sở dữ liệu được trình bày (Web Mercator). Chúng ta tìm kiếm các giao với điểm này cho các hình học được đánh dấu là tòa nhà.

Việc thực thi yêu cầu và gửi dữ liệu đến máy khách diễn ra tương tự như những gì chúng ta đã thảo luận trong bài viết trước:
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
Với một sự khác biệt nhỏ: chúng ta lưu lớp InMemory của mình dưới dạng GeoJSON trong bộ nhớ dưới dạng luồng, sau đó chuyển đổi nó thành chuỗi và gửi nó đến máy khách.

Bây giờ chúng ta đến với bản chất của các bản cập nhật trong Aspose.GIS — lưu thay đổi vào cơ sở dữ liệu. Phương thức `Edit()` xử lý điều này. Chúng ta đọc thân yêu cầu để tải hoàn toàn nó vào bộ nhớ và đọc nó dưới dạng luồng:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync();
Request.Body.Position = 0;
```
Tiếp theo, chúng ta đọc các tính năng đã chỉnh sửa ở định dạng GeoJSON:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
Bước tiếp theo, từ tập hợp các tính năng được gửi, chúng ta trích xuất các thuộc tính đại diện cho các định danh duy nhất của các tính năng tương ứng trong cơ sở dữ liệu. Chúng ta tạo một yêu cầu để điền vào một lớp đặc biệt để chỉnh sửa và xây dựng nguồn dữ liệu tương ứng:
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
Lưu ý phương thức cấu hình `AsTrackableForChanges`. Đây là một phương pháp đặc biệt chỉ ra sự cần thiết phải tạo một nguồn dữ liệu cụ thể có khả năng theo dõi các thay đổi. Tham số đầu tiên chỉ định bảng mà yêu cầu thay đổi nên được gửi đến. Cái thứ hai cho biết thuộc tính nào sẽ được coi là định danh để thực hiện thay đổi đối với cơ sở dữ liệu. Phần thú vị nhất là tham số thứ ba. Khi đặt thành True, nó chỉ ra rằng lớp sẽ theo dõi sự xuất hiện của các bản sao theo tham số thứ hai và "ghi đè" các tính năng đã tải trước đó bằng những tính năng mới. Tuy nhiên, trong trường hợp chỉnh sửa kết quả, tức là thêm một tính năng mới với cùng định danh, lệnh `UPDATE` sẽ được tạo ra theo các thay đổi so với giá trị cũ. Nếu các bản sao xuất hiện trong quá trình khởi tạo lớp từ cơ sở dữ liệu, lớp sẽ lặng lẽ ghi đè chúng bằng giá trị cuối cùng. Nếu tham số thứ ba được đặt thành false, một ngoại lệ sẽ được đưa ra khi các bản sao xuất hiện, cho dù trong quá trình khởi tạo hay chỉnh sửa.

Tên thuộc tính sẽ được sử dụng làm tên trường trong bảng có thể chỉnh sửa. Điều quan trọng cần lưu ý là một điểm quan trọng liên quan đến việc phát hiện thay đổi. Điều cần thiết là phải chỉ định chính xác loại dữ liệu của thuộc tính sẽ được lưu trữ trong lớp để theo dõi các thay đổi, nó phải chính xác liên quan đến các loại mới thêm hoặc đã sửa đổi. Ví dụ: nếu chúng ta thêm một tính năng mới với `osm_id` có kiểu `Int32`, trong khi loại thuộc tính được chỉ định trong lớp là `Int64`, điều này sẽ được coi là hai giá trị khác nhau vì không có quá tải của phương thức `Equal`s trông giống như `Int64.Equals(Int32)`. Trong các phiên bản sau, hành vi này sẽ được xem xét và sửa chữa nếu có thể. Loại tham số thứ ba sẽ được áp dụng trong quá trình lưu dữ liệu dưới dạng loại dữ liệu mục tiêu của bảng cơ sở dữ liệu.

Tiếp theo, chúng ta kết nối với cơ sở dữ liệu và đọc dữ liệu từ bảng:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
Một điểm quan trọng là để giao dịch hoạt động chính xác ở cấp độ cơ sở dữ liệu, điều cần thiết là phải truyền giao dịch hiện tại làm tham số thứ hai trong quá trình đọc.

Tiếp theo, chúng ta cần thực hiện một loạt các phép biến đổi trước khi gửi các thay đổi đến cơ sở dữ liệu:
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
Leaflet tạo hình học trong hệ thống tọa độ WGS 84, tuy nhiên, lược đồ cơ sở dữ liệu yêu cầu lưu trữ trong Web Mercator. Để chuyển đổi sang hệ thống Web Mercator, chúng ta tạo một đối tượng `transformer` đặc biệt và sử dụng nó cho quá trình chuyển đổi.

Ngoài ra, leaflet điền tham số thứ ba của tọa độ hình học Z bằng giá trị 0. Tuy nhiên, tham số này không được tính đến trong lược đồ cơ sở dữ liệu của chúng tôi, vì vậy chúng ta loại bỏ sự hiện diện của nó bằng cách đặt giá trị `HasZ` thành false.

Điểm cuối cùng là áp dụng các thay đổi bằng cách thay thế tính năng hiện có bằng tính năng nhận được từ máy khách có cùng osm_id. Hoạt động này sẽ dẫn đến việc phát hiện các thay đổi so với các phiên bản cũ hơn của tính năng. Tại thời điểm gọi `SubmitChangesAsync`, quá trình phát hiện thay đổi sẽ xảy ra và các lệnh INSERT, DELETE và UPDATE sẽ được gửi đến cơ sở dữ liệu theo các thay đổi của bạn.

Cảm ơn bạn đã đọc đến cuối bài viết. Toàn bộ mã sẽ có sẵn trong kho lưu trữ sau: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)
---