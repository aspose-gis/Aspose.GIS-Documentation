---
title: Как да стартирате Aspose.GIS в Docker
type: docs
description: "Стартирайте Aspose.GIS в Docker контейнер за Linux, Windows Server и всяка операционна система."
weight: 139
url: /bg/net/how-to-run-aspose-gis-in-docker/
---

## Предварителни условия

- Docker трябва да бъде инсталиран на вашата система. За информация как да инсталирате Docker на Windows или Mac, вижте връзките в секцията "Вижте също".

- Visual Studio 2022.

- NET Core 3.1 SDK се използва в примера.


## Hello World приложение

В този пример създавате просто Hello World конзолно приложение, което създава съставна крива и я запазва във файлове. Приложението може след това да бъде компилирано и изпълнено в Docker.

### Създаване на конзолното приложение

За да създадете програмата Hello World, следвайте стъпките по-долу:
1. След като Docker е инсталиран, уверете се, че използва Linux контейнери (по подразбиране). Ако е необходимо, изберете опцията Switch to Linux containers от менюто на Docker Desktops.
1. Във Visual Studio създайте NET Core 3.1 конзолно приложение.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. Инсталирайте най-новата версия на Aspose.GIS от NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. Тъй като приложението ще се изпълнява на Linux, трябва да бъдат инсталирани подходящите родни Linux активи. Започнете с основния образ на dotnet core sdk 3.1 и инсталирайте libgdiplus libc6-dev.
1. Когато всички необходими зависимости са добавени, напишете проста програма, която създава съставна крива:<br>
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

Забележете, че папката �TestOut� е посочена като изходна папка за запазване на изходните документи. Когато изпълнявате приложението в Docker, папка от хост машината ще бъде монтирана към тази папка в контейнера. Това ще ви позволи лесно да видите изхода, генериран от Aspose.GIS в Docker контейнера.

### Конфигуриране на Dockerfile

Следващата стъпка е да създадете и конфигурирате Dockerfile.

1. Създайте Dockerfile и го поставете до файла с решението на вашето приложение. Запазете този файл без разширение (по подразбиране).
1. В Dockerfile посочете:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

Горното е прост Dockerfile, който съдържа следните инструкции:

- Изображението на SDK, което трябва да се използва. Тук това е изображението Net 3.1. Docker ще го изтегли, когато бъде изпълнена компилацията. Версията на SDK е посочена като таг.
- Работната директория, която е посочена в следващия ред.
- Командата за инсталиране на libgdiplus се изпълнява в контейнера. Това е необходимо от System.Drawing.Common.
- Командата за копиране на всичко в контейнер, публикуване на приложението и определяне на входната точка.

### Компилиране и стартиране на приложението в Docker

Сега приложението може да бъде компилирано и изпълнено в Docker. Отворете любимата си командна линия, променете директорията към папката с приложението (папката, където са разположени файловете с решението и Dockerfile) и изпълнете следната команда:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

Първия път, когато тази команда бъде изпълнена, може да отнеме повече време, тъй като Docker трябва да изтегли необходимите изображения. След като горната команда е завършена, изпълнете следната команда:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

Обърнете внимание на аргумента mount, защото, както беше споменато по-рано, папка от хост машината е монтирана в папката на контейнера, за да видите лесно резултатите от изпълнението на приложението. Пътищата в Linux са чувствителни към главни и малки букви.

{{% /alert %}}


## Повече примери

За повече примери как можете да използвате Aspose.GIS в Docker, вижте [примерите](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## Вижте също

- [Инсталиране на Docker Desktop на Windows](https://docs.docker.com/docker-for-windows/install/)
- [Инсталиране на Docker Desktop на Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- Опция [Преминаване към Linux контейнери](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)
- Допълнителна информация за [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
