---
title: "Optimal Path Finder"
type: docs
url: /ar/net/optimal-path-finder
weight: 70
---

## ملخص

إن البحث عن أقصر مسار على شبكة طرق هو عملية تحليل تهدف إلى تحديد الطريقة الأكثر كفاءة للسفر بين النقاط على الخريطة. يمكن أن تكون هذه الأداة مفيدة في إنشاء مسارات مثالية مع توقفات متعددة أو قياس المسافة ووقت السفر بين المواقع المختلفة. مع كل مكالمة، يمكن لتقنيتنا العثور على مسارات مثالية لمركبة واحدة أو عدة مركبات. على سبيل المثال، يمكن أن تساعد السائقين في العثور على المسارات المثلى لتوصيل البضائع أو تحديد مسافة التنقل المثالية من المنزل إلى العمل للركاب المختلفين.

## قدرات الخوارزمية

توفر مكتبتنا القدرة على بناء **أكثر مسار مثالي بين نقطتين** على الخريطة. لديها الميزات الرئيسية التالية:

1. البحث عن المسار الأمثل على الخريطة، مع مراعاة المسارات والعقبات: نأخذ في الاعتبار ليس فقط الطرق ولكن أيضًا المسارات الوعرة مثل الممرات والممرات للمشاة والعقبات التي قد تؤثر على اختيار المسار الأمثل.

2. البحث عن المسار الأمثل على الطرق فقط: إذا كنت بحاجة إلى العثور على مسار حصريًا على الطرق، فإننا نوفر هذه الإمكانية. هذا مفيد ، على سبيل المثال ، للمركبات المقيدة بالسفر على الطرق فقط.

3. تحديد سرعات مختلفة للطرق: لدينا القدرة على تعيين سرعات مختلفة للطرق المختلفة. على سبيل المثال، يمكن تعيين سرعات أعلى للطرق السريعة الرئيسية وسرعات أقل للحارات الضيقة.

4. تحديد عقبات مستطيلة: يمكنك تحديد عقبات مستطيلة على الخريطة يجب أخذها في الاعتبار عند بناء المسار الأمثل. هذا مفيد عندما تكون هناك عقبات معروفة مثل المباني أو البحيرات (تقريبها).

5. الحد من نصف قطر البحث للطرق: يمكنك تقييد نصف قطر البحث للطرق لتقليل وقت البحث والتركيز فقط على منطقة معينة.

6. التحكم في الأداء والدقة: نحن نوفر القدرة على التحكم في أداء ودقة الخوارزمية. يمكنك ضبطه لتحقيق التوازن المطلوب بين سرعة البحث ودقة بناء المسار.

بعد ذلك، سنقدم وصفًا أكثر تفصيلاً لكل من هذه الميزات ونفحص أمثلة لتطبيقاتها.

## النهج نحو الحل

على الرغم من أن إيجاد المسار مهمة غير تافهة، إلا أن هناك العديد من الخوارزميات الجيدة والموثوقة المعترف بها في مجتمع التطوير.

في تطبيقنا، استخدمنا خوارزمية Lee المعدلة. لدينا شبكة من الخلايا على المستوى. من نقطة البداية، تنتشر موجة في 8 اتجاهات (بما في ذلك الأقطار) إلى الخلايا المجاورة، وحساب الوقت اللازم للوصول إلى كل منها. قد تحتوي خلية مجاورة على عقبة أو طريق. يمكن أن يكون للطرق معاملات سرعة مختلفة. وبالتالي ، "نضع علامة" على شبكتنا بالوقت الذي يستغرقه الوصول إلى كل خلية من خلية البداية ضمن نصف قطر معين أو حتى الوصول إلى نقطة الهدف. إذا وصلنا إلى نقطة الهدف، فإننا نبني مسارًا عكسيًا باستخدام شبكتنا.

