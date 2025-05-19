---
title: "Смешанный Геометрический Символизатор"
type: docs
url: /ru/net/mixed-geometry-symbolizer/
weight: 50
description: Смешанный геометрический символизатор в API библиотеки GIS C# позволяет указывать символизаторы отдельно для каждого типа геометрии, если слой содержит смешанные типы геометрии.
---

## **Смешанный Геометрический Символизатор**
Смешанный геометрический символизатор позволяет указывать символизаторы отдельно для каждого типа геометрии, если слой содержит смешанные типы геометрии.


|**Свойство**|**Описание**|
| :- | :- |
|[PointSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/pointsymbolizer)|Указывает символизатор для использования с точечными геометриями в слое (Точка, MultiPoint)|
|[LineSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/linesymbolizer)|Указывает символизатор для использования с линейными геометриями в слое (LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString)|
|[PolygonSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/polygonsymbolizer)|Указывает символизатор для использования с полигональными геометриями в слое (Полигон, CurvePolygon, MultiPolygon, MultiSurface)|
### **Пример**
В этом примере слой содержит точку, линию и многоугольник. Мы будем стилизовать каждый тип геометрии отдельно.
