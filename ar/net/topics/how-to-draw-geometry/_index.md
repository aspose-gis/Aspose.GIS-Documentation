---
title: "كيفية رسم هندسة على الخريطة"
type: docs
url: /ar/net/how-to-draw-geometry
weight: 70
---

لإنشاء وعرض الأشكال الهندسية على الخريطة، تحتاج إلى البدء بـ **إنشاء كائن هندسي**. هناك طريقتان يمكنك استخدامهما:

- **منشئ لكل نوع من أنواع الميزات الهندسية**
تتضمن هذه الطريقة استخدام مُنشئ مخصص لكل نوع من أنواع الميزات الهندسية. على سبيل المثال، لإنشاء نقطة، ستستخدم الكود التالي:

```
Point point = new Point(40.7128, -74.006);
```

ومع ذلك، يمكن أن تصبح هذه الطريقة صعبة ومعقدة للإدارة عند إنشاء كائنات معقدة مثل الخطوط المتعددة أو المجموعات. نتيجة لذلك، قد يحتاج المطور إلى إضافة العديد من سطور التعليمات البرمجية، مما يتسبب في انخفاض قابلية قراءة الكود. يمكن أن يكون ضمان سلامة البيانات أثناء التهيئة أمرًا صعبًا أيضًا. على سبيل المثال، ضع في اعتبارك المثال التالي الذي ينشئ مضلعًا به ثقب بداخله:

```
Polygon polygon = new Polygon();

LinearRing ring = new LinearRing();
ring.AddPoint(50.02, 36.22);
ring.AddPoint(49.99, 36.26);
ring.AddPoint(49.97, 36.23);
ring.AddPoint(49.98, 36.17);
ring.AddPoint(50.02, 36.22);

LinearRing hole = new LinearRing();
hole.AddPoint(50.00, 36.22);
hole.AddPoint(49.99, 36.20);
hole.AddPoint(49.98, 36.23);
hole.AddPoint(50.00, 36.24);
hole.AddPoint(50.00, 36.22);

polygon.ExteriorRing = ring;
polygon.AddInteriorRing(hole);
```

عيب آخر لهذه الطريقة هو عدم وجود توحيد للبيانات للتهيئة. لا يمكنك إنشاء مستودع من الثوابت أو الملفات داخل مشروعك.

- **WKT (نص معروف جيدًا)**
تتضمن هذه الطريقة إنشاء هندسة من WKT (نص معروف جيدًا)، والذي يوفر طريقة قياسية لإنشاء أشكال هندسية. يوضح الكود التالي كيفية إنشاء نقطة وخط:

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

في حين أن هذا النهج قد يقلل الأداء قليلاً بسبب الحاجة إلى تحليل السلسلة، إلا أنه يبسط إنشاء كائنات أكثر تعقيدًا.

يمكنك العثور على مزيد من التفاصيل حول WKT في المقالة التالية: "تصدير واستيراد البيانات من/إلى WKT و WKB."

عرض الأشكال الهندسية على الخريطة
بمجرد إنشاء شكل هندسي، فإن الخطوة التالية هي عرضه على الخريطة. بينما يمكن للخريطة عرض طبقات محملة من مصادر وتنسيقات مختلفة، فإن InMemoryLayer عبارة عن طبقة لا تتطلب مصدرًا.

**لعرض الشكل الهندسي الخاص بك**، يمكنك إنشاء InMemoryLayer وإضافة الكائن إليه:

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

الآن يمكنك **عرض هذه الطبقة على الخريطة وإنشاء ملف بأحد التنسيقات المدعومة**، مثل SVG، باستخدام الكود التالي:

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

بمجرد إضافة الطبقة وعرضها على الخريطة، يمكنك حفظها بأي من التنسيقات المدعومة. في هذا المثال، تم اختيار تنسيق SVG لتجنب المشكلات المحتملة مع دعم Bitmap. من المهم ملاحظة أن Net 6.0 لديه دعم محدود لـ Bitmap، مما قد يؤدي إلى قيود مثل عدم القدرة على عرض صور Bitmap باستخدام Blazor WebAsm على جانب العميل. لذلك، عند اختيار تنسيق لحفظ الخريطة الخاصة بك، من المهم مراعاة قيود النظام الأساسي المستهدف واختيار تنسيق متوافق معه.

تشرح المقالة كيفية إنشاء وعرض الأشكال الهندسية على الخريطة بأسلوب افتراضي وبسيط. ومع ذلك، تقدم مكتبة Aspose مجموعة واسعة من خيارات التنسيق التي يمكن تخصيصها لتناسب احتياجاتك. لاستكشاف هذه الخيارات، نوصي بالرجوع إلى [وثائق Aspose.MapRendering]( https://docs.aspose.com/gis/net/map-rendering/) ، والتي توفر معلومات مفصلة حول كيفية استخدام تقنيات التنسيق المختلفة لتعزيز المظهر المرئي للخريطة الخاصة بك.

**باختصار**، لإنشاء أشكال هندسية على الخريطة، يمكنك استخدام إما مُنشئ لكل نوع من أنواع الميزات الهندسية أو إنشاء هندسة من WKT. لعرض الكائن، ضعه على طبقة واعرض الطبقة على الخريطة بأسلوب الخريطة الافتراضي. احفظ الخريطة بتنسيق مدعوم، مثل SVG، واستخدم مكتبتنا لاستكشاف خيارات التنسيق. بالإضافة إلى ذلك، توفر مكتبتنا فرصة لرؤية مثال مكتمل بالنقر فوق [الرابط]( https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer) المتوفر في الوثائق، والذي يمكن أن يساعدك على فهم كيفية تنفيذ هذه التقنيات في مشاريعك الخاصة.
