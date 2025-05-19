---
title: "Mixed Geometry Symbolizer"
type: docs
url: /th/net/mixed-geometry-symbolizer/
weight: 50
description: Mixed Geometry Symbolizer ใน GIS C# Library API ช่วยให้สามารถระบุ symbolizers แยกกันสำหรับแต่ละประเภทของ geometry ได้ หาก layer ประกอบด้วย mixed geometry types
---

## **Mixed Geometry Symbolizer**
Mixed Geometry Symbolizer ช่วยให้สามารถระบุ symbolizers แยกกันสำหรับแต่ละประเภทของ geometry ได้ หาก layer ประกอบด้วย mixed geometry types

|**Property**|**Description**|
| :- | :- |
|[PointSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/pointsymbolizer)|ระบุ symbolizer ที่จะใช้สำหรับ geometries ประเภท point ใน layer (Point, MultiPoint)|
|[LineSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/linesymbolizer)|ระบุ symbolizer ที่จะใช้สำหรับ geometries ประเภท line ใน layer (LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString)|
|[PolygonSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/polygonsymbolizer)|ระบุ symbolizer ที่จะใช้สำหรับ geometries ประเภท polygon ใน layer (Polygon, CurvePolygon, MultiPolygon, MultiSurface)|
### **Example**
ในตัวอย่างนี้ layer ประกอบด้วย point, line และ polygon เราจะกำหนดรูปแบบแต่ละประเภทของ geometry แยกกัน
