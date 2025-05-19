---
title: Docker에서 Aspose.GIS 실행 방법
type: docs
description: "Linux, Windows Server 및 모든 OS용 Docker 컨테이너에서 Aspose.GIS를 실행합니다."
weight: 139
url: /ko/net/how-to-run-aspose-gis-in-docker/
---

## 필수 조건

- Docker이 시스템에 설치되어 있어야 합니다. Windows 또는 Mac에 Docker을 설치하는 방법에 대한 자세한 내용은 "참고" 섹션의 링크를 참조하십시오.

- Visual Studio 2022.

- 예제에서는 NET Core 3.1 SDK가 사용됩니다.

## Hello World 애플리케이션

이 예제에서는 복합 곡선을 생성하고 파일을 저장하는 간단한 Hello World 콘솔 애플리케이션을 만듭니다. 그런 다음 애플리케이션을 빌드하여 Docker에서 실행할 수 있습니다.

### 콘솔 애플리케이션 만들기

Hello World 프로그램을 만들려면 아래 단계를 따르십시오.
1. Docker이 설치되었는지 확인하고 Linux 컨테이너(기본값)를 사용하도록 설정합니다. 필요한 경우 Docker Desktop 메뉴에서 "Linux 컨테이너로 전환" 옵션을 선택하십시오.
1. Visual Studio에서 NET Core 3.1 콘솔 애플리케이션을 만드십시오.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. NuGet에서 최신 Aspose.GIS 버전을 설치합니다.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. 애플리케이션이 Linux에서 실행될 예정이므로 적절한 네이티브 Linux 자산을 설치해야 합니다. dotnet core sdk 3.1 기본 이미지를 시작하고 libgdiplus libc6-dev를 설치하십시오.
1. 필요한 모든 종속성을 추가하면 복합 곡선을 생성하는 간단한 프로그램을 작성합니다.<br>
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
                // 'S' 글자 생성 (하단 왼쪽 끝에서 시작)
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

참고: 출력 문서를 저장하기 위한 출력 폴더로 "TestOut" 폴더가 지정되어 있습니다. Docker에서 애플리케이션을 실행할 때 호스트 머신의 폴더가 컨테이너의 이 폴더에 마운트됩니다. 이렇게 하면 Docker 컨테이너에서 생성된 Aspose.GIS 출력을 쉽게 볼 수 있습니다.

### Dockerfile 구성

다음 단계는 Dockerfile을 만들고 구성하는 것입니다.

1. Dockerfile을 만들고 애플리케이션 솔루션 파일 옆에 놓습니다. 이 파일 이름은 확장자 없이 유지합니다(기본값).
1. Dockerfile에서 다음을 지정하십시오.

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

위는 다음과 같은 명령이 포함된 간단한 Dockerfile입니다.

- 사용할 SDK 이미지입니다. 여기서는 Net 3.1 이미지입니다. 빌드가 실행될 때 Docker에서 다운로드합니다. SDK 버전은 태그로 지정됩니다.
- 다음 줄에 지정된 작업 디렉터리입니다.
- libgdiplus를 설치하는 명령이 컨테이너에서 실행됩니다. System.Drawing.Common에 필요합니다.
- 모든 것을 컨테이너에 복사하고, 애플리케이션을 게시하고, 진입점을 지정하는 명령입니다.

### Docker에서 애플리케이션 빌드 및 실행

이제 애플리케이션을 Docker에서 빌드하고 실행할 수 있습니다. 좋아하는 명령 프롬프트를 열고 애플리케이션(솔루션 파일과 Dockerfile이 있는 폴더)이 있는 디렉토리로 변경한 다음 다음 명령을 실행합니다.

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

이 명령을 처음 실행하면 Docker에서 필요한 이미지를 다운로드해야 하므로 시간이 더 오래 걸릴 수 있습니다. 이전 명령이 완료되면 다음 명령을 실행하십시오.

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

마운트 인수에 주의하십시오. 앞서 언급했듯이 컨테이너의 애플리케이션 실행 결과를 쉽게 확인할 수 있도록 호스트 머신의 폴더가 컨테이너의 폴더에 마운트되기 때문입니다. Linux 경로는 대소문자를 구분합니다.

{{% /alert %}}


## 더 많은 예제

Aspose.GIS를 Docker에서 사용하는 방법에 대한 자세한 샘플은 [예제](https://github.com/aspose-gis/Aspose.Gis-for-.NET)를 참조하십시오.

## 참고

- [Windows에 Docker Desktop 설치](https://docs.docker.com/docker-for-windows/install/)
- [Mac에 Docker Desktop 설치](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [Linux 컨테이너로 전환](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) 옵션
- [.NET Core SDK]에 대한 추가 정보(https://hub.docker.com/_/microsoft-dotnet-sdk)
