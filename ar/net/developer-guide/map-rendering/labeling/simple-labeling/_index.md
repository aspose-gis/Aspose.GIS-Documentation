---
title: "تسمية بسيطة"
type: docs
url: /ar/net/simple-labeling/
weight: 10
---

## **التسمية البسيطة**
تحدد التسمية البسيطة كيفية تسمية الميزات.

الخيارات المدعومة هي:

|**خاصية**|**الوصف**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|يحدد اسم السمة المراد استخدامه كمصدر للتسميات.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|يوفر طريقة لتخصيص وتنسيق نص التسمية. يتجاوز LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|يحدد عائلة الخط المستخدمة لعرض النص. الافتراضي هو قيمة تعتمد على النظام.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>النمط المراد تطبيقه على النص.</p><p>- FontStyle.Regular - نص عادي.</p><p>- FontStyle.Bold - نص عريض.</p><p>- FontStyle.Italic - نص مائل.</p><p>- FontStyle.Underine - نص مسطر.</p><p>- FontStyle.StrikeOut - نص بخط عبر المنتصف.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|يحدد حجم النص.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|يحدد لون النص.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|يحدد حجم الهالة (أو المخطط التفصيلي) حول النص.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|يحدد لون الهالة حول النص.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|تعبير هندسي ليتم استخدامه لتحويل الهندسة قبل تمريرها إلى محرك التسمية.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>يحدد سلوك العرض للهندسات متعددة الأجزاء.</p><p>- MultipartMode.All - ضع تسمية بالقرب من كل جزء من الهندسة.</p><p>- MultipartMode.Any - ضع تسمية واحدة بالقرب من أي جزء من الهندسة.</p><p>- MultipartMode.Largest - ضع تسمية بالقرب من أكبر جزء من الهندسة.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>يحدد كيفية وضع التسميات بالنسبة للهندسة.</p><p>- PointLabelPlacement - يضع التسمية بالقرب من مركز الهندسة.</p><p>- LineLabelPlacement - يضع التسمية على طول الهندسة أو محيطها.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|يحدد أولوية التسمية في حالة تداخلها مع تسمية أخرى.<br>لا يتم عرض التسمية ذات الأولوية المنخفضة.|

## **أمثلة**
### **أمثلة تسمية النقاط**
بشكل افتراضي، ترسم التسمية البسيطة النص فوق النقاط:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
إليك كيفية تصميم الخط:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
من أجل التحكم في موضع النص بالنسبة لميزة النقطة، يجب تعيين خاصية الموضع:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
للحصول على سيناريوهات أكثر تقدمًا، قد ترغب في اختيار تسميات مختلفة للميزات. إليك كيفية القيام بذلك:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **أمثلة تسمية الخطوط**
بشكل افتراضي، ترسم التسمية البسيطة تسمية بالقرب من مركز الخط:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
من أجل تدوير التسميات بحيث تكون موازية للخطوط، يمكن استخدام LineLabelPlacement مع LineLabelAlignment.Parallel:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
إذا كنت تريد أن يتبع النص الخط بدقة، فيمكن استخدام LineLabelPlacement مع LineLabelAlignment.Curved:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
إذا كنت لا تريد أن يتداخل النص مع الخط، فاستخدم LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
للحصول على سيناريوهات أكثر تقدمًا، قد ترغب في تعديل نمط التسميات ديناميكيًا بناءً على قيم سمات الميزة. إليك كيفية القيام بذلك:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
