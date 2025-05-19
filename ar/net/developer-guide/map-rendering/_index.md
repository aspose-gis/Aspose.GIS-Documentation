---
title: تقديم خريطة الرسومات إلى صورة SVG، PNG، JPG باستخدام مكتبة GIS C#
linktitle: "رسم الخريطة"
type: docs
url: /ar/net/map-rendering/
weight: 50
description: باستخدام واجهة برمجة التطبيقات C# لـ GIS ، يمكنك رسم الخريطة من ملف Shapefile، FileGDB، GeoJSON، KML ، أداء الأنماط المتقدمة ورسم الخريطة من تنسيقات البكسل.
---

## **نظرة عامة على رسم الخريطة**
مع Aspose.GIS لـ .NET C# API يمكنك رسم خريطة من ملف Shapefile، FileGDB، GeoJSON، KML أو أي [تنسيقات ملف مدعومة](/ar/gis/net/supported-file-formats/) أخرى إلى SVG، PNG، JPEG، أو BMP.

هنا كود C# يوضح كيفية رسم خريطة من ملف shapefile إلى SVG باستخدام الإعدادات الافتراضية:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}

ها هو النتيجة:

![رسم الخريطة](map_rendering.png)

دعونا نلقي نظرة أقرب على الكود.

أولاً ، نقوم بإنشاء [Map](https://reference.aspose.com/gis/net/aspose.gis.rendering/map)، وهي تمثل مجموعة من الطبقات من مصادر مختلفة يمكن عرضها. يوجد للخريطة حجم مقصود للعرض. هنا نقوم بتعيين الخريطة بأن تكون عرضها 800 بكسل وارتفاعها 400 بكسل.

لاحظ أن الخريطة متضمنة في بيان using. هذا ضروري لأن الخريطة تتتبع جميع الموارد التي تمت إضافتها إليها، وتتخلص منها عندما ننتهي من رسم الخريطة والكائن Map يتم التخلص منه.

بعد ذلك، نضيف طبقة من ملف إلى الخريطة. يتم رسم كل طبقة فوق الطبقة السابقة، بالترتيب الذي تمت إضافته إلى الخريطة. انظر المزيد من التفاصيل حول كيفية فتح الطبقات النوعية [هنا](/ar/gis/net/working-with-vector-layers/).

أخيرًا، نستدعي [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) لرسم الخريطة إلى ملف. نحدد مسارًا لحفظ ملف النتيجة ومشغل لاستخدامه. تحتوي الفئة [Renderers](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) على مراجع لجميع المشغلات المضمّنة في Aspose.GIS. على سبيل المثال، يمكنك تحديد Renderers.Png بدلاً من Renderers.Svg في المثال أعلاه لرسم الخريطة إلى ملف PNG.

## **الأنماط المتقدمة**
مع Aspose.GIS API، يمكنك تخصيص الرسم والأنماط الميزة من أجل تحقيق المظهر الذي تريده.

![الأنماط المتقدة](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}

## **رسم البكسل في الخريطة**
مع Aspose.GIS لـ .NET يمكنك رسم خريطة من تنسيقات البكسل.

### **الرسم بالإعدادات الافتراضية**
ها هو كيفية رسم خريطة من GeoTIFF إلى SVG باستخدام الإعدادات الافتراضية:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![البكسل الافتراضي](default_raster.png)

### **رسم بكسل مائلة**
مع Aspose.GIS يمكنك رسم بكسل مائلة.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![البكسل المائل](skew_raster.png)

### **رسم في الإسناد المكاني القطبي**
Aspose.GIS يتيح لك استخدام الإسناد المكاني القطبي في عملية رسم الخريطة.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![دول جنومونيك](gnomonic_countries.png)