لتحديد المسار الأمثل على شبكة الطرق، يجب اتخاذ عدة خطوات. أولاً ، تحتاج إلى تحديد الطرق وتحديد سرعة الحركة عليها. يجب عليك أيضًا مراعاة وجود عقبات اصطناعية وطبيعية قد تؤثر على اجتياز المسار. بعد ذلك ، تحتاج إلى تحديد نقاط البداية والهدف للبحث. بمجرد الانتهاء من هذه الخطوات الأولية، يمكنك المتابعة لإيجاد المسار الفعلي. ستكون النتيجة مسارًا ممثلاً كمجموعة من إحداثيات النقاط.

من المهم ملاحظة أن المسار الأمثل قد يعتمد على وضع النقل المختار ، حيث قد تختلف سرعة الحركة ومجموعة العقبات. لذلك ، يجب استخدام مجموعات طرق وعقبات مختلفة لكل نوع من أنواع النقل عند البحث عن المسار الأمثل.

## مشروع تجريبي على GitHub

لفهم وظائف مكتبتنا بشكل أفضل، دعنا نفكر في [مثال لاستخدامه](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths). يوضح هذا الرمز كيفية إعداد الطرق والعقبات في خوارزمية إيجاد المسار والعثور على المسار الأمثل.

يتكون المثال من الخطوات التالية:

