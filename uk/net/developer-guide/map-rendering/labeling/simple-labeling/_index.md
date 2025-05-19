---
title: "Просте Маркування"
type: docs
url: /uk/net/simple-labeling/
weight: 10
---

## **Просте Маркування**
Просте маркування визначає, як потрібно позначати об'єкти.

Підтримувані опції:

|**Властивість**|**Опис**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Визначає ім'я атрибута, який буде використовуватися як джерело міток.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Надає спосіб налаштування та форматування тексту мітки. Перевизначає LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Визначає сімейство шрифтів, яке буде використовуватися для відображення тексту. Значення за замовчуванням залежить від системи.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Стиль, який потрібно застосувати до тексту.</p><p>- FontStyle.Regular - звичайний текст.</p><p>- FontStyle.Bold - жирний текст.</p><p>- FontStyle.Italic - курсив.</p><p>- FontStyle.Underine - підкреслений текст.</p><p>- FontStyle.StrikeOut - текст із лінією посередині.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Визначає розмір тексту.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Визначає колір тексту.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Визначає розмір ореолу (або контуру) навколо тексту.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Визначає колір ореолу навколо тексту.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Геометричний вираз, який буде використовуватися для перетворення геометрії перед передачею її в механізм маркування.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Визначає поведінку рендерингу для багатокомпонентних геометрій.</p><p>- MultipartMode.All - розмістити мітку біля кожної частини геометрії.</p><p>- MultipartMode.Any - розмістити одну мітку біля будь-якої частини геометрії.</p><p>- MultipartMode.Largest - розмістити мітку біля найбільшої частини геометрії.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Визначає, як мітки розташовуються відносно геометрії.</p><p>- PointLabelPlacement - розміщує мітку біля центру геометрії.</p><p>- LineLabelPlacement - розміщує мітку вздовж геометрії або її периметра.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Визначає пріоритет мітки у випадку, якщо вона перекривається з іншою міткою.<br>Мітка з нижчим пріоритетом не відображається. Значення за замовчуванням - 1000.|

## **Приклади**
### **Приклади Маркування Точок**
За замовчуванням SimpleLabeling малює текст над точками:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
Ось як стилізувати шрифт:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
Щоб контролювати положення тексту відносно точкової ознаки, потрібно встановити властивість placement:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
Для більш просунутих сценаріїв, можливо, ви захочете вибрати різні мітки для об'єктів. Ось як це зробити:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **Приклади Маркування Ліній**
За замовчуванням SimpleLabeling малює мітку біля центру лінії:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
Щоб повернути мітки так, щоб вони були паралельні лініям, можна використовувати LineLabelPlacement з LineLabelAlignment.Parallel:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
Якщо ви хочете, щоб текст точно слідував лінії, можна використовувати LineLabelPlacement з LineLabelAlignment.Curved:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
Якщо ви не хочете, щоб текст перекривався з лінією, використовуйте LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
Для більш просунутих сценаріїв, можливо, ви захочете налаштувати стиль міток динамічно на основі значень атрибутів об'єктів. Ось як це зробити:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
