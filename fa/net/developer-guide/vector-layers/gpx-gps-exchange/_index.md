---
title: کار با فایل‌های فرمت تبادل GPS (GPX) در C#
linktitle: GPX - فرمت تبادل GPS
type: docs
url: /fa/net/gpx-gps-exchange/
weight: 60
description: کتابخانه GIS سی شارپ به شما امکان می‌دهد ویژگی‌ها را از فایل‌های تبادل GPS (GPX) باز کرده و بخوانید.
---

## **کار با فایل‌های فرمت تبادل GPS (GPX)**
Aspose.GIS به شما امکان می‌دهد ویژگی‌ها را از فایل‌های تبادل GPS (GPX) باز کرده و بخوانید.
## **خواندن ویژگی‌ها از فایل GPX**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **خواندن ویژگی‌ها برای هر نقطه در سگمنت**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **نوشتن چند ضلعی‌ها به عنوان خطوط در فایل GPX**
فرمت GPX از چندضلعی‌ها و چندضلعی‌های متعدد پشتیبانی نمی‌کند. در نتیجه، گاهی اوقات تبدیل از فرمت‌های دیگر با شکست مواجه می‌شود. برای حل این مشکل باید گزینه WritePolygonsAsLines را اعمال کنید.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
