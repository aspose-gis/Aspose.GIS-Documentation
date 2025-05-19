---
title: نمادشناسی - API GIS# C
linktitle: "نمادشناسی"
type: docs
url: /fa/net/symbology/
weight: 10
description: کتابخانه یا API GIS# C از نمادسازها برای ترسیم هندسه ویژگی مانند نشانگر، خط، پر کردن و ترکیب نمادسازها برای ایجاد تجسم‌های پیچیده‌تر پشتیبانی می‌کند.
---

نمادساز روشی برای رسم هندسه یک ویژگی روی نقشه است.

|** **|**نمادساز**|**کلاس API**|**توضیحات**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**نشانگر**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|یک شکل از پیش تعریف شده را با پر کردن و حاشیه قابل تنظیم رسم می‌کند. |
|![todo:image_alt_text](symbology_2.png)|**خط**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|یک خط با سبک قابل تنظیم رسم می‌کند.|
|![todo:image_alt_text](symbology_3.png)|**پر کردن**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|یک چند ضلعی یا ناحیه محدود شده توسط یک خط را با پر کردن و ضربه قابل تنظیم پر می‌کند.|

علاوه بر نمادسازهایی که رسم واقعی را انجام می‌دهند، تعدادی نمادساز دیگر نیز وجود دارد که امکان ترکیب نمادسازهای دیگر را برای ایجاد تجسم‌های پیچیده‌تر فراهم می‌کنند.

|**نمادساز**|**کلاس API**|**توضیحات**|
| :- | :- | :- |
|**نمادساز لایه‌ای**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|یک ویژگی را با چندین نمادساز روی یکدیگر رسم می‌کند|
|**نمادساز هندسه ترکیبی**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|ویژگی‌ها را از لایه‌هایی که حاوی هندسه‌های مختلط هستند با یک نمادساز خاص برای هر نوع هندسه رسم می‌کند|
|**نمادساز مبتنی بر قانون**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|یک نمادساز را برای اعمال به یک ویژگی با قوانینی که توسط کاربر مشخص شده است انتخاب می‌کند.|
|**نمادساز خوشه نشانگر**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|خوشه‌بندی نشانگرها، گروه‌بندی این آیتم‌ها را رسم می‌کند.|
|**نمادساز تولید کننده هندسه**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|به جایگزینی هندسه ویژگی قبل از رندر اجازه می‌دهد.|
|**نمادساز تهی**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|هیچ چیزی رسم نمی‌کند. هنگام ترکیب با نمادسازهای دیگر، مانند نمادساز مبتنی بر قانون، مفید است.|
