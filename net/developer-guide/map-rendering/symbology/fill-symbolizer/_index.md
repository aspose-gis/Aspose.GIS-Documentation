---
title: "Fill Symbolizer"
type: docs
url: /net/fill-symbolizer/
weight: 30
description: GIS C# Library API supports Simple Fill symbolizer to fill style and stroke for 2-dimensional geometries polygons of any type like Point, Line, Surface.
---

## **Fill Symbolizer**
The Simple Fill symbolizer fills an area with a customizable fill style and stroke. This is the default symbolizer for 2-dimensional geometries (polygons). 

If a polygon has “holes,”  they are not filled, but the borders around the holes are stroked in the usual way. “Islands” within holes are filled and stroked, and so on.

Supported styling options:

|**Property**|**Description**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Specifies the color and transparency given to the fill.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - Solid fill</p><p>- None - Do not fill the polygon</p><p>- Horizontal Hatch - A pattern of horizontal lines.</p><p>- Vertical Hatch - A pattern of vertical lines.</p><p>- Cross Hatch - Specifies horizontal and vertical lines that cross.</p><p>- Forward Diagonal Hatch - A pattern of lines on a diagonal from upper left to lower right.</p><p>- Backward Diagonal Hatch - A pattern of lines on a diagonal from upper right to lower left.</p><p>- Diagonal Cross Hatch - A pattern of criss-cross diagonal lines.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Specifies the color and transparency given to the stroke line.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Specifies how the symbol linework should be drawn.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Specifies the width of the stroke line.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Specifies an array of distances that specifies the lengths of alternating dashes and spaces in dashed lines.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Specifies the distance from the start of a line to the beginning of a dash pattern.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Determines how lines are rendered at intersections of line segments.</p><p>- Miter - sharp corner</p><p>- Round - rounded corner</p><p>- Bevel - diagonal corner</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Specifies horizontal offset from a point location  to the shape anchor point.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Specifies vertical offset from a point location to the shape anchor point.|
### **Geometry Types**
` `The symbolizer can be applied to geometries of any type.

|**Geometry Dimension**|**Geometry Types**|**Rendering Behavior**|
| :-: | :-: | :-: |
|**Point**|Point, MultiPoint|Draws a small square orthogonal polygon.|
|**Line**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|The line is closed for filling by connecting its end point to its start point. Only the original line is stroked.|
|**Surface**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Draws the polygon.|


For GeometryCollections, the rendering behavior is determined separately for each geometry inside the collection. Layers with Mixed geometry type follow the logic for GeometryCollections.

Use MixedGeometrySymbolizer to limit a symbolizer to specific geometry types.

### **Examples**
By default the Simple Fill symbolizer a draws black stroke line and solid white fill:







-----
Here's how to change styling:



|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |


-----
You might also want to add labels to your polygons. Visit [Lines Labeling Examples](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) for examples on how to label polygons border or [Points Labeling Examples](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) on exmaples on how to label polygons centers.
