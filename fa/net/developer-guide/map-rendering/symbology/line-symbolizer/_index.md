---
title: "نماد خط"
type: docs
url: /fa/net/line-symbolizer/
weight: 20
description: کتابخانه یا API# GIS C از نماد خط ساده برای هندسه‌های یک بعدی خطوط پشتیبانی می‌کند و می‌تواند بر روی هندسه‌های هر نوعی مانند نقطه، خط، سطح اعمال شود.
---

## **نماد خط**
نماد خط ساده یک خط با سبک قابل تنظیم رسم می کند. این نماد پیش‌فرض برای هندسه‌های یک بعدی (خطوط) است.

گزینه‌های سبک پشتیبانی شده:

|**ویژگی**|**توضیحات**|
| :- | :- |
|[Color](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|رنگ و شفافیت داده شده به خط را مشخص می کند.|
|[Width](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|عرض خط را مشخص می‌کند|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|تعیین می کند که چگونه خطوط در تقاطع قطعات خط رسم شوند.|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|نحوه ترسیم کار خطی نماد را مشخص می‌کند.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|آرایه‌ای از فاصله‌ها را مشخص می‌کند که طول‌های تناوبی خطوط و فواصل در خطوط نقطه چین را تعیین می‌کنند.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|فاصله از شروع یک خط تا شروع الگوی خط چین را مشخص می‌کند.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>نحوه ترسیم خطوط در انتهای آنها را مشخص می کند.</p><p>- Butt - لبه مربع تیز</p><p>- Round - لبه گرد</p><p>- Square - لبه مربع کمی کشیده</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|انحراف از خط اصلی را مشخص می کند. برای فاصله مثبت، انحراف در سمت چپ خط ورودی (نسبت به جهت خط) خواهد بود. برای فاصله منفی، در سمت راست خواهد بود.|

### **نوع هندسه**
` `نماد را می‌توان بر روی هندسه‌های هر نوعی اعمال کرد.

|**بعد هندسه**|**انواع هندسه**|**رفتار رندرینگ**|
| :-: | :-: | :-: |
|**نقطه**|Point, MultiPoint|یک خط با طول کوچک با جهت افقی در مرکز نقطه رسم می کند، با دو کلاهک انتهایی.|
|**خط**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|خط را رسم می‌کند.|
|**سطح**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|خارجی بسته هندسه به عنوان رشته خط استفاده می شود (بدون کلاهک انتهایی)|

برای GeometryCollections، رفتار رندرینگ به طور جداگانه برای هر هندسه در داخل مجموعه تعیین می‌شود. لایه‌های با نوع هندسه ترکیبی از منطق برای GeometryCollections پیروی می‌کنند.

از MixedGeometrySymbolizer برای محدود کردن یک نمادگر به انواع هندسه خاص استفاده کنید.

### **مثال ها**
به طور پیش فرض، نماد خط خطوط سیاه را رسم می کند:




اینجا نحوه تغییر رنگ خط به آبی است:



|![todo:text_alt](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

برای سناریوهای پیشرفته تر، ممکن است بخواهید سبک خط را به صورت پویا بر اساس مقادیر ویژگی تنظیم کنید. در اینجا نحوه انجام آن آمده است:



|![todo:text_alt](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |



همچنین ممکن است بخواهید برچسب‌هایی به خطوط خود اضافه کنید. برای مثال‌ها از [مثال‌های برچسب‌گذاری خطوط](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) بازدید کنید.
