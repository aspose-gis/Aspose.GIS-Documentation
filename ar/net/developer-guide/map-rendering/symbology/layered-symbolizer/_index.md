---
title: "مُرمِّز مُتَعدِّد الطبقات"
type: docs
url: /ar/net/layered-symbolizer/
weight: 40
description: يقوم المُرمِّز المتعدد الطبقات في مكتبة GIS C# API برسم ميزة باستخدام عدة مرمِّزات فوق بعضها البعض مع أوضاع ترتيب العرض بناءً على الميزات أو الطبقات.
---

## **مُرمِّز مُتَعدِّد الطبقات**
يقوم المُرمِّز المتعدد الطبقات برسم ميزة باستخدام عدة مرمِّزات فوق بعضها البعض. يمكنك الاختيار من بين وضعين لترتيب العرض:

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - ارسم الميزة الأولى بجميع المُرمِّزات المضافة إلى المُرمِّز المتعدد الطبقات، ثم تابع رسم الميزة التالية.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - ارسم جميع الميزات باستخدام المُرمِّز الأول، ثم ارسم جميع الميزات باستخدام المُرمِّز التالي.

### **العرض حسب الميزات**

### **العرض حسب الطبقات**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
