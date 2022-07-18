---
title: "Simple Labeling"
type: docs
url: /net/simple-labeling/
weight: 10
---

## **Simple Labeling**
The Simple Labeling specifies how features must be labeled.

Supported options are:

|**Property**|**Description**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Specifies attribute name to be used as a source of labels.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Provides a way to customize and format label text. Overrides LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Specifies font family to use to render text. The default is system dependent value.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Style to apply to text.</p><p>- FontStyle.Regular - regular text.</p><p>- FontStyle.Bold - bold text.</p><p>- FontStyle.Italic - italic text.</p><p>- FontStyle.Underine - underlined text.</p><p>- FontStyle.StrikeOut - text with a line through the middle.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Specifies size of the text.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Determines color of the text.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Determines a size of the halo (or outline) around the text.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Determines color of the halo around the text.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Geometry expression to be used to transform geometries before passing it to the labeling engine.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Specifies rendering behavior for multipart geometries.</p><p>- MultipartMode.All - place a label near every part of the geometry.</p><p>- MultipartMode.Any - place one label near any part of the geometry.</p><p>- MultipartMode.Largest - place a label near the largest part of the geometry.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Specifies how labels are placed relatively to the geometry.</p><p>- PointLabelPlacement - places label near the center of the geometry.</p><p>- LineLabelPlacement - places label along the geometry or its perimeter.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Specifies priority of the label in case if it overlaps with other label.<br>The label with lower priority is not rendered. Default is 1000.|
## **Examples**
### **Points Labeling Examples**
By default SimpleLabeling draws text over points:


|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |


-----
Here's how to style font:



|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |


-----
In order to control text position relatively to point feature, placement property must be set:



|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |


-----
For more advanced scenarios, you might want to choose different labelings for features. Here's how to do that:



|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |
-----
### **Lines Labeling Examples**
By default SimpleLabeling draws label near center of the line:



|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |


-----
In order to rotate labels so they are parallel to lines, LineLabelPlacement with LineLabelAlignment.Parallel can be used:



|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |


-----
If you want texts to follow line precisely, LineLabelPlacement with LineLabelAlignment.Curved can be used:



|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |


-----
If you don't want texts to overlap with line, use LineLabelPlacement.Offset:



|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |


-----
For more advanced scenarios, you might want to adjust the labels style dynamically based on feature attribute values. Here's how to do that:



|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |

