---
title: "混合几何符号化器"
type: docs
url: /zh/net/mixed-geometry-symbolizer/
weight: 50
description: GIS C# Library API 中的混合几何符号化器允许为包含混合几何类型的图层，为每种几何类型单独指定符号化器。
---

## **混合几何符号化器**
混合几何符号化器允许为包含混合几何类型的图层，为每种几何类型单独指定符号化器。


|**属性**|**描述**|
| :- | :- |
|[PointSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/pointsymbolizer)|指定用于图层中点几何体（点、多点）的符号化器|
|[LineSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/linesymbolizer)|指定用于图层中线几何体（LineString、CircularString、CompoundCurve、LinerRing、MultiCurve、MultiLineString）的符号化器|
|[PolygonSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/polygonsymbolizer)|指定用于图层中多边形几何体（Polygon、CurvePolygon、MultiPolygon、MultiSurface）的符号化器|
### **示例**
在此示例中，一个图层包含一个点、一条线和一个多边形。我们将分别设置每种几何类型的样式。
