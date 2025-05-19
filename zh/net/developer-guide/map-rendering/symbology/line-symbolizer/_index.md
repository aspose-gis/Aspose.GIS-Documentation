---
title: "线条符号化器"
type: docs
url: /zh/net/line-symbolizer/
weight: 20
description: GIS C# Library 或 API 支持用于一维几何体（线）的简单线条符号化器，并且可以应用于任何类型的几何体，例如点、线、面。
---

## **线条符号化器**
简单的线条符号化器绘制具有可自定义样式的线条。 这是默认的一维几何体（线）符号化器。 

支持的样式选项：

|**属性**|**描述**|
| :- | :- |
|[Color](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|指定赋予线条的颜色和透明度。|
|[Width](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|指定线条的宽度|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|确定如何在行段的交点处渲染线。|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|指定应如何绘制符号线条。|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|指定一个距离数组，该数组指定虚线中交替的短划线和空格的长度。|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|指定从线条开始到破折模式开始的距离。|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>指定如何在线条末端渲染线。</p><p>- Butt - 锐利的方形边缘</p><p>- Round - 圆形边缘</p><p>- Square - 略微拉长的方形边缘</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|指定与原始线的偏移量。 对于正距离，偏移将在输入线的左侧（相对于线方向）。 对于负距离，它将在右侧。|

### **几何类型**
` `符号化器可以应用于任何类型的几何体。

|**几何维度**|**几何类型**|**渲染行为**|
| :-: | :-: | :-: |
|**点**|Point, MultiPoint|绘制以水平方向为中心的小长度线，并在点的两端带有两个端盖。|
|**线**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|绘制线条。|
|**面**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|几何体的封闭轮廓用作线条（没有端盖）|

对于 GeometryCollections，渲染行为是针对集合内的每个几何体单独确定的。 具有混合几何类型的图层遵循 GeometryCollections 的逻辑。

使用 MixedGeometrySymbolizer 将符号化器限制为特定的几何类型。

### **示例**
默认情况下，线条符号化器绘制黑色线条：



这里是如何将线条颜色更改为蓝色：



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

-----

对于更高级的场景，您可能希望根据要素属性值动态调整线条样式。 以下是如何做到：



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |



-----

您可能还希望为线条添加标签。 请访问 [线条标注示例](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) 以获取示例。
