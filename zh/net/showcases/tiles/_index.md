---
title: "绘制地图。带有图块的滑动地图。"
type: docs
url: /zh/net/showcases/sliding-map-with-tiles/
description: "如何绘制图块并从中构建滑动地图。"
weight: 80
aliases:
 - /zh/net/showcases/tiles/
---
# 绘制地图。带有图块的滑动地图。
在本文中，我们想展示如何使用 [Aspose.GIS](https://www.nuget.org/packages/Aspose.GIS/) 库和公共数据构建一个滑动地图，该地图将在实时生成。得益于库的新功能，我们可以现在通过 SQL 查询从数据库查询 GIS 数据。以下是我们应该得到的结果：

![结果](result.png)

仓库源代码 [这里](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)。

## 数据准备。

首先，我们需要可以加载到数据库中的地理空间信息。`OpenStreetMap` 是此类信息的流行来源之一，所以让我们使用它。我认为最方便的方法是从公共资源 https://download.geofabrik.de/ 下载 pbf 格式的数据。例如，我们下载 [匈牙利](https://download.geofabrik.de/europe/hungary-latest.osm.pbf)。

在下一阶段，我们需要一个正在运行的 `PostGIS` 实例。当然，您可以使用本地安装的 `PostgreSQL` 版本，但我发现使用 Docker 容器非常方便。让我们使用 docker compose 文件安装 PostGIS：

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

`d:\local_folder:/usr/share/gisdata` 卷需要从本地机器加载 GIS 数据。

接下来，让我们运行我们的容器：

```bash
docker compose up
```

使用 `pgAdmin` 连接到数据库实例并在那里创建匈牙利数据库：

![创建 DB](create_db.png)

或者通过 SQL 命令：

```sql
CREATE DATABASE Hungary;
```

将必要的扩展添加到此数据库：

![Extentions](add_extention.png)

这些将是 `postgis` 和 `hstore` 扩展。hstore 是一个允许您使用键值数据类型的扩展。OpenStreetMap 广泛使用这种类型来描述不属于主要类别中的属性，因此不会为它们创建单独的字段，而是存储在 tags 字段中。

还有一个 SQL-like 的命令版本：

```sql
CREATE EXTENSION IF NOT EXISTS hstore;
CREATE EXTENSION IF NOT EXISTS postgis;
```

现在让我们连接到容器，以我的例子来说是 `local_folder-postgis-1`：

```bash
docker exec -it local_folder-postgis-1 sh
```

并安装将从 `pbf` 文件导入数据的程序：

```bash
apt-get update && apt-get install -y osm2pgsql
```

确保 `hungary-latest.osm.pbf` 文件位于您的 `local_folder` 文件夹中，然后运行导入命令：

```bash
osm2pgsql --create --database=Hungary --user=gis --password --host=localhost --port=5432 --hstore /usr/share/gisdata/hungary-latest.osm.pbf
```

对于匈牙利来说，完成此命令花费了我一分半钟。`--create` 选项意味着新数据库的简单创建模式。顺便说一下，除此之外，还有 `--append` 模式，它允许在数据发生更改时更新它们：

```bash
osm2pgsql --append --slim OSMFILE
```

`--hstore` 选项告诉应用程序额外创建一个 `tags` 字段的 hstore 类型来存储有关特征和几何图形的其他信息。

## 后端

所以，我们的数据已经准备好使用了。创建地图的下一步是创建后端。我们后端的目的是从数据库中生成特殊的 `tiles`，通常大小为 `256*256`，浏览器将像马赛克一样从它们组装成地图。每个图块都由 Z（地图放大/缩小程度）、X（图块数组中的行）和 Y（列）等参数的组合唯一标识。您可以[在这里](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames) 了解有关图块性质的更多信息。

我们的后端将是 ASP.NET Core，所以让我们开始创建项目。因此，让我们基于预安装的 `ASP.NET Core MVC` 模板在 `Visual Studio` 中创建一个项目。

接下来，将 NuGet 包 `Aspose.GIS` 安装到将生成图块的项目中：

```cmd
dotnet add package Aspose.GIS --version 24.6.0
```

清理项目中不必要的文件。这样结构看起来大致如下：

![解决方案资源管理器](project.png)

然后删除 wwwroot/lib 文件夹中的内容，因为我们将通过 `libman` 安装我们的依赖项。以下是 libman.json 文件的结构：
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


将客户端依赖项添加到 `_Layout.cshtml` 文件：

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

并编辑 `Index.cshtml`：

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

在这种情况下，`bootstrap-reboot.min.css` 重置了默认样式设置，而 `leaflet.min.js` 负责渲染地图，即从图块组装成地图。让我们在 `map.css` 文件中将地图块的高度设置为可见区域的完整高度：

```css
#map {
    min-height: 100vh;
}
```

`map.js` 文件的内容也相当简单，但更令人感兴趣：

```javascript
var map = L.map('map').setView([47.59995, 19.36623], 13);
const tiles = L.tileLayer('/tiles/{z}/{x}/{y}.png', {
    maxZoom: 19,
    minZoom: 11
}).addTo(map);
```

在这里，我们使用 leaflet 库的 API，其中指定了地图块的 ID `'map'`，然后在 `setView` 方法中设置初始地图加载开始位置的坐标以及比例尺，例如 13。请注意 `tileLayer` 方法，它接受服务器请求图块的模式字符串。此地址可以是绝对的以访问第三方图块服务器，也可以是相对的，如我们在此例中所做的那样。路由 `'/tiles/{z}/{x}/{y}.png'` 尚未由我们实现，这是我们的叙述中最重要的一部分，我们还没有实现它。

为了实现生成图块的请求处理程序，让我们首先在 `Program.cs` 文件中定义一个单独的路由：

```csharp
app.MapControllerRoute(name: "tiles",
  pattern: "tiles/{z}/{x}/{y}.png",
  defaults: new { controller = "Tiles", action = "Index" });

app.MapControllerRoute(
  name: "default",
  pattern: "{controller=Home}/{action=Index}/{id?}");
```

在这里，定义了两个路由，第一个是图块的路由，第二个是标准路由。在 `MapControllerRoute` 的情况下，顺序很重要，为了避免意外行为，值得将图块路由放在标准路由之前。

接下来，让我们转到处理程序本身。创建 `TilesController.cs` 控制器。它将具有以下类型的单个操作：

```csharp
public async Task<ActionResult> Index(int z, int x, int y)
```

现在我们拥有所有必要的数据来计算图块对应的坐标系中覆盖的边界框。在当前的实现中，我们的数据库中的数据存储在 Web Mercator 坐标系中。OpenStreetMap 默认提供这种坐标系统的数据。Web Mercator 是 `projection`(坐标系形式)，最常用于各种流行的服务中的映射，因为它涵盖了几乎整个地球，并且距离以米为单位测量，这简化了计算，与例如 `WGS 84` 不同，其中距离以角度测量，使计算更加复杂。所以，好吧，现在让我们定义“世界的一半”常量，它需要用于计算图块坐标：

```csharp
private const double _halfOfWorld = 20037508.34;
```

坐标的计算如下：

```csharp
double worldSize = _halfOfWorld * 2;
double tileSize = worldSize / Math.Pow(2, z);

double min_x = x * tileSize - _halfOfWorld;
double max_x = (x + 1) * tileSize - _halfOfWorld;
double min_y = _halfOfWorld - (y + 1) * tileSize;
double max_y = _halfOfWorld - y * tileSize;

min_x = Math.Round(min_x, 6);
max_x = Math.Round(max_x, 6);
min_y = Math.Round(min_y, 6);
max_y = Math.Round(max_y, 6);
```

在 Web Mercator 坐标系中，Y 轴是倒置的。因此，我们需要交换 min_y 和 max_y 的值：

```csharp
double temp = min_y;
min_y = max_y;
max_y = temp;
```

一个非常重要的点是，在当前数据库集成阶段，该库可以读取 `WKB` 格式的几何图形，但最好使用 `EWKB`，即扩展已知二进制格式，那么就不需要将空间坐标系信息作为单独字段传递了，因为它已经嵌入到几何信息中。为了这些目的，我们使用 `ST_AsEWKB` 函数。

我们预先计算通过 `ST_MakeEnvelope` 函数的图块边界框，该函数将在所有联接查询中使用并存储在 `envelope` 变量中。

我们指定传递的坐标对应于 3857 坐标系（Web Mercator）。

在 `WHERE` 表达式中，我们使用 `ST_Intersects` 函数指定我们想要检索与包围框区域相交的表中所有几何图形。

> [!WARNING]
> 一个非常重要的点是，在当前阶段的数据库集成中，该库可以读取 `WKB` 格式的几何图形，但最好使用 `EWKB`，即扩展已知二进制格式，那么就不需要将空间坐标系信息作为单独字段传递了，因为它已经嵌入到几何信息中。为了这些目的，我们使用 `ST_AsEWKB` 函数。

`ST_ClipByBox2D` 函数用于剪除超出边界框范围的几何图形。

现在是关键时刻，如何执行查询并获得包含一组特征的图层，该特征将在图块上渲染。这很简单：

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

我们收到一个图层，其中包含与我们的图块相交的所有几何图形。

好的，现在我们可以稍微给地图上色，比如城市、水体或森林。为此，我们需要将单个图层分解为独立的图层，这些图层符合特定标准，例如森林或河流。这是一个例子：

```csharp
var cities = inputLayer.Where(x => x.GetValue<string>("place") == "city");
citiesLayer = CopyToNewLayer(cities, inputLayer);

var forest = inputLayer.Where(x => x.GetValue<string>("landuse") == "forest");
forestLayer = CopyToNewLayer(forest, inputLayer);

var water = inputLayer.Where(x => !x.IsValueNull("water"));
waterLayer = CopyToNewLayer(water, inputLayer);
```

下面您将看到我们将如何使用这些图层。`CopyToNewLayer` 函数是辅助函数，它有助于创建新图层；对于本文来说，它不是特别重要的，您可以查看其实现方式在文章开头的仓库中。

现在我们只需要将所有这些渲染成 PNG 图块并将其返回给客户端。这是一个示例代码：

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

在这里，创建了一个大小为 256x256 的标准图块尺寸的 `Map` 对象。基本上，`Map` 是渲染图块的画布。接下来，我们初始化一个特殊的对象来标记，将规则传递给要绘制的几何形状进行文本渲染，例如房屋号码、街道名称等。在这种情况下，如果它不是多边形和/或 `addr:housenumber` 属性为空，则数据将从 `name` 属性中获取。

重要的是，Map 对象需要显式指定将在其中渲染的坐标系：

```csharp
map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
```

接下来，我们需要设置要渲染的实际图块区域，而不是我们从数据库请求的扩展区域。为此，我们通过 `Extent` 属性显式设置渲染区域：

```csharp
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);
```

然后我们按顺序将图层添加到图块中。第一个添加在所有下方，最后一个在顶部。

最后，我们需要将图块渲染为内存中的字节流，然后重置流到开头，并将流传递给 ASP.NET Core 平台以进一步传输给客户端：

```csharp
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

pngStream.Seek(0, SeekOrigin.Begin);

return File(pngStream, "image/png");
```

希望我们能够将构建地图的基本思想和技术传递给您。祝您在实验中一切顺利。