---
title: "محرف المؤشر"
type: docs
url: /ar/net/marker-symbolizer/
weight: 10
description: مكتبة أو واجهة برمجة تطبيقات GIS C# تدعم محرف مؤشر بسيط يرسم شكلاً مُعرَّفًا مسبقًا مع تعبئة ومخطط تفصيلي قابلين للتخصيص على هندسات من أي نوع مثل النقطة والخط والسطح.
---

## **محرف المؤشر**
يرسم محرف المؤشر البسيط شكلًا مُعرَّفًا مسبقًا مع تعبئة ومخطط تفصيلي قابلين للتخصيص. هذا هو المحرف الافتراضي للهندسات ذات الأبعاد الصفرية (النقاط).

الأشكال المدعومة هي:

|![todo:image_alt_text](marker-symbolizer_1.png)|دائرة| |![todo:image_alt_text](marker-symbolizer_2.png)|نجمة|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|مربع| |![todo:image_alt_text](marker-symbolizer_4.png)|صليب|
|![todo:image_alt_text](marker-symbolizer_5.png)|مثلث| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

خيارات التنسيق المدعومة:

|**خاصية**|**الوصف**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|يحدد شكل المؤشر.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|يحدد حجم شكل المؤشر|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|يحدد اللون والشفافية المعطاة للتعبئة|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|يحدد اللون والشفافية المعطاة للخط|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|يحدد عرض الخط|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|يحدد كيفية عرض الخطوط عند تقاطعات أجزاء الخط.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|يحدد كيف يجب رسم خط عمل الرمز.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|يحدد مصفوفة من المسافات التي تحدد أطوال الشرطات والمسافات المتبادلة في الخطوط المتقطعة.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|يحدد المسافة من بداية الخط إلى بداية نمط الشرطة.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|يحدد دوران الرمز حول نقطة مركزه، بالدرجات العشرية. تشير القيم الموجبة إلى الدوران في اتجاه عقارب الساعة، وتشير القيم السالبة إلى الدوران عكس اتجاه عقارب الساعة. الافتراضي هو 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|يحدد الإزاحة الأفقية من موقع النقطة إلى نقطة ارتكاز الشكل.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|يحدد الإزاحة الرأسية من موقع النقطة إلى نقطة ارتكاز الشكل.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|يحدد أي جانب من شكل المؤشر سيتم محاذاته أفقيًا مع موقع النقطة.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|يحدد أي جانب من شكل المؤشر سيتم محاذاته رأسيًا مع موقع النقطة.|

### **أنواع الهندسة**
يمكن تطبيق المحرف على هندسات من أي نوع.

|**أبعاد الهندسة**|**أنواع الهندسة**|**سلوك العرض**|
| :-: | :-: | :-: |
|**نقطة**|نقطة، متعدد النقاط|يرسم الشكل في منتصف إحداثيات النقطة.|
|**خط**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>يرسم الشكل في منتصف مركز ثقل الهندسة</p><p> </p>|
|**سطح**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

بالنسبة إلى GeometryCollections، يتم تحديد سلوك العرض بشكل منفصل لكل هندسة داخل المجموعة. تتبع الطبقات ذات النوع المختلط للهندسة منطق GeometryCollections.

استخدم MixedGeometrySymbolizer للحد من المحرف لأنواع هندسة محددة.

### **أمثلة**
بشكل افتراضي، يرسم محرف المؤشر دوائر سوداء:



هنا كيفية تغيير لون التعبئة إلى اللون الأحمر:



|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

مثال آخر للتنسيق باستخدام شكل مُعرَّف مسبقًا (مثلث):



|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----

للحصول على سيناريوهات متقدمة، قد ترغب في تعديل نمط المؤشر ديناميكيًا بناءً على قيم سمات الميزة. إليك كيفية القيام بذلك:



|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
قد ترغب أيضًا في إضافة تسميات إلى المؤشرات الخاصة بك. قم بزيارة [أمثلة تسمية النقاط](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) للحصول على أمثلة.
