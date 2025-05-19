---
title: "نمایشگر خوشه مارکر"
type: docs
url: /fa/net/marker-cluster-symbolizer/
weight: 65
description: نمایشگر خوشه مارکر در کتابخانه یا API# C GIS امکان خوشه‌بندی نشانگرها را در فاصله مشخص فراهم می‌کند.
---

## **نمایشگر خوشه مارکر**
نمایشگر خوشه مارکر یکی از نمادپردازهای پیشرفته است. این امکان را فراهم می‌کند تا نشانگرها در فاصله مشخص خوشه‌بندی شوند.

در این مثال #C، مراکز خوشه را به صورت دایره‌های قرمز رسم کرده‌ایم. همچنین، تمام نقاط خوشه تو در تو را با استفاده از رنگ‌های مختلف رسم کرده‌ایم. برای انجام این کار، از تابع FeaturesBasedConfiguration استفاده کردیم که سبک خاصی را برای هر خوشه تنظیم می‌کند.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterMarkerSymbolizer.cs" >}}

در اینجا نتیجه آمده است:

![خوشه نقاط](points-cluster.png)

## **رسم تعداد کل آیتم‌ها**

این نمونه تعداد کل آیتم‌های موجود در خوشه را نمایش می‌دهد.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterTextSymbolizer.cs" >}}

در اینجا نتیجه آمده است:

![خوشه ارقام](digits-cluster.png)
