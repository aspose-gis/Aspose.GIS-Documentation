---
title: 如何在 Docker 中运行 Aspose.GIS
type: docs
description: 在 Linux、Windows Server 和任何操作系统中，在 Docker 容器中运行 Aspose.GIS。
weight: 139
url: /zh/net/how-to-run-aspose-gis-in-docker/
---

## 先决条件

- Docker 必须安装在您的系统上。有关如何在 Windows 或 Mac 上安装 Docker 的信息，请参阅“参见”部分中的链接。

- Visual Studio 2022。

- NET Core 3.1 SDK 用于示例。

## Hello World 应用程序

在此示例中，您创建一个简单的 Hello World 控制台应用程序，该程序创建复合曲线并将其保存到文件中。然后可以在 Docker 中构建和运行该应用程序。

### 创建控制台应用程序

要创建 Hello World 程序，请按照以下步骤操作：
1. 安装 Docker 后，确保它使用 Linux 容器（默认）。如果需要，从 Docker Desktops 菜单中选择“切换到 Linux 容器”选项。
1. 在 Visual Studio 中，创建一个 NET Core 3.1 控制台应用程序。<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. 从 NuGet 安装最新版本的 Aspose.GIS。<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. 由于该应用程序将在 Linux 上运行，因此必须安装适当的本机 Linux 资产。从 dotnet core sdk 3.1 基本镜像开始，并安装 libgdiplus libc6-dev。
1. 添加所有必需的依赖项后，编写一个简单的程序来创建复合曲线：<br>
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
                // 创建一个“S”字母（从左下端开始）
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

请注意，“TestOut”文件夹指定为保存输出文档的输出文件夹。在 Docker 中运行应用程序时，主机机器上的一个文件夹将被挂载到容器中的此文件夹中。这将使您能够轻松查看 Docker 容器中 Aspose.GIS 生成的输出。

### 配置 Dockerfile

下一步是创建和配置 Dockerfile。

1. 创建 Dockerfile 并将其放置在您的应用程序解决方案文件旁边。保留此文件名（无扩展名）。
1. 在 Dockerfile 中，指定：

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

以上是一个简单的 Dockerfile，其中包含以下指令：

- 要使用的 SDK 镜像。这里是 Net 3.1 镜像。Docker 在运行构建时会下载它。SDK 的版本指定为标签。
- 工作目录，在下一行中指定。
- 在容器中运行安装 libgdiplus 的命令。System.Drawing.Common 需要此命令。
- 将所有内容复制到容器、发布应用程序并指定入口点的命令。

### 在 Docker 中构建和运行应用程序

现在可以在 Docker 中构建和运行该应用程序。打开您喜欢的命令行提示符，更改目录到包含应用程序的文件夹（放置解决方案文件和 Dockerfile 的文件夹），然后运行以下命令：

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

首次执行此命令时可能需要更长的时间，因为 Docker 需要下载所需的镜像。完成上述命令后，运行以下命令：

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

请注意 mount 参数，因为如前所述，主机机器上的一个文件夹被挂载到容器的文件夹中，以便轻松查看应用程序执行的结果。Linux 中的路径区分大小写。

{{% /alert %}}


## 更多示例

有关如何在 Docker 中使用 Aspose.GIS 的更多示例，请参阅 [examples](https://github.com/aspose-gis/Aspose.Gis-for-.NET)。

## 参见

- [在 Windows 上安装 Docker Desktop](https://docs.docker.com/docker-for-windows/install/)
- [在 Mac 上安装 Docker Desktop](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022、NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [切换到 Linux 容器](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)选项
- 关于 [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk) 的更多信息
