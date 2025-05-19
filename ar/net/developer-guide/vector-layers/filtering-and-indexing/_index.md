---
title: تصفية وفهرسة طبقات المتجهات الجغرافية في C#
linktitle: التصفية والفهرسة
second_title: Aspose.GIS for .NET
type: docs
url: /ar/net/filtering-and-indexing/
weight: 30
description: باستخدام مكتبة أو واجهة برمجة تطبيقات GIS C#‎ .NET، يمكنك تصفية طبقات المتجهات الجغرافية حسب قيم السمات أو الحدود المكانية. يمكنك أيضًا استخدام الفهارس لتسريع التصفية والاستعلامات المكانية.
---

باستخدام Aspose.GIS for .NET يمكنك تصفية الطبقات حسب قيم السمات أو الحدود المكانية. يمكنك أيضًا استخدام الفهارس لتسريع التصفية والاستعلامات المكانية.
## **فهرس السمات**
### **تصفية بدون فهرس**
إليك كيفية تصفية طبقة حسب قيم سمة:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **تصفية باستخدام فهرس**
الكود أعلاه جيد طالما أن الطبقة تتم تصفيتها مرة واحدة فقط. ولكن، إذا كان من المحتمل الاستعلام عن الطبقة عدة مرات، يمكننا الاستفادة من فهارس السمات. يستغرق بناء فهرس السمات بعض الوقت، ولكنه يمكن إعادة استخدامه عدة مرات لتسريع التصفية.

يستخدم المثال التالي ملف فهرس سمات لتسريع تصفية الطبقة حسب قيم السمة:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **حفظ الميزات التي تمت تصفيتها**
يمكن حفظ الميزات التي تمت تصفيتها في طبقات:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **عرض الميزات التي تمت تصفيتها**
من الممكن أيضًا عرض الميزات التي تمت تصفيتها. يستخدم المثال التالي فهرس السمات لتحديد جميع الميزات التي يزيد عدد سكانها عن 2000 بسرعة وإضافتها إلى الخريطة:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **الفهرس المكاني**
تستخدم الفهارس المكانية لتسريع الاستعلامات المكانية. مثل فهارس السمات، تتم إعادة استخدام الفهارس المكانية بعد إنشائها.
### **العثور على الميزات الأقرب إلى نقطة**
إليك كيفية استخدام الفهرس المكاني لتسريع البحث عن الميزة الأقرب إلى نقطة ما:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **تحديد الميزات التي تتقاطع مع هندسة**
يستخدم المثال التالي فهرسًا مكانيًا لتسريع تحديد الميزات التي تتقاطع مع الهندسة:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
