---
title: "مُرمز تجميع العلامات"
type: docs
url: /ar/net/marker-cluster-symbolizer/
weight: 65
description: يسمح مُرمز تجميع العلامات في مكتبة أو واجهة برمجة تطبيقات GIS C# بتجميع العلامات ضمن مسافة محددة.
---

## **مُرمز تجميع العلامات**
يعد مُرمز تجميع العلامات أحد المُرمزات المتقدمة. فهو يسمح بتجميع العلامات ضمن المسافة المحددة.

في هذا المثال بلغة C#، قمنا برسم مراكز التجمعات كدوائر حمراء. أيضًا، قمنا برسم جميع نقاط التجمع المتداخلة باستخدام ألوان مختلفة. للقيام بذلك، استخدمنا وظيفة FeaturesBasedConfiguration، التي تقوم بإعداد نمط خاص لكل تجمع.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterMarkerSymbolizer.cs" >}}

إليك النتيجة:

![تجمع النقاط](points-cluster.png)

## **رسم إجمالي العناصر**

يعرض هذا المثال إجمالي عدد العناصر في التجمع.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterTextSymbolizer.cs" >}}

إليك النتيجة:

![تجمع الأرقام](digits-cluster.png)
