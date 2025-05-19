---
title: "برچسب‌گذاری ساده"
type: docs
url: /fa/net/simple-labeling/
weight: 10
---

## **برچسب‌گذاری ساده**
برچسب‌گذاری ساده مشخص می‌کند که چگونه ویژگی‌ها باید برچسب‌گذاری شوند.

گزینه‌های پشتیبانی شده عبارتند از:

|**ویژگی**|**توضیحات**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|مشخص می‌کند نام ویژگی برای استفاده به عنوان منبع برچسب‌ها.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|راهی را برای سفارشی‌سازی و قالب‌بندی متن برچسب ارائه می‌دهد. LabelAttribute را لغو می‌کند|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|خانواده فونت مورد استفاده برای رندر کردن متن را مشخص می‌کند. مقدار پیش‌فرض وابسته به سیستم است.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>سبکی که باید روی متن اعمال شود.</p><p>- FontStyle.Regular - متن معمولی.</p><p>- FontStyle.Bold - متن پررنگ.</p><p>- FontStyle.Italic - متن ایتالیک.</p><p>- FontStyle.Underine - متن زیرخط‌دار.</p><p>- FontStyle.StrikeOut - متن با خطی در وسط.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|اندازه متن را مشخص می‌کند.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|رنگ متن را تعیین می‌کند.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|اندازه هاله (یا حاشیه) اطراف متن را تعیین می‌کند.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|رنگ هاله اطراف متن را تعیین می‌کند.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|عبارت هندسی که برای تبدیل هندسه‌ها قبل از انتقال آن به موتور برچسب‌گذاری استفاده می‌شود.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>رفتار رندر کردن برای هندسه‌های چند بخشی را مشخص می‌کند.</p><p>- MultipartMode.All - یک برچسب نزدیک هر قسمت از هندسه قرار دهید.</p><p>- MultipartMode.Any - یک برچسب نزدیک هر قسمتی از هندسه قرار دهید.</p><p>- MultipartMode.Largest - یک برچسب نزدیک بزرگترین قسمت هندسه قرار دهید.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>نحوه قرارگیری برچسب‌ها نسبت به هندسه را مشخص می‌کند.</p><p>- PointLabelPlacement - برچسب را نزدیک مرکز هندسه قرار می‌دهد.</p><p>- LineLabelPlacement - برچسب را در امتداد هندسه یا محیط آن قرار می‌دهد.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|اولویت برچسب را در صورت همپوشانی با برچسب دیگر مشخص می‌کند.<br>برچسبی که اولویت کمتری دارد رندر نمی‌شود. مقدار پیش‌فرض 1000 است.|

## **مثال‌ها**
### **مثال‌های برچسب‌گذاری نقاط**
به طور پیش فرض SimpleLabeling متن را روی نقاط رسم می‌کند:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
در اینجا نحوه استایل‌دهی فونت آمده است:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
برای کنترل موقعیت متن نسبت به ویژگی نقطه، باید ویژگی placement تنظیم شود:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
برای سناریوهای پیشرفته‌تر، ممکن است بخواهید برچسب‌گذاری‌های مختلفی را برای ویژگی‌ها انتخاب کنید. در اینجا نحوه انجام آن آمده است:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **مثال‌های برچسب‌گذاری خطوط**
به طور پیش فرض SimpleLabeling یک برچسب نزدیک مرکز خط رسم می‌کند:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
برای چرخاندن برچسب‌ها به طوری که موازی با خطوط باشند، می‌توان از LineLabelPlacement با LineLabelAlignment.Parallel استفاده کرد:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
اگر می‌خواهید متن‌ها دقیقاً خط را دنبال کنند، می‌توانید از LineLabelPlacement با LineLabelAlignment.Curved استفاده کنید:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
اگر نمی‌خواهید متن‌ها با خط همپوشانی داشته باشند، از LineLabelPlacement.Offset استفاده کنید:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
برای سناریوهای پیشرفته‌تر، ممکن است بخواهید سبک برچسب‌ها را به صورت پویا بر اساس مقادیر ویژگی تنظیم کنید. در اینجا نحوه انجام آن آمده است:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
