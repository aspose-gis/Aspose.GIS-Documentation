---
title: "جریان‌ها و فضای ذخیره‌سازی از راه دور"
type: docs
url: /fa/net/streams-and-remote-storage/
weight: 70
---

## **کار با فرمت‌های چند فایل**
برخی از فرمت‌های داده GIS محتوا را به چندین فایل تقسیم می‌کنند. برای مثال، یک shapefile باید حداقل سه فایل داشته باشد: *.shp، *.shx و *.dbf. این فرمت‌ها نیاز دارند که همه فایل‌ها در یک ساختار دایرکتوری خاص با الگوی از پیش تعریف شده برای نام فایل‌ها ذخیره شوند.

در عین حال، ممکن است فایل‌ها روی سرور از راه دور یا مکان دیگری که فقط از طریق جریان قابل دسترسی باشد ذخیره شوند. جریان‌ها فاقد اطلاعات مربوط به نام فایل و ساختار دایرکتوری هستند و این امر تعیین نحوه پردازش داده را برای درایورهای فرمت فایل غیرممکن می‌کند. Aspose.GIS با ارائه مکانیزم مسیرهای انتزاعی این مشکل را حل می‌کند.

یک مسیر انتزاعی نمایانگر مسیری به یک فایل (یا دایرکتوری) در فضای ذخیره‌سازی شبیه به سیستم فایل است. فضای ذخیره‌سازی می‌تواند هر چیزی باشد که مفهوم فایل و دایرکتوری را داشته باشد، از آرشیو گرفته تا سرور FTP. این تعریف می‌کند که چگونه عملیات فایل معمولی مانند باز کردن یک فایل یا فهرست کردن یک دایرکتوری انجام شود.

شما می‌توانید نحوه انجام عملیات فایل برای فضای ذخیره‌سازی خود را با پیاده‌سازی کلاسی که از [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) به ارث می‌برد و ارائه پیاده‌سازی برای روش‌های انتزاعی آن مشخص کنید.
## **نمایش: فضای ذخیره‌سازی Azure Blob**
مخزن Aspose.GIS Examples شامل نمونه‌ای از یک پیاده‌سازی کاملاً کاربردی از یک مسیر انتزاعی سفارشی برای فضای ذخیره‌سازی Azure Blob است. این نمایش نشان می‌دهد که چگونه می‌توان یک shapefile را مستقیماً از فضای ذخیره‌سازی Azure Blob خواند. می‌توانید آن را در اینجا پیدا کنید: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **فرمت‌های تک‌فایلی (GeoJSON، KML)**
فرمت‌های داده GIS مانند GeoJSON و KML می‌توانند تمام داده‌ها را برای یک لایه در یک فایل واحد ذخیره کنند. اگر بتوانید جریانی برای فایل بدست آورید، می‌توانید از پیاده‌سازی مسیر انتزاعی سفارشی صرف نظر کنید و از روش [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) برای ایجاد یک مسیر انتزاعی برای جریان استفاده کنید.
### **خواندن یک فایل از یک جریان**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **نوشتن یک فایل به یک جریان**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
