---
title: "كيفية ضم الطبقات باستخدام الهندسة أو السمة"
type: docs
url: /ar/net/how-to-join-layers
weight: 70
---

## ملخص

في نظم المعلومات الجغرافية (GIS)، تعتبر عمليات الضم آلية قوية لدمج المعلومات من طبقات مختلفة بناءً على سمة مشتركة أو علاقة مكانية. تسمح لك عمليات الضم بدمج بيانات السمة من طبقة واحدة (الطبقة المصدر) مع طبقة أخرى (الطبقة الهدف) باستخدام حقل مشترك أو موقع مكاني. الأول هو ضم البيانات عن طريق المفتاح (سمة في الجدول). باستخدام حقل مشترك، مثل مفتاح فريد، يمكنك ربط سجلات في جدول واحد بسجلات في جدول آخر. النهج الثاني هو ضم البيانات حسب الموقع (مكانيًا). نحن ندعم كلا النهجين ونقدم لك الفرصة لاستخدامهما اعتمادًا على احتياجاتك.

لنفترض أنك قد تلقيت بيانات تصف التغيير بالنسبة المئوية في عدد السكان للمقاطعات المختلفة، وتريد إنشاء عدة خرائط لنمو السكان بناءً على هذه المعلومات. بينما يتم تخزين بيانات السكان الخاصة بك في جدول في قاعدة البيانات الخاصة بك وتشارك حقلًا مشتركًا مع طبقتك، يمكنك ضم هذه البيانات إلى كائناتك الجغرافية واستخدام الحقول الإضافية للتسمية أو التصنيف أو الاستعلام أو تحليل كائنات الطبقة.

عادةً ما تقوم بإجراء عمليات ضم البيانات بناءً على قيمة حقل موجود في كلا الجدولين. لا يجب أن تتطابق أسماء الحقول بالضرورة، ولكن يجب أن تكون أنواع البيانات هي نفسها - أرقام مع أرقام وسلاسل نصية مع سلاسل نصية وما إلى ذلك. يمكنك تنفيذ عملية ضم البيانات باستخدام أداة المعالجة المسبقة "Add Join". عند ضم السمات، تتم إضافة الحقول التي تم ضمها ديناميكيًا إلى الجدول الحالي. يتم الحفاظ على خصائص الحقل مثل الأسماء والرؤية وتنسيق الأرقام عند إضافة أو إزالة الضم.

## القدرات للضم حسب حقل المفتاح

- يتيح لك هذا النهج **ربط سجلات من جداول مختلفة** بناءً على حقل مفتاح مشترك. يمكنك تحديد حقل المفتاح الذي سيتم استخدامه للمقارنة لتأسيس العلاقة بين السجلات. هذا مفيد بشكل خاص عندما تحتاج إلى دمج البيانات بناءً على معرف أو سمة فريدة أخرى.

تحديد الطريقة لمقارنة البيانات بناءً على حقل المفتاح:

- يمكنك تحديد **طرق مقارنة مختلفة** لحقل المفتاح عند دمج البيانات. على سبيل المثال، يمكنك اختيار الحصول على تطابق تام أو المقارنة بناءً على نمط أو ضمن نطاق من القيم. يسمح هذا بتحديد أكثر دقة للعلاقات بين السجلات ويمنحك التحكم في عملية دمج البيانات.

تحديد قائمة بأسماء السمات المراد دمجها:

- عند دمج البيانات، يمكنك تحديد **سمات محددة** يجب دمجها. يتيح لك ذلك اختيار السمات الضرورية فقط للدمج وإدارة هيكل الجدول الناتج.

## القدرات للضم باستخدام الهندسة

- يتيح لك هذا النهج ربط البيانات بناءً على **موقعها المكاني**. يمكنك تحديد نصف قطر بحث ضمنه سيتم البحث عن أقرب الكائنات الهندسية للدمج. هذا مفيد عندما تحتاج إلى ضم البيانات بناءً على موقعها الجغرافي.

التحكم في نصف قطر البحث للعثور على أقرب الكائنات الهندسية:

