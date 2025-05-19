---
title: الرموز - واجهة برمجة تطبيقات GIS C#‎
linktitle: "الرموز"
type: docs
url: /ar/symbology/
weight: 10
description: تدعم مكتبة أو واجهة برمجة تطبيقات GIS C#‎ استخدام مُرمِّزات لرسم هندسة الميزات مثل العلامة والخط والتعبئة ودمج المُرمِّزات لإنشاء تصورات أكثر تعقيدًا.
---

المُرمِّز هو طريقة لرسم هندسة ميزة على الخريطة.

|** **|**المُرمِّز**|**فئة واجهة برمجة التطبيقات (API)**|**الوصف**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**علامة**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|يرسم شكلًا مُعرَّفًا مسبقًا بملء وتحديد قابلين للتخصيص. |
|![todo:image_alt_text](symbology_2.png)|**خط**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|يرسم خطًا بتصميم قابل للتخصيص.|
|![todo:image_alt_text](symbology_3.png)|**تعبئة**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|يملأ مضلعًا أو منطقة محددة بخط بتعبئة وسكتة قابلين للتخصيص.|
بالإضافة إلى المُرمِّزات التي تقوم بالرسم الفعلي، هناك عدد من المُرمِّزات الأخرى التي تسمح بدمج مُرمِّزات أخرى لإنشاء تصورات أكثر تعقيدًا.

|**المُرمِّز**|**فئة واجهة برمجة التطبيقات (API)**|**الوصف**|
| :- | :- | :- |
|**مُرمِّز طبقي**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|يرسم ميزة بعدة مُرمِّزات فوق بعضها البعض|
|**مُرمِّز هندسة مختلطة**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|يرسم الميزات من الطبقات التي تحتوي على هندسات من أنواع مختلطة بمُرمِّز معين لكل نوع هندسة|
|**مُرمِّز قائم على القواعد**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|يحدد مُرمِّزًا لتطبيقه على ميزة بالقواعد التي يحددها المستخدم.|
|**مُرمِّز تجميع العلامات**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|يرسم تجمعات من العلامات، وتجميع هذه العناصر.|
|**مُرمِّز مُنشئ الهندسة**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|يسمح باستبدال هندسة الميزة قبل العرض.|
|**مُرمِّز فارغ**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|لا يرسم أي شيء. مفيد عند دمجه مع مُرمِّزات أخرى، مثل المُرمِّز القائم على القواعد.|
