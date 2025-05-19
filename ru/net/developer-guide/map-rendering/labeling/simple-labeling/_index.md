---
title: "Простое Маркирование"
type: docs
url: /ru/net/simple-labeling/
weight: 10
---

## **Простое Маркирование**
Простое маркирование определяет, как должны быть помечены объекты.

Поддерживаемые параметры:

|**Свойство**|**Описание**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Указывает имя атрибута, который будет использоваться в качестве источника меток.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Предоставляет способ настройки и форматирования текста метки. Переопределяет LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Указывает семейство шрифтов, используемое для отображения текста. Значение по умолчанию зависит от системы.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Стиль, применяемый к тексту.</p><p>- FontStyle.Regular - обычный текст.</p><p>- FontStyle.Bold - жирный текст.</p><p>- FontStyle.Italic - курсивный текст.</p><p>- FontStyle.Underine - подчеркнутый текст.</p><p>- FontStyle.StrikeOut - текст с линией посередине.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Указывает размер текста.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Определяет цвет текста.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Определяет размер ореола (или контура) вокруг текста.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Определяет цвет ореола вокруг текста.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Выражение геометрии, которое будет использоваться для преобразования геометрий перед передачей в механизм маркировки.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Указывает поведение рендеринга для многокомпонентных геометрий.</p><p>- MultipartMode.All - разместить метку рядом с каждой частью геометрии.</p><p>- MultipartMode.Any - разместить одну метку рядом с любой частью геометрии.</p><p>- MultipartMode.Largest - разместить метку рядом с самой большой частью геометрии.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Указывает, как метки располагаются относительно геометрии.</p><p>- PointLabelPlacement - размещает метку рядом с центром геометрии.</p><p>- LineLabelPlacement - размещает метку вдоль геометрии или ее периметра.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Указывает приоритет метки в случае, если она перекрывается с другой меткой.<br>Метка с более низким приоритетом не отображается. Значение по умолчанию - 1000.|

## **Примеры**
### **Примеры Маркировки Точек**
По умолчанию SimpleLabeling рисует текст поверх точек:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
Вот как стилизовать шрифт:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
Чтобы контролировать положение текста относительно точечного объекта, необходимо установить свойство placement:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
Для более сложных сценариев может потребоваться выбрать разные метки для объектов. Вот как это сделать:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **Примеры Маркировки Линий**
По умолчанию SimpleLabeling рисует метку рядом с центром линии:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
Чтобы повернуть метки так, чтобы они были параллельны линиям, можно использовать LineLabelPlacement с LineLabelAlignment.Parallel:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
Если вы хотите, чтобы текст точно следовал линии, можно использовать LineLabelPlacement с LineLabelAlignment.Curved:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
Если вы не хотите, чтобы текст перекрывался с линией, используйте LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
Для более сложных сценариев может потребоваться динамически настраивать стиль меток на основе значений атрибутов объектов. Вот как это сделать:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
