---
title: "Simbolizzatore di Geometrie Miste"
type: docs
url: /it/net/mixed-geometry-symbolizer/
weight: 50
description: Il Simbolizzatore di Geometrie Miste nella libreria API GIS C# consente di specificare i simbolizzatori separatamente per ogni tipo di geometria se un layer contiene tipi di geometria misti.
---

## **Simbolizzatore di Geometrie Miste**
Il Simbolizzatore di Geometrie Miste consente di specificare i simbolizzatori separatamente per ogni tipo di geometria se un layer contiene tipi di geometria misti.


|**Proprietà**|**Descrizione**|
| :- | :- |
|[PointSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/pointsymbolizer)|Specifica un simbolizzatore da utilizzare per le geometrie di tipo punto nel layer (Punto, MultiPunto)|
|[LineSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/linesymbolizer)|Specifica un simbolizzatore da utilizzare per le geometrie di tipo linea nel layer (LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString)|
|[PolygonSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/polygonsymbolizer)|Specifica un simbolizzatore da utilizzare per le geometrie di tipo poligono nel layer (Poligono, CurvePolygon, MultiPoligono, MultiSurface)|
### **Esempio**
In questo esempio, un layer contiene un punto, una linea e un poligono. Stileremo ogni tipo di geometria separatamente.
