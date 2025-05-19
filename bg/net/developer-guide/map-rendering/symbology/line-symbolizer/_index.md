---
title: "Символ на линия"
type: docs
url: /bg/net/line-symbolizer/
weight: 20
description: GIS C# Библиотека или API поддържа Simple Line символ за 1-измерни геометрии линии и може да се прилага върху геометрии от всякакъв тип като Point, Line, Surface.
---

## **Символ на линия**
Simple Line символът рисува линия с персонализируем стил. Това е символът по подразбиране за 1-измерни геометрии (линии). 

Поддържани опции за стилизиране:

|**Свойство**|**Описание**|
| :- | :- |
|[Цвят](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|Определя цвета и прозрачността, дадени на линията.|
|[Ширина](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|Определя ширината на линията|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|Определя как линиите се рендират в пресечните точки на сегментите на линии.|
|[Стил](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|Определя как символното очертание трябва да бъде нарисувано.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|Определя масив от разстояния, които определят дължините на редуващи се тирета и интервали в пунктирани линии.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|Определя разстоянието от началото на линия до началото на шаблон за тирета.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>Определя как линиите се рендират в краищата им.</p><p>- Butt - остра квадратна ръба</p><p>- Round - заоблен ръб</p><p>- Square - леко удължен квадратен ръб</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|Определя отместване от оригиналната линия. За положително разстояние отместването ще бъде от лявата страна на входната линия (спрямо посоката на линията). За отрицателно разстояние то ще бъде от дясната страна.|

### **Видове геометрии**
` `Символът може да се прилага към геометрии от всякакъв тип.

|**Размерност на геометрията**|**Видове геометрии**|**Поведение при рендиране**|
| :-: | :-: | :-: |
|**Точка**|Point, MultiPoint|Рисува линия с малка дължина с хоризонтална ориентация, центрирана върху точката, с два крайни капака.|
|**Линия**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Рисува линията.|
|**Повърхност**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Затворената очертание на геометрията се използва като низ на линия (без крайни капаци)|

За GeometryCollections поведението при рендиране се определя отделно за всяка геометрия в колекцията. Слоеве със смесен тип геометрия следват логиката за GeometryCollections.

Използвайте MixedGeometrySymbolizer, за да ограничите символ към специфични видове геометрии.

### **Примери**
По подразбиране символът на линията рисува черни линии:



Ето как да промените цвета на линията на синьо:




|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

За по-напреднали сценарии може да искате да коригирате стила на линията динамично въз основа на стойностите на атрибутите на обекта. Ето как да го направите:




|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |



Може също да искате да добавите етикети към линиите си. Посетете [Примери за етикетиране на линии](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) за примери.