- يمكنك التحكم في **نصف قطر البحث** عند دمج البيانات بناءً على الموقع. عن طريق تحديد قيمة نصف القطر، تحدد المسافة التي سيتم فيها البحث عن أقرب الكائنات للدمج. يمنحك هذا التحكم في الكائنات التي ستشارك في عملية دمج البيانات بناءً على علاقتها المكانية.

## مشروع تجريبي

لفهم وظائف مكتبتنا بشكل أفضل، دعنا نفكر في [مثال لاستخدامه](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Layers.Join). يوضح هذا الرمز كيفية ضم الطبقات المتجهة بالسمات أو الهندسة.

يتكون الكود المقدم من طريقتين، JoinByIndex() و JoinByCoords()، اللتين توضحان عمليات ضم البيانات باستخدام فئة LayerConstructor.

في طريقة JoinByIndex():

- يتم إنشاء قوائم من الهندسيات مع السمات المرتبطة بها.

- تتم تهيئة كائن LayerConstructor.

- تنشئ الطريقة طبقة متجهة وطبقة هندسية باستخدام الهندسيات المتوفرة.

- يتم ضم الطبقة الهندسية بناءً على معرف فريد ("Id") باستخدام طريقة JoinLayersById().

- يتم إرجاع طبقة المتجهات المدمجة الناتجة.

في طريقة JoinByCoords():

- يتم إنشاء قوائم من الهندسيات مع السمات المرتبطة بها.

- تتم تهيئة كائن LayerConstructor.

- يتم إنشاء طبقات هندسية باستخدام الهندسيات المتوفرة.

- يتم ضم الطبقات الهندسية بناءً على الإحداثيات المطابقة باستخدام طريقة JoinLayersByCoords().

- يتم إرجاع طبقة المتجهات المدمجة الناتجة.

باختصار، توضح هاتان الطريقتان طريقتين مختلفتين لضم البيانات: واحدة تعتمد على معرف فريد والأخرى تعتمد على الإحداثيات المطابقة. تسهل فئة LayerConstructor عمليات ضم البيانات هذه.

## خيارات الضم للفهرس

توفر فئة JoinOptions مجموعة من الخيارات لتكوين ضم الطبقات. دعنا نتعمق أكثر في كل خيار:

- **JoinAttributeName**: يتيح لك هذا الخيار تحديد اسم السمة من الطبقة المدمجة التي سيتم استخدام قيمتها في مقارنة الشرط. إنه ينشئ اتصالاً بين الطبقتين بناءً على هذه السمة.

- **TargetAttributeName**: باستخدام هذا الخيار، يمكنك تحديد اسم السمة من الطبقة الرئيسية التي تتم مقارنتها بالسمة من الطبقة المدمجة. يساعد ذلك في تحديد الميزات المطابقة بين الطبقات.

- **JoinAttributeNames**: يتيح لك هذا الخيار تحديد قائمة بأسماء السمات التي تريد ضمها. إذا تركت هذه القائمة فارغة أو تم تعيينها على قيمة فارغة، فسيتم تضمين جميع السمات من الطبقة المدمجة في عملية الضم. ومع ذلك، عن طريق تحديد أسماء سمات محددة، يمكنك التحكم في السمات التي يتم ضمها، مما يمكن أن يكون مفيدًا لتحسين استخدام الذاكرة ووقت المعالجة.

- **ConditionComparer**: يتيح لك هذا الخيار تحديد منطق مخصص لمقارنة قيم السمات بين ميزات الطبقتين. بشكل افتراضي، يستخدم مقارن EqualityComparer.Default، الذي يتحقق من المساواة. ومع ذلك، يمكنك توفير مقارن مخصص خاص بك والذي ينفذ IEqualityComparer للحصول على متطلبات مقارنة أكثر تخصصًا.

- **JoinedAttributesPrefix**: يتيح لك هذا الخيار تحديد بادئة سلسلة لأسماء السمات للطبقة المدمجة. القيمة الافتراضية هي "joined_"، مما يعني أنه سيتم إضافة بادئة "joined_" إلى السمات التي تم ضمها في الطبقة المدمجة الناتجة. تساعد هذه البادئة في التمييز بين السمات التي تم ضمها والسمات الأصلية للطبقة الرئيسية.

