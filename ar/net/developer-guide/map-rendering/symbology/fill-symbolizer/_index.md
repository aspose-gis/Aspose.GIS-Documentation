---
title: "مُرمِّز التعبئة"
type: docs
url: /ar/net/fill-symbolizer/
weight: 30
description: تدعم مكتبة GIS C# API مُرمِّز التعبئة البسيط لتعبئة الأنماط والحدبات للهندسة ثنائية الأبعاد متعددة الأضلاع من أي نوع مثل النقطة والخط والسطح.
---

## **مُرمِّز التعبئة**
يقوم مُرمِّز التعبئة البسيط بملء منطقة بنمط تعبئة وحدبة قابلة للتخصيص. هذا هو المُرمِّز الافتراضي للهندسة ثنائية الأبعاد (المضلعات). 

إذا كان للمضلع "ثقوب"، فلا يتم ملؤها، ولكن الحدود حول الثقوب تُحدَّب بالطريقة المعتادة. يتم ملء وخط "الجزر" داخل الثقوب، وهكذا.

خيارات التنسيق المدعومة:

|**الخاصية**|**الوصف**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|يحدد اللون والشفافية المعطاة للتعبئة.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- صلب - تعبئة صلبة</p><p>- لا يوجد - لا تقم بملء المضلع</p><p>- خطوط أفقية - نمط من الخطوط الأفقية.</p><p>- خطوط رأسية - نمط من الخطوط الرأسية.</p><p>- خطوط متقاطعة - يحدد الخطوط الأفقية والرأسية التي تتقاطع.</p><p>- خطوط قطرية للأمام - نمط من الخطوط على قطري من أعلى اليسار إلى أسفل اليمين.</p><p>- خطوط قطرية للخلف - نمط من الخطوط على قطري من أعلى اليمين إلى أسفل اليسار.</p><p>- خطوط قطرية متقاطعة - نمط من الخطوط القطرية المتقاطعة.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|يحدد اللون والشفافية المعطاة لخط الحدبة.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|يحدد كيفية رسم خطوط الرمز.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|يحدد عرض خط الحدبة.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|يحدد مصفوفة من المسافات التي تحدد أطوال الشرطات والمسافات المتبادلة في الخطوط المتقطعة.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|يحدد المسافة من بداية الخط إلى بداية نمط الشرطة.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>يحدد كيفية عرض الخطوط عند تقاطعات أجزاء الخط.</p><p>- Miter - زاوية حادة</p><p>- Round - زاوية مستديرة</p><p>- Bevel - زاوية قطرية</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|يحدد الإزاحة الأفقية من موقع النقطة إلى نقطة ارتكاز الشكل.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|يحدد الإزاحة الرأسية من موقع النقطة إلى نقطة ارتكاز الشكل.|

### **أنواع الهندسة**
` `يمكن تطبيق المُرمِّز على هندسات من أي نوع.

|**أبعاد الهندسة**|**أنواع الهندسة**|**سلوك العرض**|
| :-: | :-: | :-: |
|**نقطة**|نقطة، MultiPoint|يرسم مربعًا صغيرًا متعدد الأضلاع متعامد.|
|**خط**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|يتم إغلاق الخط للتعبئة عن طريق توصيل نقطة النهاية بنقطة البداية. يتم رسم الخط الأصلي فقط.|
|**سطح**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|يرسم المضلع.|

بالنسبة إلى GeometryCollections، يتم تحديد سلوك العرض بشكل منفصل لكل هندسة داخل المجموعة. تتبع الطبقات ذات النوع الهندسي المختلط منطق GeometryCollections.

استخدم MixedGeometrySymbolizer للحد من المُرمِّز لأنواع هندسية محددة.

### **أمثلة**
افتراضيًا، يرسم مُرمِّز التعبئة البسيط خط حدبة أسود وتعبئة بيضاء صلبة:



هنا كيفية تغيير النمط:




|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

-----
قد ترغب أيضًا في إضافة تسميات إلى المضلعات الخاصة بك. قم بزيارة [أمثلة تسمية الخطوط](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) للحصول على أمثلة حول كيفية تسمية حدود المضلعات أو [أمثلة تسمية النقاط](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) حول أمثلة حول كيفية تسمية مراكز المضلعات.
