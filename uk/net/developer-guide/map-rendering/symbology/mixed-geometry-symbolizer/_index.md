---
title: "Змішаний геометричний символізатор"
type: docs
url: /uk/net/mixed-geometry-symbolizer/
weight: 50
description: Змішаний геометричний символізатор у GIS C# Library API дозволяє вказувати символізатори окремо для кожного типу геометрії, якщо шар містить змішані типи геометрії.
---

## **Змішаний геометричний символізатор**
Змішаний геометричний символізатор дозволяє вказувати символізатори окремо для кожного типу геометрії, якщо шар містить змішані типи геометрії.


|**Властивість**|**Опис**|
| :- | :- |
|[PointSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/pointsymbolizer)|Визначає символізатор для використання точкових геометрій у шарі (Точка, MultiPoint)|
|[LineSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/linesymbolizer)|Визначає символізатор для використання лінійних геометрій у шарі (LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString)|
|[PolygonSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/polygonsymbolizer)|Визначає символізатор для використання полігональних геометрій у шарі (Полігон, CurvePolygon, MultiPolygon, MultiSurface)|
### **Приклад**
У цьому прикладі шар містить точку, лінію та полігон. Ми будемо стилізувати кожен тип геометрії окремо.
