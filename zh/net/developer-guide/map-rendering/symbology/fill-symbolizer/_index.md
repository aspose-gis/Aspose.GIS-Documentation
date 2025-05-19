---
title: "填充符号化"
type: docs
url: /zh/net/fill-symbolizer/
weight: 30
description: GIS C# Library API 支持简单的填充符号化，用于为二维几何图形（例如点、线、面）的样式和描边填充。
---

## **填充符号化**
简单的填充符号化使用可自定义的填充样式和描边来填充区域。 这是二维几何图形（多边形）的默认符号化器。 

如果多边形具有“孔洞”，则不会填充它们，但孔洞周围的边界以通常的方式进行描边。“岛屿”位于孔洞内被填充并描边，依此类推。

支持的样式选项：

|**属性**|**描述**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|指定给定填充的颜色和透明度。|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - 纯色填充</p><p>- None - 不填充多边形</p><p>- Horizontal Hatch - 水平线条图案。</p><p>- Vertical Hatch - 垂直线条图案。</p><p>- Cross Hatch - 指定水平和垂直相交的线条。</p><p>- Forward Diagonal Hatch - 从左上到右下的对角线线条图案。</p><p>- Backward Diagonal Hatch - 从右上到左下的对角线线条图案。</p><p>- Diagonal Cross Hatch - 交叉对角线线条图案。</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|指定给定描边线的颜色和透明度。|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|指定应如何绘制符号线条。|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|指定描边线的宽度。|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|指定一个距离数组，该数组指定虚线中交替的短划线和空格的长度。|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|指定从线条开始到虚线图案开始的距离。|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>确定如何在行段的交点处渲染行。</p><p>- Miter - 锐角</p><p>- Round - 圆角</p><p>- Bevel - 对角线角</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|指定从点位置到形状锚点之间的水平偏移量。|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|指定从点位置到形状锚点之间的垂直偏移量。|

### **几何类型**
` `符号化器可以应用于任何类型的几何图形。

|**几何维度**|**几何类型**|**渲染行为**|
| :-: | :-: | :-: |
|**点**|Point, MultiPoint|绘制一个小正方形直角多边形。|
|**线**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|通过将线条的端点连接到起点来关闭线条进行填充。仅对原始线条进行描边。|
|**面**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|绘制多边形。|

对于 GeometryCollections，渲染行为是针对集合内的每个几何图形分别确定的。具有混合几何类型的图层遵循 GeometryCollections 的逻辑。

使用 MixedGeometrySymbolizer 将符号化器限制为特定的几何类型。

### **示例**
默认情况下，简单的填充符号化器绘制黑色描边线和纯白色填充：



这里是如何更改样式的：




|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

-----
您可能还想为您的多边形添加标签。请访问 [线条标注示例](/gis/zh/simple-labeling/#simplelabeling-lineslabelingexamples) 了解有关如何标记多边形边界的示例，或访问 [点标注示例](/gis/zh/simple-labeling/#simplelabeling-pointslabelingexamples) 了解有关如何标记多边形中心的示例。
