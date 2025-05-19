---
title: "Mixed Geometry Symbolizer"
type: docs
url: /vi/net/mixed-geometry-symbolizer/
weight: 50
description: Mixed Geometry Symbolizer trong GIS C# Library API cho phép chỉ định các symbolizers riêng biệt cho mỗi loại hình học nếu một lớp chứa các loại hình học hỗn hợp.
---

## **Mixed Geometry Symbolizer**
The Mixed Geometry Symbolizer allows to specify symbolizers separately for each geometry type if a layer contains mixed geometry types.

|**Property**|**Description**|
| :- | :- |
|[PointSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/pointsymbolizer)|Chỉ định một symbolizer để sử dụng cho các hình học điểm trong lớp (Điểm, MultiPoint)|
|[LineSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/linesymbolizer)|Chỉ định một symbolizer để sử dụng cho các hình học đường trong lớp (LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString)|
|[PolygonSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/polygonsymbolizer)|Chỉ định một symbolizer để sử dụng cho các hình học đa giác trong lớp (Đa giác, CurvePolygon, MultiPolygon, MultiSurface)|
### **Example**
Trong ví dụ này, một lớp chứa một điểm, một đường và một đa giác. Chúng ta sẽ tạo kiểu cho mỗi loại hình học riêng biệt.
