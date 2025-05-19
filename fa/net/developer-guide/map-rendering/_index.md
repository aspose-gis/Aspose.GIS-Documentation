---
title: رندر نقشه به تصویر SVG، PNG، JPG با استفاده از کتابخانه GIS C#‎
linktitle: "رندر نقشه"
type: docs
url: /fa/net/map-rendering/
weight: 50
description: با API سی شارپ GIS، می‌توانید نقشه را از فرمت‌های Shapefile، FileGDB، GeoJSON، KML رندر کنید، استایل‌بندی پیشرفته انجام دهید و نقشه را از فرمت‌های رستری ترسیم کنید.
---

## **بررسی اجمالی رندر نقشه**
با API سی شارپ Aspose.GIS for .NET می‌توانید یک نقشه را از Shapefile، FileGDB، GeoJSON، KML یا سایر [فرمت‌های فایل پشتیبانی شده](/gis/net/supported-file-formats/) به SVG، PNG، JPEG یا BMP رندر کنید.

در اینجا کد سی شارپ وجود دارد که نشان می‌دهد چگونه یک نقشه را از یک shapefile با استفاده از تنظیمات پیش‌فرض به SVG رندر کنیم:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



در اینجا نتیجه آمده است:



![رندر نقشه](map_rendering.png)

بیایید نگاهی دقیق‌تر به کد داشته باشیم.

اول، یک [نقشه ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map) را ایجاد می‌کنیم. این نشان‌دهنده مجموعه‌ای از لایه‌ها از منابع مختلف است که می‌توانند رندر شوند. نقشه دارای اندازه‌ای است که در نظر گرفته شده است تا با آن نمایش داده شود. در اینجا ما نقشه را به عرض 800 پیکسل و ارتفاع 400 پیکسل تنظیم می‌کنیم.

توجه داشته باشید که نقشه در دستور using قرار دارد. این ضروری است زیرا نقشه تمام منابع اضافه شده به آن را ردیابی می‌کند و هنگام اتمام رندر و دور انداختن شیء Map، آن‌ها را از بین می‌برد.

سپس یک لایه را از یک فایل به نقشه اضافه می‌کنیم. هر لایه روی لایه قبلی رندر می‌شود، به ترتیبی که به نقشه اضافه شده‌اند. برای اطلاعات بیشتر در مورد نحوه باز کردن لایه‌های برداری [اینجا](/gis/net/working-with-vector-layers/) را ببینید.

در نهایت، [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) را فراخوانی می‌کنیم تا نقشه را در یک فایل رندر کنیم. ما مسیری را برای ذخیره فایل نتیجه و یک رندر کننده برای استفاده مشخص می‌کنیم. کلاس [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) شامل مراجعی به تمام رندرکننده‌های موجود در Aspose.GIS است. به عنوان مثال، می‌توانید Renderers.Png را به جای Renderers.Svg در مثال بالا مشخص کنید تا نقشه را به یک فایل PNG رندر کنید.
## **استایل‌بندی پیشرفته**
با API Aspose.GIS می‌توانید سفارشی‌سازی رندر و سبک‌های ویژگی‌ها را برای دستیابی به ظاهری که می‌خواهید انجام دهید.

![استایل‌بندی پیشرفته](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **ترسیم رستری در نقشه**
با Aspose.GIS for .NET می‌توانید یک نقشه را از فرمت‌های رستری رندر کنید.
### **رندر با تنظیمات پیش‌فرض**
در اینجا نحوه رندر یک نقشه از GeoTIFF به SVG با استفاده از تنظیمات پیش‌فرض آمده است:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![رستر پیش‌فرض](default_raster.png)
### **رندر رسترهای کج**
با Aspose.GIS می‌توانید یک رستر با سلول‌های رستری کج را رندر کنید.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![رستر کج](skew_raster.png)
### **رندر در مرجع فضایی قطبی**
Aspose.GIS به شما امکان می‌دهد از مراجع فضایی قطبی در فرآیند رندر نقشه استفاده کنید.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![کشورهای گنومونیک](gnomonic_countries.png)
