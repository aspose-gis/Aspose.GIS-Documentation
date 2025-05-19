---
title: كيفية تشغيل Aspose.GIS في Docker
type: docs
description: "تشغيل Aspose.GIS في حاوية Docker على نظام Linux و Windows Server وأي نظام تشغيل آخر."
weight: 139
url: /ar/net/how-to-run-aspose-gis-in-docker/
---

## الشروط الأولية

- يجب أن يكون Docker مثبتًا على النظام الخاص بك. لمزيد من المعلومات حول كيفية تثبيت Docker على Windows أو Mac، راجع الروابط في قسم "انظر أيضًا".

- Visual Studio 2022.

- يتم استخدام NET Core 3.1 SDK في هذا المثال.


## تطبيق Hello World

في هذا المثال، ستقوم بإنشاء تطبيق وحدة تحكم بسيط Hello World ينشئ منحنى مركب ويحفظه في ملفات. يمكن بناء التطبيق ثم تشغيله في Docker.

### إنشاء تطبيق وحدة التحكم

لإنشاء برنامج Hello World، اتبع الخطوات التالية:
1. بمجرد تثبيت Docker، تأكد من أنه يستخدم حاويات Linux (افتراضيًا). إذا لزم الأمر، حدد خيار التبديل إلى حاويات Linux من قائمة Docker Desktops.
1. في Visual Studio، قم بإنشاء تطبيق وحدة تحكم NET Core 3.1.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. قم بتثبيت أحدث إصدار من Aspose.GIS من NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. نظرًا لأن التطبيق سيتم تشغيله على نظام Linux، فيجب تثبيت الأصول البرمجية الأصلية المناسبة لنظام Linux. ابدأ باستخدام صورة قاعدة مجموعة التطوير core sdk 3.1 وقم بتثبيت libgdiplus libc6-dev.
1. بعد إضافة جميع التبعيات اللازمة، اكتب برنامج بسيط ينشئ منحنى مركب:<br>
**.NET**<br>
{{< highlight csharp >}}
using System.IO;
using Aspose.Gis.Geometries;
using Aspose.Gis;

namespace Aspose.GIS.Docker.Sample
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string path = Path.Combine("TestOut", "CreateCompoundCurve_out.shp");
            using (VectorLayer layer = VectorLayer.Create(path, Drivers.Shapefile))
            {
                var feature = layer.ConstructFeature();
                // create an 'S' letter (starts at bottom left end)
                var compoundCurve = new CompoundCurve();

                var bottom = (ILineString)Geometry.FromText("LineString (0 0, 3 0)");
                var firstArc = (ICircularString)Geometry.FromText("CircularString (3 0, 4 1, 3 2)");
                var middle = (ILineString)Geometry.FromText("LineString (3 2, 1 2)");
                var secondArc = (ICircularString)Geometry.FromText("CircularString (1 2, 0 3, 1 4)");
                var top = (ILineString)Geometry.FromText("LineString (1 4, 4 4)");

                compoundCurve.AddCurve(bottom);
                compoundCurve.AddCurve(firstArc);
                compoundCurve.AddCurve(middle);
                compoundCurve.AddCurve(secondArc);
                compoundCurve.AddCurve(top);
                feature.Geometry = compoundCurve;

                layer.Add(feature);
            }
        }
    }
}
{{< /highlight >}}

يرجى ملاحظة أن يتم تحديد مجلد "TestOut" كمجلد إخراج لحفظ المستندات الناتجة. عند تشغيل التطبيق في Docker، سيتم توصيل مجلد على الجهاز الهدف بهذا المجلد في الحاوية. وهذا سيمكنك من رؤية بسهولة النتائج التي تم إنشاؤها بواسطة Aspose.GIS في حاوية Docker.

### تكوين ملف Dockerfile

الخطوة التالية هي إنشاء وتكوين ملف Dockerfile.

1. قم بإنشاء ملف Dockerfile ووضعه بجوار ملف الحل لتطبيقك. احتفظ باسم هذا الملف بدون امتداد (الافتراضي).
1. في ملف Dockerfile، حدد:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

المذكور أعلاه هو ملف Dockerfile بسيط، يحتوي على التعليمات التالية:

- الصورة SDK التي ستتم استخدامها. هنا تكون الصورة Net 3.1. سيقوم Docker بتنزيلها عند تشغيل البنية. تم تحديد إصدار SDK كوسم.
- دليل العمل المحدد في السطر التالي.
- تشغيل الأمر لتثبيت libgdiplus في الحاوية. هذا مطلوب من قبل System.Drawing.Common.
- الأمر لنسخ كل شيء إلى الحاوية، نشر التطبيق، وتحديد نقطة البداية.

### بناء وتشغيل التطبيق في Docker

الآن يمكن بناء التطبيق وتشغيله في Docker. افتح سطر الأوامر المفضل لديك، غير الدليل إلى المجلد الذي يحتوي على التطبيق (المجلد الذي يتم فيه وضع ملف الحل وملف Dockerfile) وأدخل الأمر التالي:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

قد يستغرق الأمر الأول تنفيذ وقتًا أطول، نظرًا لأن Docker بحاجة لتنزيل الصور المطلوبة. بمجرد اكتمال الأمر السابق، قم بتشغيل الأمر التالي:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

امنح انتباهك لوسيط التركيب، لأنه، كما ذكر سابقًا، يتم توصيل مجلد على جهاز الهدف بمجلد الحاوية، لرؤية النتائج بسهولة عند تشغيل التطبيق. المسارات في Linux حساسة لحالة الأحرف.

{{% /alert %}}


## المزيد من الأمثلة

لمزيد من الأمثلة حول كيفية استخدام Aspose.GIS في Docker، انظر [الأمثلة](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## انظر أيضًا

- [تثبيت Docker Desktop على Windows](https://docs.docker.com/docker-for-windows/install/)
- [تثبيت Docker Desktop على Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022، NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- خيار [Switch to Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)
- معلومات إضافية حول [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
