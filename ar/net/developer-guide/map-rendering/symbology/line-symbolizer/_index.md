---
title: "مُرمِّز الخط"
type: docs
url: /ar/net/line-symbolizer/
weight: 20
description: مكتبة GIS C# أو واجهة برمجة التطبيقات (API) تدعم مُرمِّز الخط البسيط للهندسة أحادية الأبعاد وهي الخطوط، ويمكن تطبيقها على هندسات من أي نوع مثل النقطة والخط والسطح.
---

## **مُرمِّز الخط**
يرسم مُرمِّز الخط البسيط خطًا بأسلوب قابل للتخصيص. هذا هو المُرمِّز الافتراضي للهندسة أحادية الأبعاد (الخطوط). 

خيارات التنسيق المدعومة:

|**خاصية**|**الوصف**|
| :- | :- |
|[Color](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|يحدد اللون والشفافية المعطاة للخط.|
|[Width](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|يحدد عرض الخط|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|يحدد كيفية عرض الخطوط عند تقاطعات أجزاء الخط.|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|يحدد كيف يجب رسم خط الرمز.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|يحدد مصفوفة من المسافات التي تحدد أطوال الشرطات والمسافات المتبادلة في الخطوط المنقطة.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|يحدد المسافة من بداية الخط إلى بداية نمط الشرطة.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>يحدد كيفية عرض الخطوط في نهاياتها.</p><p>- Butt - حافة مربعة حادة</p><p>- Round - حافة مستديرة</p><p>- Square - حافة مربعة ممدودة قليلاً</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|يحدد الإزاحة من الخط الأصلي. بالنسبة للمسافة الموجبة، ستكون الإزاحة على الجانب الأيسر من الخط المدخل (بالنسبة لاتجاه الخط). بالنسبة للمسافة السالبة، ستكون على الجانب الأيمن.|

### **أنواع الهندسة**
` `يمكن تطبيق المُرمِّز على هندسات من أي نوع.

|**أبعاد الهندسة**|**أنواع الهندسة**|**سلوك العرض**|
| :-: | :-: | :-: |
|**نقطة**|نقطة، MultiPoint|يرسم خطًا بطول صغير مع اتجاه أفقي متمركز على النقطة، مع غطاءين للنهاية.|
|**خط**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|يرسم الخط.|
|**سطح**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|يستخدم المخطط التفصيلي للهندسة كخط (بدون أغطية للنهاية)|

بالنسبة لمجموعات الهندسة، يتم تحديد سلوك العرض بشكل منفصل لكل هندسة داخل المجموعة. تتبع الطبقات ذات النوع الهندسي المختلط منطق مجموعات الهندسة.

استخدم MixedGeometrySymbolizer للحد من المُرمِّز إلى أنواع هندسة محددة.

### **أمثلة**
بشكل افتراضي، يرسم مُرمِّز الخط خطوطًا سوداء:



إليك كيفية تغيير لون الخط إلى اللون الأزرق:



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

-----

للحصول على سيناريوهات أكثر تقدمًا، قد ترغب في تعديل نمط الخط ديناميكيًا بناءً على قيم سمات الميزة. إليك كيفية القيام بذلك:



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |



-----

قد ترغب أيضًا في إضافة تسميات إلى خطوطك. قم بزيارة [أمثلة تسمية الخطوط](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) للحصول على أمثلة.
