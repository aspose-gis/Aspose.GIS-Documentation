---
title: "Символ лінії"
type: docs
url: /uk/net/line-symbolizer/
weight: 20
description: GIS C# Library або API підтримує простий символ лінії для 1-вимірних геометрій ліній і може бути застосований до геометрій будь-якого типу, таких як Точка, Лінія, Поверхня.
---

## **Символ лінії**
Простий символ лінії малює лінію зі змінним стилем. Це символ за замовчуванням для 1-вимірних геометрій (ліній). 

Підтримувані параметри стилю:

|**Властивість**|**Опис**|
| :- | :- |
|[Колір](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|Визначає колір і прозорість лінії.|
|[Ширина](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|Визначає ширину лінії|
|[З'єднання ліній](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|Визначає, як лінії відображаються в місцях перетину сегментів ліній.|
|[Стиль](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|Визначає, як повинні бути намальовані символьні лінії.|
|[Шаблон штрихів](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|Визначає масив відстаней, які визначають довжини чергуючихся тире та пробілів у пунктирних лініях.|
|[Зміщення штрихів](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|Визначає відстань від початку лінії до початку шаблону штрихів.|
|[Стиль кришки](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>Визначає, як лінії відображаються на їхніх кінцях.</p><p>- Butt - різкий квадратний край</p><p>- Round - заокруглений край</p><p>- Square - трохи видовжений квадратний край</p>|
|[Зміщення](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|Визначає зміщення від початкової лінії. Для позитивної відстані зміщення буде зліва від вхідної лінії (відносно напрямку лінії). Для негативної відстані воно буде справа.|

### **Типи геометрії**
` `Символ може бути застосований до геометрій будь-якого типу.

|**Розмірність геометрії**|**Типи геометрії**|**Поведінка рендерингу**|
| :-: | :-: | :-: |
|**Точка**|Точка, MultiPoint|Малює лінію невеликої довжини з горизонтальною орієнтацією, центрованою на точці, з двома кінцевими кришками.|
|**Лінія**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Малює лінію.|
|**Поверхня**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Закритий контур геометрії використовується як лінія (без кінцевих кришок)|

Для GeometryCollections поведінка рендерингу визначається окремо для кожної геометрії всередині колекції. Шари з змішаним типом геометрії слідують логіці для GeometryCollections.

Використовуйте MixedGeometrySymbolizer, щоб обмежити символ певними типами геометрії.

### **Приклади**
За замовчуванням символ лінії малює чорні лінії:



Ось як змінити колір лінії на синій:



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

Для більш складних сценаріїв, можливо, захочете динамічно налаштувати стиль лінії на основі значень атрибутів об'єкта. Ось як це зробити:



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |



Ви також можете захотіти додати підписи до своїх ліній. Відвідайте [Приклади маркування ліній](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) для прикладів.
