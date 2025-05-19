---
title: "Просто Етикетиране"
type: docs
url: /bg/net/simple-labeling/
weight: 10
---

## **Просто Етикетиране**
Простото етикетиране определя как трябва да бъдат етикетирани характеристиките.

Поддържаните опции са:

|**Свойство**|**Описание**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Определя името на атрибута, който да се използва като източник на етикетите.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Предоставя начин за персонализиране и форматиране на текста на етикета. Отменя LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Определя шрифта, който да се използва за рендиране на текста. По подразбиране е стойност, зависима от системата.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Стил, който да се приложи към текста.</p><p>- FontStyle.Regular - обикновен текст.</p><p>- FontStyle.Bold - удебелен текст.</p><p>- FontStyle.Italic - курсивен текст.</p><p>- FontStyle.Underine - подчертан текст.</p><p>- FontStyle.StrikeOut - текст с линия през средата.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Определя размера на текста.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Определя цвета на текста.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Определя размера на ореола (или контура) около текста.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Определя цвета на ореола около текста.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Израз за геометрия, който да се използва за трансформиране на геометриите преди предаването им към механизма за етикетиране.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Определя поведението при рендиране на многокомпонентни геометрии.</p><p>- MultipartMode.All - поставете етикет близо до всяка част от геометрията.</p><p>- MultipartMode.Any - поставете един етикет близо до която и да е част от геометрията.</p><p>- MultipartMode.Largest - поставете етикет близо до най-голямата част от геометрията.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Определя как се поставят етикетите спрямо геометрията.</p><p>- PointLabelPlacement - поставя етикет близо до центъра на геометрията.</p><p>- LineLabelPlacement - поставя етикет по протежение на геометрията или нейния периметър.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Определя приоритета на етикета в случай, че се припокрива с друг етикет.<br>Етикетът с по-нисък приоритет не се рендира. По подразбиране е 1000.|

## **Примери**
### **Примери за етикетиране на точки**
По подразбиране SimpleLabeling рисува текст върху точките:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
Ето как да стилизирате шрифта:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
За да контролирате позицията на текста спрямо точковата характеристика, трябва да се зададе свойството placement:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
За по-напреднали сценарии може да искате да изберете различни етикети за характеристиките. Ето как да го направите:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **Примери за етикетиране на линии**
По подразбиране SimpleLabeling рисува етикет близо до центъра на линията:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
За да завъртите етикетите, така че да са успоредни на линиите, може да се използва LineLabelPlacement с LineLabelAlignment.Parallel:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
Ако искате текстовете да следват линията прецизно, може да се използва LineLabelPlacement с LineLabelAlignment.Curved:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
Ако не искате текстовете да се припокриват с линията, използвайте LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
За по-напреднали сценарии може да искате да коригирате стила на етикетите динамично въз основа на стойностите на атрибутите на характеристиките. Ето как да го направите:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
