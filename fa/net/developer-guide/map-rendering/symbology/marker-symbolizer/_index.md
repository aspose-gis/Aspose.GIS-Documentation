---
title: "نمادگر نشانگر"
type: docs
url: /fa/net/marker-symbolizer/
weight: 10
description: کتابخانه یا API#GIS C  از نمادگر نشانگر ساده پشتیبانی می‌کند که یک شکل از پیش تعریف شده را با پر کردن و حاشیه قابل تنظیم بر روی هندسه‌ها از هر نوع مانند نقطه، خط، سطح ترسیم می‌کند.
---

## **نمادگر نشانگر**
نمادگر نشانگر ساده یک شکل از پیش تعریف شده را با پر کردن و حاشیه قابل تنظیم ترسیم می‌کند. این نمادگر پیش‌فرض برای هندسه‌های 0 بعدی (نقاط) است. 

شکل‌های پشتیبانی‌شده عبارتند از:

|![todo:image_alt_text](marker-symbolizer_1.png)|دایره| |![todo:image_alt_text](marker-symbolizer_2.png)|ستاره|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|مربع| |![todo:image_alt_text](marker-symbolizer_4.png)|ضربدر|
|![todo:image_alt_text](marker-symbolizer_5.png)|مثلث| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

گزینه‌های استایل پشتیبانی‌شده:

|**خاصیت**|**توضیحات**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|شکل نشانگر را مشخص می‌کند.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|اندازه شکل نشانگر را مشخص می‌کند|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|رنگ و شفافیت داده شده به پر کردن را مشخص می‌کند|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|رنگ و شفافیت داده شده به خط را مشخص می‌کند|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|عرض خط را مشخص می‌کند|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|تعیین می‌کند که چگونه خطوط در تقاطع قطعات خط رندر می‌شوند.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|نحوه رسم کار خطی نماد را مشخص می‌کند.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|آرایه‌ای از فاصله‌ها را مشخص می‌کند که طول‌های تناوبی خطوط و فواصل در خطوط نقطه‌چین را تعیین می‌کنند.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|فاصله از شروع یک خط تا شروع الگوی خط چین را مشخص می‌کند.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|چرخش نماد در اطراف نقطه مرکزی آن را به صورت درجه اعشاری مشخص می‌کند. مقادیر مثبت نشان‌دهنده چرخش در جهت عقربه‌های ساعت و مقادیر منفی نشان‌دهنده چرخش خلاف جهت عقربه‌های ساعت هستند. مقدار پیش‌فرض 0 است.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|انحراف افقی از موقعیت یک نقطه تا نقطه لنگر شکل را مشخص می‌کند.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|انحراف عمودی از موقعیت یک نقطه تا نقطه لنگر شکل را مشخص می‌کند.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|مشخص می‌کند کدام سمت از شکل نشانگر به صورت افقی با موقعیت نقطه تراز شود.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|مشخص می‌کند کدام سمت از شکل نشانگر به صورت عمودی با موقعیت نقطه تراز شود.|

### **انواع هندسه**
` `نمادگر را می‌توان بر روی هندسه‌های هر نوع اعمال کرد.

|**بعد هندسه**|**نوع هندسه**|**رفتار رندرینگ**|
| :-: | :-: | :-: |
|**نقطه**|نقطه، چند نقطه|شکل را در مرکز مختصات نقطه رسم می‌کند.|
|**خط**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>شکل را در مرکز ثقل هندسه رسم می‌کند</p><p> </p>|
|**سطح**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

برای GeometryCollections، رفتار رندرینگ به طور جداگانه برای هر هندسه درون مجموعه تعیین می‌شود. لایه‌هایی با نوع هندسه ترکیبی از منطق GeometryCollections پیروی می‌کنند.

از MixedGeometrySymbolizer برای محدود کردن یک نمادگر به انواع هندسه‌های خاص استفاده کنید.

### **مثال‌ها**
به طور پیش‌فرض، نمادگر نشانگر دایره‌های سیاه رسم می‌کند:



اینجا نحوه تغییر رنگ پر کردن به قرمز است:



|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

مثال دیگری از استایل‌دهی با یک شکل از پیش تعریف شده (مثلث):



|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----
برای سناریوهای پیشرفته‌تر، ممکن است بخواهید سبک نشانگر را به صورت پویا بر اساس مقادیر ویژگی تنظیم کنید. در اینجا نحوه انجام آن آمده است:



|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
همچنین ممکن است بخواهید برچسب‌هایی به نشانگرهای خود اضافه کنید. برای مثال‌ها از [مثال‌های برچسب‌گذاری نقاط](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) بازدید کنید.
