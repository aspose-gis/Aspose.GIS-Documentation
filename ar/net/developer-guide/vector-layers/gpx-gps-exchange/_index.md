---
title: العمل مع ملفات تنسيق تبادل نظام تحديد المواقع العالمي GPX في C#
linktitle: GPX - تنسيق تبادل نظام تحديد المواقع العالمي
type: docs
url: /ar/net/gpx-gps-exchange/
weight: 60
description: تتيح لك مكتبة GIS الخاصة بـ C# فتح وقراءة الميزات من ملفات تنسيق تبادل نظام تحديد المواقع العالمي (GPX).
---

## **العمل مع ملفات تنسيق تبادل نظام تحديد المواقع العالمي (GPX)**
تتيح لك Aspose.GIS فتح وقراءة الميزات من ملفات تنسيق تبادل نظام تحديد المواقع العالمي (GPX).
## **قراءة الميزات من ملف GPX**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **قراءة الميزات لكل نقطة في الجزء**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **كتابة المضلعات كخطوط إلى ملف GPX**
لا يدعم تنسيق GPX المضلعات والمضلعات المتعددة. كنتيجة لذلك، قد يفشل التحويل في بعض الأحيان من تنسيقات أخرى. يجب عليك تطبيق خيار WritePolygonsAsLines لحل هذه المشكلة.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
