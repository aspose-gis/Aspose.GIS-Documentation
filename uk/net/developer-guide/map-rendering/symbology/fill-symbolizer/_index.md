---
title: "Заповнювач Символів"
type: docs
url: /uk/net/fill-symbolizer/
weight: 30
description: GIS C# Library API підтримує простий заповнювач символів для стилю та обведення двовимірних геометричних фігур полігонів будь-якого типу, таких як Точка, Лінія, Поверхня.
---

## **Заповнювач Символів**
Простий заповнювач символів заповнює область настроюваним стилем заповнення та обведенням. Це символ за замовчуванням для двовимірних геометричних фігур (полігонів). 

Якщо полігон має “отвори”, вони не заповнюються, але межі навколо отворів обводяться звичайним способом. “Острови” всередині отворів заповнюються та обводяться, і так далі.

Підтримувані параметри стилю:

|**Властивість**|**Опис**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Визначає колір і прозорість, задані заповненню.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - Суцільне заповнення</p><p>- None - Не заповнювати полігон</p><p>- Horizontal Hatch - Шаблон горизонтальних ліній.</p><p>- Vertical Hatch - Шаблон вертикальних ліній.</p><p>- Cross Hatch - Визначає горизонтальні та вертикальні лінії, що перетинаються.</p><p>- Forward Diagonal Hatch - Шаблон ліній по діагоналі з верхнього лівого кута до нижнього правого.</p><p>- Backward Diagonal Hatch - Шаблон ліній по діагоналі з верхнього правого кута до нижнього лівого.</p><p>- Diagonal Cross Hatch - Шаблон перехрещених діагональних ліній.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Визначає колір і прозорість, задані лінії обведення.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Визначає, як повинні бути намальовані лінійні елементи символу.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Визначає ширину лінії обведення.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Визначає масив відстаней, який визначає довжини чергування штрихів і проміжків у пунктирних лініях.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Визначає відстань від початку лінії до початку шаблону штрихів.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Визначає, як лінії рендеряться в місцях перетину сегментів ліній.</p><p>- Miter - гострий кут</p><p>- Round - заокруглений кут</p><p>- Bevel - діагональний кут</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Визначає горизонтальне зміщення від точки розташування до якоря фігури.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Визначає вертикальне зміщення від точки розташування до якоря фігури.|

### **Типи Геометрії**
` `Символ може бути застосований до геометрій будь-якого типу.

|**Розмірність Геометрії**|**Типи Геометрії**|**Поведінка Рендерингу**|
| :-: | :-: | :-: |
|**Точка**|Point, MultiPoint|Малює невеликий квадратний ортогональний полігон.|
|**Лінія**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Лінію закривають для заповнення, з’єднавши її кінцеву точку з початковою точкою. Тільки оригінальна лінія обводиться.|
|**Поверхня**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Малює полігон.|

Для GeometryCollections поведінка рендерингу визначається окремо для кожної геометрії всередині колекції. Шари з змішаним типом геометрії слідують логіці для GeometryCollections.

Використовуйте MixedGeometrySymbolizer, щоб обмежити символ певними типами геометрії.

### **Приклади**
За замовчуванням Simple Fill symbolizer малює чорну лінію обведення та суцільне біле заповнення:



Тут як змінити стиль:




|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

Ви також можете додати підписи до своїх полігонів. Відвідайте [Приклади лінійного маркування](/gis/uk/simple-labeling/#simplelabeling-lineslabelingexamples) для прикладів того, як позначити межі полігонів або [Приклади маркування точок](/gis/uk/simple-labeling/#simplelabeling-pointslabelingexamples) на прикладах того, як позначити центри полігонів.
