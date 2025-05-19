---
title: نحوه اجرای Aspose.GIS در Docker
type: docs
description: "اجرای Aspose.GIS در یک کانتینر Docker برای لینوکس، سرور ویندوز و هر سیستم عاملی."
weight: 139
url: /fa/net/how-to-run-aspose-gis-in-docker/
---

## پیش‌نیازها

- Docker باید روی سیستم شما نصب شده باشد. برای اطلاعات در مورد نحوه نصب Docker در ویندوز یا مک، به پیوندهای بخش "همچنین ببینید" مراجعه کنید.

- Visual Studio 2022.

- از NET Core 3.1 SDK در مثال استفاده می‌شود.


## برنامه Hello World

در این مثال، یک برنامه کنسول ساده Hello World ایجاد می‌کنید که یک منحنی ترکیبی ایجاد می‌کند و آن را در فایل‌ها ذخیره می‌کند. سپس می‌توان برنامه را ساخت و در Docker اجرا کرد.

### ایجاد برنامه کنسول

برای ایجاد برنامه Hello World، مراحل زیر را دنبال کنید:
1. پس از نصب Docker، اطمینان حاصل کنید که از کانتینرهای لینوکس (پیش‌فرض) استفاده می‌کند. در صورت نیاز، گزینه Switch to Linux containers را از منوی Docker Desktops انتخاب کنید.
1. در Visual Studio، یک برنامه کنسول NET Core 3.1 ایجاد کنید.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. آخرین نسخه Aspose.GIS را از NuGet نصب کنید.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. از آنجایی که برنامه روی لینوکس اجرا می‌شود، باید دارایی‌های بومی مناسب لینوکس نصب شوند. با تصویر پایه dotnet core sdk 3.1 شروع کنید و libgdiplus libc6-dev را نصب کنید.
1. هنگامی که تمام وابستگی‌های مورد نیاز اضافه شدند، یک برنامه ساده بنویسید که یک منحنی ترکیبی ایجاد کند:<br>
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
                // ایجاد یک حرف 'S' (از پایین سمت چپ شروع می‌شود)
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

توجه داشته باشید که پوشه �TestOut� به عنوان یک پوشه خروجی برای ذخیره اسناد خروجی مشخص شده است. هنگام اجرای برنامه در Docker، یک پوشه روی دستگاه میزبان به این پوشه در کانتینر متصل می‌شود. این به شما امکان می‌دهد تا به راحتی خروجی تولید شده توسط Aspose.GIS را در کانتینر Docker مشاهده کنید.

### پیکربندی Dockerfile

مرحله بعدی ایجاد و پیکربندی Dockerfile است.

1. Dockerfile را ایجاد کنید و آن را در کنار فایل راه حل برنامه خود قرار دهید. نام این فایل را بدون پسوند نگه دارید (پیش‌فرض).
1. در Dockerfile، مشخص کنید:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

بالا یک Dockerfile ساده است که شامل دستورالعمل‌های زیر است:

- تصویر SDK مورد استفاده. در اینجا تصویر Net 3.1 است. Docker هنگام اجرای ساخت آن را دانلود می‌کند. نسخه SDK به عنوان برچسب مشخص شده است.
- دایرکتوری کاری، که در خط بعدی مشخص شده است.
- دستور نصب libgdiplus در کانتینر اجرا می‌شود. این توسط System.Drawing.Common مورد نیاز است.
- دستور برای کپی کردن همه چیز به کانتینر، انتشار برنامه و تعیین نقطه ورود.

### ساخت و اجرای برنامه در Docker

اکنون می‌توان برنامه را در Docker ساخت و اجرا کرد. ترمینال مورد علاقه خود را باز کنید، به پوشه‌ای که حاوی برنامه است (پوشه‌ای که فایل راه حل و Dockerfile در آن قرار دارند) تغییر دهید و دستور زیر را اجرا کنید:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

اولین باری که این دستور اجرا می‌شود ممکن است طولانی‌تر باشد، زیرا Docker باید تصاویر مورد نیاز را دانلود کند. پس از تکمیل دستور قبلی، دستور زیر را اجرا کنید:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}


{{% alert color="primary" %}} 

به آرگومان mount توجه داشته باشید، زیرا همانطور که قبلاً ذکر شد، یک پوشه روی دستگاه میزبان به پوشه کانتینر متصل می‌شود تا بتوانید به راحتی نتایج اجرای برنامه را ببینید. مسیرها در لینوکس به حروف بزرگ و کوچک حساس هستند.

{{% /alert %}}


## مثال‌های بیشتر

برای نمونه‌های بیشتری از نحوه استفاده از Aspose.GIS در Docker، به [مثال‌ها](https://github.com/aspose-gis/Aspose.Gis-for-.NET) مراجعه کنید.


## همچنین ببینید

- [نصب Docker Desktop در ویندوز](https://docs.docker.com/docker-for-windows/install/)
- [نصب Docker Desktop در مک](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022، NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- گزینه [Switch to Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)
- اطلاعات بیشتر در مورد [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
