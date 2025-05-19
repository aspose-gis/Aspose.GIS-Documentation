---
title: Как запустить Aspose.GIS в Docker
type: docs
description: "Запустите Aspose.GIS в контейнере Docker для Linux, Windows Server и любой ОС."
weight: 139
url: /ru/net/how-to-run-aspose-gis-in-docker/
---

## Необходимые условия

- Docker должен быть установлен на вашей системе. Информацию о том, как установить Docker в Windows или Mac, см. ссылки в разделе "См. также".

- Visual Studio 2022.

- В примере используется NET Core 3.1 SDK.


## Hello World приложение

В этом примере вы создаете простое консольное приложение Hello World, которое создает сложное кривое и сохраняет его в файлы. Затем приложение можно собрать и запустить в Docker.

### Создание консольного приложения

Чтобы создать программу Hello World, выполните следующие действия:
1. После установки Docker убедитесь, что он использует контейнеры Linux (по умолчанию). При необходимости выберите опцию "Переключиться на контейнеры Linux" из меню Docker Desktops.
1. В Visual Studio создайте консольное приложение NET Core 3.1.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. Установите последнюю версию Aspose.GIS из NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. Поскольку приложение будет запущено в Linux, необходимо установить соответствующие собственные библиотеки Linux. Начните с базового образа dotnet core sdk 3.1 и установите libgdiplus libc6-dev.
1. После добавления всех необходимых зависимостей напишите простую программу, которая создает сложное кривое:<br>
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

Обратите внимание, что папка �TestOut� указана как выходная папка для сохранения выходных документов. При запуске приложения в Docker папка на хост-машине будет смонтирована в эту папку в контейнере. Это позволит вам легко просматривать вывод, созданный Aspose.GIS в контейнере Docker.

### Настройка Dockerfile

Следующим шагом является создание и настройка Dockerfile.

1. Создайте Dockerfile и поместите его рядом с файлом решения вашего приложения. Сохраните этот файл без расширения (по умолчанию).
1. В Dockerfile укажите:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

Вышеприведенный Dockerfile является простым и содержит следующие инструкции:

- Образ SDK, который будет использоваться. Здесь это образ Net 3.1. Docker загрузит его при выполнении сборки. Версия SDK указывается как тег.
- Рабочий каталог, который указан в следующей строке.
- Команда для установки libgdiplus выполняется в контейнере. Это требуется System.Drawing.Common.
- Команда для копирования всего в контейнер, публикации приложения и указания точки входа.

### Сборка и запуск приложения в Docker

Теперь приложение можно собрать и запустить в Docker. Откройте свою любимую командную строку, перейдите в папку с приложением (папка, где находятся файл решения и Dockerfile) и выполните следующую команду:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

В первый раз при выполнении этой команды это может занять больше времени, поскольку Docker должен загрузить необходимые образы. После завершения предыдущей команды выполните следующую команду:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

Обратите внимание на аргумент mount, поскольку, как упоминалось ранее, папка на хост-машине монтируется в папку контейнера, чтобы легко видеть результаты выполнения приложения. Пути в Linux чувствительны к регистру.

{{% /alert %}}


## Дополнительные примеры

Для получения дополнительных примеров того, как вы можете использовать Aspose.GIS в Docker, см. [примеры](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## См. также

- [Установка Docker Desktop на Windows](https://docs.docker.com/docker-for-windows/install/)
- [Установка Docker Desktop на Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [Переключение на контейнеры Linux](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) опция
- Дополнительная информация о [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
