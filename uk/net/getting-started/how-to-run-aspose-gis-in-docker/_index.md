---
title: Як запустити Aspose.GIS в Docker
type: docs
description: "Запустіть Aspose.GIS у контейнері Docker для Linux, Windows Server та будь-якої ОС."
weight: 139
url: /uk/net/how-to-run-aspose-gis-in-docker/
---

## Передумови

- Docker має бути встановлений на вашій системі. Інформацію про те, як встановити Docker у Windows або Mac, див. посилання в розділі "Див. також".

- Visual Studio 2022.

- NET Core 3.1 SDK використовується в прикладі.


## Hello World Application

У цьому прикладі ви створюєте просту програму Hello World console application, яка створює складену криву та зберігає її у файлах. Потім додаток можна скомпілювати та запустити в Docker.

### Створення Console Application

Щоб створити програму Hello World, виконайте наступні кроки:
1. Після встановлення Docker переконайтеся, що він використовує Linux Containers (за замовчуванням). Якщо необхідно, виберіть опцію Switch to Linux containers з меню Docker Desktops.
1. У Visual Studio створіть NET Core 3.1 console application.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. Встановіть останню версію Aspose.GIS з NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. Оскільки додаток буде запущено на Linux, необхідно встановити відповідні рідні ресурси Linux. Почніть із базового образу dotnet core sdk 3.1 та встановіть libgdiplus libc6-dev.
1. Коли всі необхідні залежності будуть додані, напишіть просту програму, яка створює складену криву:<br>
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

Зверніть увагу, що папка �TestOut� вказана як вихідна папка для збереження вихідних документів. При запуску програми в Docker папку на хост-машині буде змонтовано до цієї папки в контейнері. Це дозволить вам легко переглядати результати, створені Aspose.GIS у контейнері Docker.

### Налаштування Dockerfile

Наступним кроком є створення та налаштування Dockerfile.

1. Створіть Dockerfile і розмістіть його поруч із файлом рішення вашого додатка. Залиште цю назву файлу без розширення (за замовчуванням).
1. У Dockerfile вкажіть:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

Вище наведено простий Dockerfile, який містить наступні інструкції:

- Образ SDK, який потрібно використовувати. Тут це образ Net 3.1. Docker завантажить його під час виконання збірки. Версія SDK вказана як тег.
- Робочий каталог, який вказано на наступному рядку.
- Команда для встановлення libgdiplus виконується в контейнері. Це потрібно System.Drawing.Common.
- Команда для копіювання всього до контейнера, публікації програми та вказівки точки входу.

### Збірка та запуск програми в Docker

Тепер програму можна скомпілювати та запустити в Docker. Відкрийте улюблену командну строку, перейдіть до папки з додатком (папка, де знаходяться файл рішення та Dockerfile) і виконайте наступну команду:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

Перший раз ця команда може зайняти більше часу, оскільки Docker повинен завантажити необхідні образи. Після завершення попередньої команди виконайте наступну команду:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

Зверніть увагу на аргумент mount, оскільки, як згадувалося раніше, папку на хост-машині монтують у папку контейнера, щоб легко бачити результати виконання програми. Шляхи в Linux чутливі до регістру.

{{% /alert %}}


## Більше прикладів

Для отримання додаткових зразків того, як ви можете використовувати Aspose.GIS в Docker, див. [examples](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## Див. також

- [Install Docker Desktop on Windows](https://docs.docker.com/docker-for-windows/install/)
- [Install Docker Desktop on Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [Switch to Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) option
- Додаткова інформація про [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
