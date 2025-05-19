---
title: فیلتر کردن و فهرست‌بندی لایه‌های برداری GIS در C#
linktitle: فیلتر کردن و فهرست‌بندی
second_title: Aspose.GIS for .NET
type: docs
url: /fa/net/filtering-and-indexing/
weight: 30
description: با کتابخانه یا API GIS C#‎ .NET، می‌توانید لایه‌های برداری GIS را بر اساس مقادیر ویژگی یا حدود مکانی فیلتر کنید. همچنین می‌توانید از فهرست‌ها برای سرعت بخشیدن به فیلتر کردن و پرس‌وجوهای مکانی استفاده کنید.
---

با Aspose.GIS for .NET می‌توانید لایه‌ها را بر اساس مقادیر ویژگی یا حدود مکانی فیلتر کنید. همچنین می‌توانید از فهرست‌ها برای سرعت بخشیدن به فیلتر کردن و پرس‌وجوهای مکانی استفاده کنید.
## **فهرست ویژگی**
### **فیلتر بدون فهرست**
در اینجا نحوه فیلتر کردن یک لایه بر اساس مقادیر یک ویژگی آمده است:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **فیلتر با فهرست**
کد بالا تا زمانی که لایه فقط یک بار فیلتر شود خوب است. اما اگر احتمال دارد که لایه چندین بار پرس‌وجو شود، می‌توانیم از فهرست‌های ویژگی بهره ببریم. ایجاد فهرست ویژگی کمی زمان می‌برد، اما می‌توان آن را چندین بار برای سرعت بخشیدن به فیلتر کردن استفاده کرد.

مثال زیر از یک فایل فهرست ویژگی برای سرعت بخشیدن به فیلتر کردن لایه بر اساس مقادیر ویژگی استفاده می‌کند:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **ذخیره ویژگی‌های فیلتر شده**
ویژگی‌های فیلتر شده را می‌توان در لایه‌ها ذخیره کرد:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **رندر ویژگی‌های فیلتر شده**
همچنین می‌توان ویژگی‌های فیلتر شده را رندر کرد. مثال زیر از فهرست ویژگی برای انتخاب سریع تمام ویژگی‌هایی با جمعیت بیشتر از 2000 و افزودن آنها به نقشه استفاده می‌کند:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **فهرست مکانی**
فهرست‌های مکانی برای سرعت بخشیدن به پرس‌وجوهای مکانی استفاده می‌شوند. درست مانند فهرست‌های ویژگی، فهرست‌های مکانی پس از ایجاد دوباره استفاده می‌شوند.
### **یافتن ویژگی‌های نزدیک‌ترین به نقطه**
در اینجا نحوه استفاده از فهرست مکانی برای سرعت بخشیدن به یافتن ویژگی نزدیک‌ترین به یک نقطه آمده است:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **انتخاب ویژگی‌هایی که با هندسه تلاقی می‌کنند**
مثال زیر از فهرست مکانی برای سرعت بخشیدن به انتخاب ویژگی‌هایی که با هندسه تلاقی می‌کنند استفاده می‌کند:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
