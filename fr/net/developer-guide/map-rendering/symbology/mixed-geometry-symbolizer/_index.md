---
title: "Symboliseur de géométrie mixte"
type: docs
url: /fr/net/mixed-geometry-symbolizer/
weight: 50
description: Le symboliseur de géométrie mixte dans l'API de la bibliothèque C# GIS permet de spécifier des symboliseurs séparément pour chaque type de géométrie si une couche contient des types de géométrie mixtes.
---

## **Symboliseur de géométrie mixte**
Le Symboliseur de géométrie mixte permet de spécifier des symboliseurs séparément pour chaque type de géométrie si une couche contient des types de géométrie mixtes.


|**Propriété**|**Description**|
| :- | :- |
|[PointSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/pointsymbolizer)|Spécifie un symboliseur à utiliser pour les géométries de type point dans la couche (Point, MultiPoint)|
|[LineSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/linesymbolizer)|Spécifie un symboliseur à utiliser pour les géométries de type ligne dans la couche (LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString)|
|[PolygonSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/polygonsymbolizer)|Spécifie un symboliseur à utiliser pour les géométries de type polygone dans la couche (Polygon, CurvePolygon, MultiPolygon, MultiSurface)|
### **Exemple**
Dans cet exemple, une couche contient un point, une ligne et un polygone. Nous allons styliser chaque type de géométrie séparément.
