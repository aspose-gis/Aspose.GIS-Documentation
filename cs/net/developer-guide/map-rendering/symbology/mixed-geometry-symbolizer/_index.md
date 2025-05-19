---
title: "Symbolizér smíšené geometrie"
type: docs
url: /cs/net/mixed-geometry-symbolizer/
weight: 50
description: Symbolizér smíšené geometrie v API knihovny GIS C# umožňuje specifikovat symbolizéry samostatně pro každý typ geometrie, pokud vrstva obsahuje smíšené typy geometrií.
---

## **Symbolizér smíšené geometrie**
Symbolizér smíšené geometrie umožňuje specifikovat symbolizéry samostatně pro každý typ geometrie, pokud vrstva obsahuje smíšené typy geometrií.


|**Vlastnost**|**Popis**|
| :- | :- |
|[PointSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/pointsymbolizer)|Specifikuje symbolizér pro použití u bodových geometrií ve vrstvě (Bod, MultiBod)|
|[LineSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/linesymbolizer)|Specifikuje symbolizér pro použití u liniových geometrií ve vrstvě (LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString)|
|[PolygonSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/polygonsymbolizer)|Specifikuje symbolizér pro použití u polygonových geometrií ve vrstvě (Polygon, CurvePolygon, MultiPolygon, MultiSurface)|
### **Příklad**
V tomto příkladu vrstva obsahuje bod, linii a polygon. Budeme stylovat každý typ geometrie samostatně.
