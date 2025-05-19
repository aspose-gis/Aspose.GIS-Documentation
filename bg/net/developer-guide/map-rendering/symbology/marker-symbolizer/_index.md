---
title: "Символизатор Маркер"
type: docs
url: /bg/net/marker-symbolizer/
weight: 10
description: GIS C# Библиотека или API поддържа прост символизатор на маркер, който рисува предварително дефинирана форма с персонализируема заливка и контур върху геометрии от всякакъв тип като Точка, Линия, Повърхност.
---

## **Символизатор Маркер**
Простият символизатор на маркер рисува предварително дефинирана форма с персонализируема заливка и контур. Това е символ по подразбиране за 0-измерни геометрии (точки). 

Поддържаните форми са:

|![todo:image_alt_text](marker-symbolizer_1.png)|Кръг| |![todo:image_alt_text](marker-symbolizer_2.png)|Звезда|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Квадрат| |![todo:image_alt_text](marker-symbolizer_4.png)|Кръст|
|![todo:image_alt_text](marker-symbolizer_5.png)|Триъгълник| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

Поддържани опции за стилизиране:

|**Свойство**|**Описание**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|Определя формата на маркера.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|Определя размера на формата на маркера|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|Определя цвета и прозрачността, дадени на запълването|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|Определя цвета и прозрачността, дадени на линията|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|Определя ширината на линията|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|Определя как линиите се рендират в пресечните точки на линейни сегменти.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|Определя как трябва да бъде изрисувана работата с линиите на символа.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|Определя масив от разстояния, които определят дължините на редуващи се тирета и интервали в пунктирани линии.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|Определя разстоянието от началото на линия до началото на модел на тирета.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|Определя въртенето на символа около неговата централна точка, в десетични градуси. Положителните стойности показват въртене по посока на часовниковата стрелка, отрицателните стойности показват въртене обратно на часовниковата стрелка. По подразбиране е 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|Определя хоризонтално отместване от местоположението на точка до котващата точка на формата.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|Определя вертикално отместване от местоположението на точка до котващата точка на формата.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|Определя коя страна на формата на маркера ще бъде подравнена хоризонтално с местоположението на точката.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|Определя коя страна на формата на маркера ще бъде подравнена вертикално с местоположението на точката.|

### **Видове Геометрии**
` `Символизаторът може да се прилага към геометрии от всякакъв тип.

|**Размерност на Геометрията**|**Видове Геометрии**|**Поведение при Рендиране**|
| :-: | :-: | :-: |
|**Точка**|Точка, MultiPoint|Рисува формата центрирана в координатата на точката.|
|**Линия**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>Рисува формата центрирана в центроида на геометрията</p><p> </p>|
|**Повърхност**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

За GeometryCollections поведението при рендиране се определя отделно за всяка геометрия вътре в колекцията. Слоеве със смесен тип геометрия следват логиката за GeometryCollections.

Използвайте MixedGeometrySymbolizer, за да ограничите символизатора до специфични видове геометрии.

### **Примери**
По подразбиране символизаторът на маркер рисува черни кръгове:



Ето как да промените цвета на запълване на червен:



|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

Друг пример за стилизиране с предварително дефинирана форма (триъгълник):



|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----
За по-напреднали сценарии може да искате да коригирате стила на маркера динамично въз основа на стойностите на атрибутите на обекта. Ето как да го направите:



|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
Може също да искате да добавите етикети към вашите маркери. Посетете [Примери за Етикетиране на Точки](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) за примери.
