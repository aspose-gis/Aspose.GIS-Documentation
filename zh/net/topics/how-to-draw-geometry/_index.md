---
title: "如何在地图上绘制几何图形"
type: docs
url: /zh/net/how-to-draw-geometry
weight: 70
---

要创建并在地图上显示几何对象，首先需要**创建一个几何对象**。 您可以使用两种方法：

- **每种几何要素类型的构造函数**
这种方法涉及为每种几何要素类型使用自定义构造函数。 例如，要创建一个点，您将使用以下代码：

```
Point point = new Point(40.7128, -74.006);
```

但是，当创建复杂的对象（如多段线或集合）时，这种方法可能会变得具有挑战性和繁琐。 因此，开发人员可能需要添加许多行代码，从而降低代码的可读性。 在初始化期间确保数据完整性也可能很困难。 例如，考虑以下示例，该示例创建一个带有内部孔的多边形：

```
Polygon polygon = new Polygon();

LinearRing ring = new LinearRing();
ring.AddPoint(50.02, 36.22);
ring.AddPoint(49.99, 36.26);
ring.AddPoint(49.97, 36.23);
ring.AddPoint(49.98, 36.17);
ring.AddPoint(50.02, 36.22);

LinearRing hole = new LinearRing();
hole.AddPoint(50.00, 36.22);
hole.AddPoint(49.99, 36.20);
hole.AddPoint(49.98, 36.23);
hole.AddPoint(50.00, 36.24);
hole.AddPoint(50.00, 36.22);

polygon.ExteriorRing = ring;
polygon.AddInteriorRing(hole);
```

这种方法的另一个缺点是初始化数据的缺乏统一性。 您无法在项目中创建常数或文件的存储库。

- **WKT（Well-Known Text）**
这种方法涉及从 WKT（Well-Known Text）生成几何图形，它提供了一种标准化的方式来创建几何图形。 以下代码演示了如何创建一个点和一条线：

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

虽然这种方法可能会略微降低性能，因为需要解析字符串，但它简化了创建更复杂对象的流程。

您可以在以下文章中找到有关 WKT 的更多详细信息：“导出和导入 WKT 和 WKB 中的数据”。

在地图上显示几何对象
创建几何对象后，下一步是在地图上显示它。 虽然地图可以显示从各种来源和格式加载的图层，但 InMemoryLayer 是一个不需要源的图层。

**要显示您的几何对象**，您可以创建一个 InMemoryLayer 并将该对象添加到其中：

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

现在您可以**将此图层显示在地图上，并以 SVG 等受支持格式之一创建文件**，方法如下：

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

添加图层并在地图上显示它后，您可以将其保存为任何受支持的格式。 在此示例中，选择 SVG 格式以避免 Bitmap 支持可能存在的问题。 值得注意的是，Net 6.0 的 Bitmap 支持有限，这可能会导致限制，例如无法使用 Blazor WebAsm 在客户端渲染 Bitmap 图像。 因此，在选择用于保存地图的格式时，重要的是要考虑目标平台的限制并选择与之兼容的格式。

本文档解释了如何在默认、纯样式下创建并在地图上显示几何对象。 但是，Aspose 库提供了广泛的样式选项，可以自定义以适应您的需求。 要探索这些选项，我们建议查阅[Aspose.MapRendering 文档](https://docs.aspose.com/gis/net/map-rendering/)，其中提供了有关如何使用不同的样式技术来增强地图视觉吸引力的详细信息。

**总而言之**，要创建地图上的几何对象，您可以使用每种几何要素类型的构造函数或从 WKT 生成几何图形。 要显示该对象，请将其放置在图层上并在默认地图样式中将图层显示在地图上。 以 SVG 等受支持的格式保存地图，并使用我们的库探索样式选项。 此外，我们的库提供了一个机会来查看完成的示例，方法是单击文档提供的[链接](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer)，这可以帮助您了解如何在自己的项目中实现这些技术。
