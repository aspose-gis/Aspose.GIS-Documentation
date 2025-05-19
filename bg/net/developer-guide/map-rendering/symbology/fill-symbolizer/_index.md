---
title: "Запълващ Символизатор"
type: docs
url: /bg/net/fill-symbolizer/
weight: 30
description: GIS C# Библиотечна API поддържа прост Запълващ символизатор за стил и контур на двуизмерни геометрии полигони от всякакъв тип като Точка, Линия, Повърхност.
---

## **Запълващ Символизатор**
Простият Запълващ символизатор запълва площ с персонализируем стил на запълване и контур. Това е символът по подразбиране за двуизмерни геометрии (полигони).

Ако полигон има „дупки“, те не се запълват, но границите около дупките се очертават по обичайния начин. „Острови“ в дупките са запълнени и очертани и т.н.

Поддържани опции за стилизиране:

|**Свойство**|**Описание**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Определя цвета и прозрачността, дадени на запълването.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - Плътно запълване</p><p>- None - Не запълвайте полигона</p><p>- Horizontal Hatch - Модел от хоризонтални линии.</p><p>- Vertical Hatch - Модел от вертикални линии.</p><p>- Cross Hatch - Определя хоризонтални и вертикални линии, които се пресичат.</p><p>- Forward Diagonal Hatch - Модел от линии по диагонал от горния ляв към долния десен ъгъл.</p><p>- Backward Diagonal Hatch - Модел от линии по диагонал от горния десен към долния ляв ъгъл.</p><p>- Diagonal Cross Hatch - Модел от кръстосани диагонални линии.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Определя цвета и прозрачността, дадени на контурната линия.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Определя как трябва да се рисуват линиите на символа.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Определя ширината на контурната линия.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Определя масив от разстояния, които определят дължините на редуващи се тирета и интервали в пунктирани линии.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Определя разстоянието от началото на линия до началото на модела на тирета.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Определя как линиите се визуализират в пресечните точки на сегментите на линията.</p><p>- Miter - остър ъгъл</p><p>- Round - заоблен ъгъл</p><p>- Bevel - диагонален ъгъл</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Определя хоризонтално отместване от местоположение на точка до котващата точка на формата.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Определя вертикално отместване от местоположение на точка до котващата точка на формата.|

### **Типове Геометрии**
` `Символизаторът може да се прилага към геометрии от всякакъв тип.

|**Размерност на Геометрията**|**Типове Геометрии**|**Поведение при Рендиране**|
| :-: | :-: | :-: |
|**Точка**|Точка, MultiPoint|Рисува малък квадратен ортогонален полигон.|
|**Линия**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Линията се затваря за запълване чрез свързване на крайната точка към началната точка. Само оригиналната линия е очертана.|
|**Повърхност**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Рисува полигона.|

За GeometryCollections поведението при рендиране се определя отделно за всяка геометрия в колекцията. Слоеве със смесен тип геометрия следват логиката за GeometryCollections.

Използвайте MixedGeometrySymbolizer, за да ограничите символизатора до специфични типове геометрии.

### **Примери**
По подразбиране простият Запълващ символизатор рисува черен контур и плътно бяло запълване:



Тук е как да промените стилизирането:


|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

Може също да искате да добавите етикети към вашите полигони. Посетете [Примери за Етикетиране на Линии](/gis/bg/net/simple-labeling/#simplelabeling-lineslabelingexamples) за примери как да етикетирате границите на полигоните или [Примери за Етикетиране на Точки](/gis/bg/net/simple-labeling/#simplelabeling-pointslabelingexamples) за примери как да етикетирате центровете на полигоните.