1. إنشاء قائمة بمعلومات الطريق (RoadInfo) ، والتي تتضمن معلومات حول قطعة الطريق (Segment) وسرعة الحركة (Velocity).
2. إضافة طرق سريعة إلى القائمة.
3. إضافة حلقات بطيئة إلى القائمة.
4. إنشاء مولد طبقة الطرق (WayLayerGenerator) وإضافة الطرق إلى المولد.
5. البحث عن مسارات متعددة من نقطة البداية (startPoint) إلى نقاط الهدف (goalPoint01 ، goalPoint02 ، goalPoint03) باستخدام نصف القطر المحدد (radius).
6. إعداد طبقة الطرق (roadsLayer) للعرض على الخريطة وإضافة كائنات الطريق.
7. إعداد طبقة الطريقة (wayLayer) للعرض على الخريطة وإنشاء كائنات هندسية لكل مسار تم العثور عليه.
8. [عرض الخريطة](https://docs.aspose.com/gis/net/how-to-draw-geometry/) باستخدام وظيفة ShowMap ، وحفظ الخريطة في المسار المحدد.

يبني هذا الرمز ويعرض مسارات الطرق على الخريطة للنقاط المحددة باستخدام معلومات الطريق ومولد طبقة الطريقة.

## خيارات البحث

يتم إجراء إيجاد المسار باستخدام فئة **WayLayerGenerator** الموجودة في مساحة اسم Aspose.Gis.GeoTools.WayAnalyzer.

تحتوي فئة WayLayerGenerator على طريقة **FindTheWay** للعثور على المسار من نقطة البداية إلى الهدف. لإنشاء مثيل لفئة WayLayerGenerator ، فإننا نمرر WayOptions كمعلمات (جميع المعلمات اختيارية):

- StartPoint: نقطة البداية

- GoalPoint: نقطة الهدف

- Radius: نصف قطر البحث

- Scale: مقياس الشبكة

- IsMoveOnlyRoad: ما إذا كان سيتم البحث عن المسار على الطرق فقط

الميزة الملحوظة هنا هي معلمة Scale. إذا تم تحديدها في المُنشئ، فإننا نثبت مقياسًا ثابتًا للبحث اللاحق. إذا لم يتم تعيين معلمة Scale ولكن تم تعيين StartPoint و GoalPoint ، فإننا نحسب المقياس على أنه المسافة بين نقطتي البداية والهدف مقسومة على 100. في جميع الحالات الأخرى، تكون القيمة الافتراضية لـ Scale هي 1. بالنسبة للمستخدمين ذوي الخبرة، من الأفضل تعيين Scale أو تعيين StartPoint و GoalPoint مباشرة لتمثيل الطرق والعقبات بكفاءة أكبر على الشبكة (خاصة إذا كان هناك الكثير منها).

لاستخدام طريقة FindTheWay ، نحتاج إلى تحديد نقطتي البداية والهدف. يمكننا أيضًا تعيين نصف قطر البحث (المسافة التي تنتشر إليها الموجة). بشكل افتراضي، يتم حساب نصف القطر على أنه المسافة بين نقطتي البداية والهدف مضروبة في 3. يمكن أن تكون نقاط البداية والهدف قريبة أو بعيدة جدًا عن بعضها البعض ، لذلك بناءً على المسافة بينهما ، نحسب مقياس شبكتنا. إذا لم يتطابق المقياس الحالي مع المقياس السابق، فإننا نعيد حساب الشبكة. يمكن تثبيت المقياس باستخدام معلمة Scale. في هذه الحالة ، لا يتم حسابه ، ولا تتم إعادة حساب الشبكة.

قبل بدء البحث ، نحتاج إلى تحديد خريطة الطريق والعقبات باستخدام طريقتي AddRoad و AddBlock المقابلتين لفئة WayLayerGenerator.

بالنسبة لطريقة **AddRoad** ، نحتاج إلى تحديد:

- startPoint: نقطة بداية الطريق

- endPoint: نقطة نهاية الطريق

- velocity: سرعة الحركة على الطريق

بالنسبة لطريقة **AddBlock** ، نحتاج إلى تحديد:

- x: إحداثي x للزاوية العلوية اليسرى للكتلة

- y: إحداثي y للزاوية العلوية اليسرى للكتلة

- sizeX: الحجم في المحور x

- sizeY: الحجم في المحور y

تسمح لنا هذه الطرق بتحديد خريطة الطريق والعقبات قبل بدء عملية إيجاد المسار.

## أمثلة التعليمات البرمجية

فيما يلي بعض الأمثلة على التعليمات البرمجية التي توضح كيفية إعداد الطرق والعقبات في خوارزمية إيجاد المسار والعثور على المسار الأمثل.

مثال 1: العثور على مسار بين نقطتي البداية والهدف.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**مثال 2**: تعيين معلمة المقياس ووجود إحداثيات سالبة للنقطة.

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**مثال 3**: تعيين معلمة IsMoveOnlyRoad ونصف قطر البحث.

```
WayOptions mapGeneratorOptions = new WayOptions();
mapGeneratorOptions.IsMoveOnlyRoad = true;
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddRoad(new Point(100, 100), new Point(140, 150), 10);
generator.AddRoad(new Point(140, 150), new Point(190, 100), 10);
Point startPoint = new Point(100, 100);
Point goalPoint = new Point(190, 100);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 100);
```

**مثال 4**: تعيين معلمة المقياس للبحث الأسرع.

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**مثال 5**: مثال بحث متعدد.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddBlock(200, 1700, 1500, 100, 0);
generator.AddBlock(1700, 200, 100, 1600, 0);
generator.AddBlock(200, 200, 1500, 100, 0);
generator.AddRoad(new Point(1000, 1150), new Point(200, 600), 10);
generator.AddRoad(new Point(50, 450), new Point(150, 1850), 10);

Point startPoint = new Point(1000, 1000);
Point goalPoint = new Point(1900, 1000);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 3500);

Point startPoint = new Point(50, 50);
Point goalPoint = new Point(70, 70);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

تبني هذه الأمثلة على التعليمات البرمجية وتعرض مسارات الطرق على الخريطة للنقاط المحددة ، باستخدام معلومات الطريق ومولد طبقة الطريقة.

**باختصار**، يعد إيجاد المسار الأمثل أداة قوية لتحليل شبكات الطرق وتحديد أكثر المسارات كفاءة بين النقاط على الخريطة. يأخذ في الاعتبار عوامل مختلفة مثل أنواع الطرق والعقبات وسرعات مختلفة لحساب المسار الأمثل. مع القدرة على البحث عن مسارات على كل من الطرق والمسارات الوعرة ، بالإضافة إلى التحكم في نصف قطر البحث وضبط الأداء والدقة ، يوفر هذا الخوارزمية حلاً متعدد الاستخدامات لتحسين المسار. من خلال النظر في أوضاع النقل المختلفة وتعديل مجموعات الطرق والعقبات وفقًا لذلك ، يمكن استخدامه في سيناريوهات مختلفة مثل تخطيط التسليم أو تحسين التنقل.