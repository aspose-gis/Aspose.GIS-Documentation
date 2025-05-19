---
title: "Fill Symbolizer"
type: docs
url: /fa/net/fill-symbolizer/
weight: 30
description: کتابخانه GIS C# API از Simple Fill symbolizer برای پر کردن سبک و ضربه برای هندسه‌های دو بعدی چند ضلعی از هر نوع مانند Point، Line، Surface پشتیبانی می‌کند.
---

## **Fill Symbolizer**
Simple Fill symbolizer یک ناحیه را با سبک و ضربه قابل تنظیم پر می کند. این نمادگر پیش فرض برای هندسه های دو بعدی (چند ضلعی) است.

اگر چند ضلعی دارای "سوراخ" باشد، آنها پر نمی شوند، اما مرزهای اطراف سوراخ ها به روش معمول ضربه می خورند. "جزایر" در داخل سوراخ ها پر و ضربه می خورند و غیره.

گزینه های سبک پشتیبانی شده:

|**Property**|**Description**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|رنگ و شفافیت داده شده به پر کردن را مشخص می کند.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - پر کردن جامد</p><p>- None - چند ضلعی را پر نکنید</p><p>- Horizontal Hatch - الگویی از خطوط افقی.</p><p>- Vertical Hatch - الگویی از خطوط عمودی.</p><p>- Cross Hatch - مشخص کننده خطوط افقی و عمودی است که متقاطع هستند.</p><p>- Forward Diagonal Hatch - الگویی از خطوط روی مورب از بالا چپ به پایین راست.</p><p>- Backward Diagonal Hatch - الگویی از خطوط روی مورب از بالا راست به پایین چپ.</p><p>- Diagonal Cross Hatch - الگویی از خطوط مورب متقاطع.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|رنگ و شفافیت داده شده به خط ضربه را مشخص می کند.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|نحوه رسم کار خط نماد را مشخص می کند.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|عرض خط ضربه را مشخص می کند.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|آرایه ای از فواصل را که طول های تناوبی خطوط و فضاهای خط چین را مشخص می کند، مشخص می کند.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|فاصله از شروع یک خط تا شروع الگوی خط چین را مشخص می کند.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>نحوه ارائه خطوط در تقاطع های قطعات خط را تعیین می کند.</p><p>- Miter - گوشه تیز</p><p>- Round - گوشه گرد</p><p>- Bevel - گوشه مورب</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|انحراف افقی از یک مکان نقطه تا نقطه لنگر شکل را مشخص می کند.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|انحراف عمودی از یک مکان نقطه تا نقطه لنگر شکل را مشخص می کند.|

### **Geometry Types**
` `نمادگر را می توان به هندسه های هر نوع اعمال کرد.

|**Geometry Dimension**|**Geometry Types**|**Rendering Behavior**|
| :-: | :-: | :-: |
|**Point**|Point, MultiPoint|یک مربع کوچک چند ضلعی متعامد رسم می کند.|
|**Line**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|خط برای پر کردن با اتصال نقطه پایانی آن به نقطه شروع آن بسته می شود. فقط خط اصلی ضربه می خورد.|
|**Surface**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|چند ضلعی را رسم می کند.|

برای GeometryCollections، رفتار رندرینگ به طور جداگانه برای هر هندسه در داخل مجموعه تعیین می شود. لایه هایی با نوع هندسه Mixed از منطق GeometryCollections پیروی می کنند.

از MixedGeometrySymbolizer برای محدود کردن یک نمادگر به انواع هندسه خاص استفاده کنید.

### **Examples**
به طور پیش فرض Simple Fill symbolizer یک خط ضربه سیاه و پر کردن سفید جامد رسم می کند:



اینجا نحوه تغییر سبک آمده است:




|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

شاید بخواهید برچسب هایی نیز به چند ضلعی های خود اضافه کنید. برای مثال در مورد نحوه برچسب گذاری مرزهای چند ضلعی ها به [Lines Labeling Examples](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) و در مورد نمونه هایی از نحوه برچسب گذاری مراکز چند ضلعی ها به [Points Labeling Examples](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) مراجعه کنید.