توفر فئة JoinOptions مرونة وتحكمًا في جوانب مختلفة من عملية ضم الطبقات. يمكنك تحديد السمات المراد ضمها وتخصيص منطق المقارنة وتعريف بادئة للسمات المدمجة الناتجة. تمكنك هذه الخيارات من تخصيص عملية الضم وفقًا لاحتياجاتك الخاصة وتحقيق رؤى ذات مغزى من الطبقات المدمجة.

## خيارات الضم للهندسة

تمثل فئة **JoinByGeometryOptions** خيارات لضم الطبقات بناءً على الهندسة. دعنا نستكشف وظائف كل خيار:

- **Radius**: يحدد هذا الخيار نصف القطر ضمنه سيتم البحث عن الهندسة المدمجة. إنه يحدد التقارب الذي ستتم فيه مطابقة الميزات من الطبقة الرئيسية مع الميزات من الطبقة المدمجة بناءً على علاقتها المكانية.

- **ConditionComparer**: يتيح لك هذا الخيار تحديد منطق مخصص لمقارنة قيم السمات من ميزات الطبقتين. بشكل افتراضي، يستخدم EqualityComparer.Default، الذي يتحقق من المساواة. ومع ذلك، يمكنك توفير مقارن مخصص خاص بك والذي ينفذ IEqualityComparer للحصول على متطلبات مقارنة أكثر تحديدًا.

- **JoinedAttributesPrefix**: يتيح لك هذا الخيار تحديد بادئة سلسلة لأسماء السمات للطبقة المدمجة. القيمة الافتراضية هي "joined_"، مما يعني أنه سيتم إضافة بادئة "joined_" إلى السمات التي تم ضمها في الطبقة المدمجة الناتجة. تساعد هذه البادئة في التمييز بين السمات التي تم ضمها والسمات الأصلية للطبقة الرئيسية.

توفر فئة JoinByGeometryOptions الوسائل لتخصيص عملية ضم الطبقات بناءً على علاقتها المكانية. عن طريق تحديد نصف قطر البحث، يمكنك التحكم في مدى مطابقة الهندسات. يسمح هذا بضبط عملية الضم بناءً على التقارب المطلوب بين الميزات. يمنحك خيار توفير مقارن مخصص مرونة في مقارنة قيم السمات، ويساعدك خيار إضافة بادئة إلى السمات المدمجة في التمييز بينها في الطبقة المدمجة الناتجة.

باستخدام هذه الخيارات، يمكنك إجراء دمج بيانات مدرك مكانيًا والحصول على رؤى من الطبقات المدمجة التي تعتمد على قربها المكاني وقيم السمات.

## ملخص

تسمح آلية ضم البيانات في نظم المعلومات الجغرافية بدمج الكائنات الهندسية بسماتها المقابلة من طبقات مختلفة. يوفر هذا القدرة على تحليل واستخراج المعلومات بناءً على العلاقات المكانية والسمات داخل البيانات. تتيح الخيارات المتاحة تخصيص عملية الضم لتلبية المتطلبات واحتياجات التحليل المحددة في بيانات نظم المعلومات الجغرافية.

تسهل عمليات ضم البيانات مهامًا مختلفة، بما في ذلك:

- العثور على الكائنات التي تستوفي معايير مكانية محددة، مثل تحديد جميع المباني ضمن نصف قطر 500 متر من نقطة معينة.

- دمج البيانات الجغرافية لإنشاء نظرة عامة أكثر شمولاً وغنية بالمعلومات للوضع.

- تحليل قيم السمات للكائنات بناءً على ظروف مكانية محددة لتحديد الاتجاهات والأنماط.

تسمح خيارات ضم البيانات بتكوين دقيق لعملية مطابقة الكائنات. تتضمن هذه الخيارات تحديد السمات المراد ضمها وتحديد منطق مخصص لمقارنة قيم السمات وإضافة بادئة إلى أسماء سمات البيانات المدمجة. توفر هذه الخيارات مرونة وقابلية للتكيف مع عملية الضم، لتلبية الاحتياجات الخاصة وأهداف تحليل البيانات في نظم المعلومات الجغرافية.

يلعب آلية ضم البيانات دورًا مهمًا في دمج وتحليل البيانات الجغرافية، مما يؤدي إلى فهم أكثر شمولاً للطبيعة المكانية والسمات للكائنات قيد التحقيق.