---
title: "标记符号化器"
type: docs
url: /zh/net/marker-symbolizer/
weight: 10
description: GIS C# Library 或 API 支持简单的标记符号化器，该符号化器在任何类型的几何体（如点、线、面）上绘制具有可自定义填充和轮廓的预定义形状。
---

## **标记符号化器**
简单的标记符号化器绘制具有可自定义填充和轮廓的预定义形状。 这是 0 维几何体（点）的默认符号化器。 

支持的形状有：

|![todo:image_alt_text](marker-symbolizer_1.png)|圆形| |![todo:image_alt_text](marker-symbolizer_2.png)|星形|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|正方形| |![todo:image_alt_text](marker-symbolizer_4.png)|十字|
|![todo:image_alt_text](marker-symbolizer_5.png)|三角形| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

支持的样式选项：

|**属性**|**描述**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|指定标记的形状。|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|指定标记形状的大小|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|指定填充的颜色和透明度|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|指定线条的颜色和透明度|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|指定线条的宽度|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|确定在线段相交处如何渲染线条。|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|指定应如何绘制符号线工作。|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|指定一个距离数组，该数组指定虚线的交替短划线和空格的长度。|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|指定从线条开始到破折模式开始的距离。|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|指定符号围绕其中心点的旋转，以十进制度为单位。正值表示顺时针方向旋转，负值表示逆时针方向旋转。默认值为 0。|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|指定从点位置到形状锚点的水平偏移量。|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|指定从点位置到形状锚点的垂直偏移量。|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|指定标记形状的哪一侧将水平对齐于点位置。|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|指定标记形状的哪一侧将垂直对齐于点位置。|

### **几何类型**
` `符号化器可以应用于任何类型的几何体。

|**几何维度**|**几何类型**|**渲染行为**|
| :-: | :-: | :-: |
|**点**|Point, MultiPoint|在点的坐标处绘制形状居中。|
|**线**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>在几何体的质心处绘制形状</p><p> </p>|
|**面**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

对于GeometryCollections，渲染行为是针对集合内的每个几何体分别确定的。具有混合几何类型的图层遵循GeometryCollections的逻辑。

使用MixedGeometrySymbolizer将符号化器限制为特定的几何类型。

### **示例**
默认情况下，标记符号化器绘制黑色圆圈：



-----
以下是如何更改填充颜色为红色：



|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----


另一个使用预定义形状（三角形）样式的示例：



|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----
对于更高级的场景，您可能希望根据要素属性值动态调整标记样式。以下是如何操作：



|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
您可能还希望为标记添加标签。请访问[点标注示例](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) 了解更多示例。
