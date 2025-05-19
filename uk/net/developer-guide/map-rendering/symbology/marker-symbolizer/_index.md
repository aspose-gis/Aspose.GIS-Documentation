---
title: "Маркерний Символізатор"
type: docs
url: /uk/net/marker-symbolizer/
weight: 10
description: GIS C# Бібліотека або API підтримує простий символізатор маркера, який малює попередньо визначену форму з настроюваним заповненням та обведенням на геометріях будь-якого типу, таких як Точка, Лінія, Поверхня.
---

## **Маркерний Символізатор**
Простий символізатор маркера малює попередньо визначену форму з настроюваним заповненням та обведенням. Це символ за замовчуванням для 0-вимірних геометрій (точок). 

Підтримувані форми:

|![todo:image_alt_text](marker-symbolizer_1.png)|Коло| |![todo:image_alt_text](marker-symbolizer_2.png)|Зірка|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Квадрат| |![todo:image_alt_text](marker-symbolizer_4.png)|Хрест|
|![todo:image_alt_text](marker-symbolizer_5.png)|Трикутник| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

Підтримувані параметри стилю:

|**Властивість**|**Опис**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|Визначає форму маркера.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|Визначає розмір форми маркера|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|Визначає колір та прозорість заповнення|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|Визначає колір та прозорість лінії|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|Визначає ширину лінії|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|Визначає, як лінії рендеряться в місцях перетину лінійних сегментів.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|Визначає, як повинні бути намальовані лінійні елементи символу.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|Визначає масив відстаней, який визначає довжини чергуючихся тире та проміжків у пунктирних лініях.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|Визначає відстань від початку лінії до початку шаблону тире.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|Визначає поворот символу навколо його центральної точки в десяткових градусах. Позитивні значення вказують на обертання за годинниковою стрілкою, негативні значення - проти годинникової стрілки. За замовчуванням 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|Визначає горизонтальне зміщення від координати точки до якоря форми.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|Визначає вертикальне зміщення від координати точки до якоря форми.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|Визначає, яка сторона форми маркера буде вирівняна горизонтально з точкою розташування.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|Визначає, яка сторона форми маркера буде вирівняна вертикально з точкою розташування.|

### **Типи Геометрії**
` `Символізатор може бути застосований до геометрій будь-якого типу.

|**Розмірність Геометрії**|**Типи Геометрії**|**Поведінка Рендерингу**|
| :-: | :-: | :-: |
|**Точка**|Point, MultiPoint|Малює форму в центрі координати точки.|
|**Лінія**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>Малює форму в центрі геометрії</p><p> </p>|
|**Поверхня**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

Для GeometryCollections поведінка рендерингу визначається окремо для кожної геометрії всередині колекції. Шари з змішаним типом геометрії слідують логіці для GeometryCollections.

Використовуйте MixedGeometrySymbolizer, щоб обмежити символізатор певними типами геометрії.

### **Приклади**
За замовчуванням маркерний символізатор малює чорні кола:



Ось як змінити колір заливки на червоний:



|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

Інший приклад стилізації з попередньо визначеною формою (трикутник):



|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----
Для більш просунутих сценаріїв, можливо, ви захочете налаштувати стиль маркера динамічно на основі значень атрибутів об'єкта. Ось як це зробити:



|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
Ви також можете захотіти додати підписи до своїх маркерів. Відвідайте [Приклади позначення точок](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) для прикладів.
