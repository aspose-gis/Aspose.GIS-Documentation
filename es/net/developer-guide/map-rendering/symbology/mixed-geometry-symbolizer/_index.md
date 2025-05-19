---
title: "Simbolizador de Geometría Mixta"
type: docs
url: /es/net/mixed-geometry-symbolizer/
weight: 50
description: El Simbolizador de Geometría Mixta en la API de la Biblioteca C# GIS permite especificar simbolizadores por separado para cada tipo de geometría si una capa contiene tipos de geometría mixtos.
---

## **Simbolizador de Geometría Mixta**
El Simbolizador de Geometría Mixta permite especificar simbolizadores por separado para cada tipo de geometría si una capa contiene tipos de geometría mixtos.


|**Propiedad**|**Descripción**|
| :- | :- |
|[PointSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/pointsymbolizer)|Especifica un simbolizador para usar para geometrías de punto en la capa (Punto, MultiPunto)|
|[LineSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/linesymbolizer)|Especifica un simbolizador para usar para geometrías de línea en la capa (LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString)|
|[PolygonSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/polygonsymbolizer)|Especifica un simbolizador para usar para geometrías de polígono en la capa (Polígono, CurvePolygon, MultiPolígono, MultiSurface)|
### **Ejemplo**
En este ejemplo, una capa contiene un punto, una línea y un polígono. Estilizaremos cada tipo de geometría por separado.
