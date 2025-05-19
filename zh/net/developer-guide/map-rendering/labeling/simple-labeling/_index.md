---
title: "简单标签"
type: docs
url: /zh/net/simple-labeling/
weight: 10
---

## **简单标签**
简单标签指定了特征必须如何标记。

支持的选项有：

|**属性**|**描述**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|指定用作标签来源的属性名称。|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|提供了一种自定义和格式化标签文本的方式。覆盖 LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|指定用于渲染文本的字体系列。默认值取决于系统。|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>应用于文本的样式。</p><p>- FontStyle.Regular - 常规文本。</p><p>- FontStyle.Bold - 粗体文本。</p><p>- FontStyle.Italic - 斜体文本。</p><p>- FontStyle.Underine - 带下划线的文本。</p><p>- FontStyle.StrikeOut - 中间有一条线的文本。</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|指定文本的大小。|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|确定文本的颜色。|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|确定文本周围光晕（或轮廓）的大小。|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|确定文本周围光晕的颜色。|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|用于变换几何体的几何表达式，然后再将其传递给标签引擎。|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>指定多部件几何体的渲染行为。</p><p>- MultipartMode.All - 在几何体的每个部分附近放置标签。</p><p>- MultipartMode.Any - 在几何体的任何一部分附近放置一个标签。</p><p>- MultipartMode.Largest - 在几何体的最大部分附近放置标签。</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>指定标签相对于几何体的位置方式。</p><p>- PointLabelPlacement - 将标签放置在几何体的中心附近。</p><p>- LineLabelPlacement - 将标签放置在线或其周长上。</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|指定标签的优先级，以防它与其他标签重叠。<br>优先级较低的标签不会被渲染。默认值为 1000。|

## **示例**
### **点标签示例**
默认情况下，SimpleLabeling 在点上绘制文本：

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
以下是如何设置字体样式：

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
为了控制文本相对于点特征的位置，必须设置 placement 属性：

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
对于更高级的场景，您可能希望为特征选择不同的标签。以下是如何做到：

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **线标签示例**
默认情况下，SimpleLabeling 在线的中心附近绘制标签：

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
为了使标签平行于线，可以使用 LineLabelPlacement 和 LineLabelAlignment.Parallel：

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
如果您希望文本精确地跟随线，可以使用 LineLabelPlacement 和 LineLabelAlignment.Curved：

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
如果您不希望文本与线重叠，请使用 LineLabelPlacement.Offset：

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
对于更高级的场景，您可能希望根据特征属性值动态调整标签样式。以下是如何做到：

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
