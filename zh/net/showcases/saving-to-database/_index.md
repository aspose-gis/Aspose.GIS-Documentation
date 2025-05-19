---
title: "Aspose.GIS 更新：编辑要素和几何体并将更改保存到数据库。"
type: docs
url: /zh/net/showcases/saving-changes-to-database/
description: “本文探讨了 Aspose.GIS 库的最新增强功能，重点是检测和保存映射应用程序中几何体和要素更改的新能力。”
weight: 80
---
# Aspose.GIS 更新：编辑要素和几何体并将更改保存到数据库。

## 简介

鉴于 Aspose.GIS ([https://www.nuget.org/packages/Aspose.gis](https://www.nuget.org/packages/Aspose.gis)) 库的最新变化，重要的是突出其中一些内容，以免被忽视。 在本文中，我们将讨论检测和保存数据库中几何体和要素更改的新能力。

作为演示示例，我们将继续使用在 ["绘制地图。带有切片的滑动地图"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) 一文中描述的应用程序，并通过添加地图上的对象编辑功能来略微扩展它。 数据集与上一篇文章中的数据集相同。

## 前端

为了演示几何体修改能力，我们选择了一个流行的开源 [leaflet](https://leafletjs.com/) 扩展 — [leaflet-geoman](https://geoman.io/)。

我们通过 libman.json 文件添加此库：
![Libman](libman.png)

接下来，我们将样式和脚本连接到页面：
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

为了演示的目的，我们将编辑能力限制为仅建筑物。 用户单击地图上的左键，如果该位置有建筑物，则会突出显示并可供编辑。 这是通过在切片之上覆盖额外的图层来实现的。

当用户点击地图时，Leaflet 库会计算点击的空间坐标。 我们将这些坐标发送到后端并在数据库中搜索与点击点相交的几何体。 如果这些几何体中有建筑物，我们将返回它们。

从后端返回的建筑物采用 `GeoJSON` 格式，并作为单独的可编辑图层添加到地图上。 以下是我们处理点击的方式：
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

我们有一个用于可编辑几何体的持久图层组 `featuresLayer`，它已添加到地图中。 我们检查点击是否是在已经加载的几何体上进行的，如果不是，则向后端发出请求以加载代表建筑物的多边形。 加载的功能图层被添加到 featuresLayer 中，并激活了编辑模式。

以下是加载功能和从 `GeoJSON` 转换的功能：
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

在编辑会话之后，用户点击自定义的 `Save` 按钮：

![Save](save-btn.png)

刷新页面并查看更改：

![Changes](changes.png)

不幸的是，`tiles.redraw()` 函数无法正常工作，因为先前加载的切片已被缓存，需要通过 `Ctrl + F5` 进行强制刷新地图。

这是处理保存按钮的处理程序：
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

## 后端

在这里，我们添加了一个新的控制器 `FeaturesController`，其中我们创建一个处理程序来根据发送的坐标提取房屋/要素。

SQL 请求如下：

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

坐标被转换为一个点，指示原始客户端请求的坐标系（WGS 84），然后翻译成数据库数据呈现的系统（Web Mercator）。 我们查找与该点相交的标记为建筑物的几何体。

请求的执行和将数据发送到客户端类似于我们之前讨论的内容：
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
与一个小小的区别：我们将 InMemory 图层作为 GeoJSON 存储在内存中作为一个流，然后将其转换为字符串并发送到客户端。

现在我们来到了 Aspose.GIS 更新的本质 — 将更改保存到数据库。 `Edit()` 方法处理此操作。 我们读取请求体以完全将其加载到内存中并将其读取为流：
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync();
Request.Body.Position = 0;
```
接下来，我们以 GeoJSON 格式读取编辑的功能：
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
下一步，从发送的特征集中，我们提取代表数据库中相应特征的唯一标识符的属性。 我们形成一个请求以填充用于编辑的特殊图层并构建相应的DataSource：
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
请注意配置方法 `AsTrackableForChanges`。 这是一个特殊的方法，指示需要创建能够跟踪更改的特定DataSource。 第一个参数指定应发送更改请求到哪个表。 第二个指示将哪个属性视为数据库中进行更改的标识符。 最有趣的部分是第三个参数。 当设置为 True 时，它表示该图层将根据第二个参数跟踪重复项的出现并用新的覆盖以前加载的功能。 但是，在编辑结果的情况下，即添加具有相同标识符的新功能，将生成一个根据与旧值相比的变化进行的 `UPDATE` 命令。 如果在初始化图层时出现重复项，则该图层会静默地用最后一个值覆盖它们。 如果第三个参数设置为 false，则无论是在初始化期间还是编辑过程中出现重复项，都会抛出异常。

属性名称将用作可编辑表中字段的名称。 重要的是要注意关于更改检测的一个关键点。 指定将在图层中存储以跟踪更改的属性的确切数据类型至关重要，它必须准确地对应于新添加或修改的类型。 例如，如果我们添加一个具有 `osm_id` 类型为 `Int32` 的新功能，而图层中指定的属性类型是 `Int64`，这将视为两个不同的值，因为没有查找类似于 `Int64.Equals(Int32)` 的 `Equal`s 方法的重载。 在未来的版本中，将审查并更正此行为（如果可能）。 第三参数类型将在数据保存时作为数据库表的的目标数据类型应用。

接下来，我们连接到数据库并从表中读取数据：
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
一个重要的点是，为了使数据库级别的事务正确工作，必须将当前的事务作为第二个参数传递到读取操作中。

接下来，我们需要在将更改发送到数据库之前执行一系列转换：
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
Leaflet 生成 Web Mercator 坐标系中的几何体，但是数据库模式需要以 Web Mercator 存储。 为了转换为 Web Mercator 系统，我们创建一个特殊的 `transformer` 对象并将其用于转换。

此外，leaflet 将几何体的第三个参数 Z 用值为 0 填充。 但是，此参数未在我们的数据库模式中考虑，因此我们通过将 `HasZ` 的值设置为 false 来删除其存在。

最终的点是通过用从客户端接收到的具有相同 osm_id 的功能替换现有功能来应用更改。 此操作将导致检测相对于旧实例的更改。 在调用 `SubmitChangesAsync` 时，将发生更改检测过程，并且根据您的更改，将向数据库发送 INSERT、DELETE 和 UPDATE 命令。

感谢您阅读到最后。 整个代码将在以下存储库中提供：[Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)
---