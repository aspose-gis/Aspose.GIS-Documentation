---
title: "설치"
second_title: Aspose.GIS for .NET
type: docs
url: /ko/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: NuGet를 사용하여 패키지 관리자 UI 또는 콘솔에서 GIS C#.NET 라이브러리 또는 API를 설치하거나 ZIP 아카이브에서 설치합니다. 또한 .NET Core 및 Linux OS에서도 사용할 수 있습니다.
---

## **Aspose.GIS 설치**
### **NuGet에서**
Aspose.GIS를 설치하려면 패키지 관리자 UI 또는 패키지 관리자 콘솔을 사용합니다. 패키지를 설치하면 NuGet는 종속성을 프로젝트 파일 또는 packages.config 파일에 기록합니다.
#### **패키지 관리자 UI**
1. 솔루션 탐색기에서 **참조**를 마우스 오른쪽 버튼으로 클릭하고 **NuGet 패키지 관리**를 선택합니다.

![todo:image_alt_text](installation_1.png)

1. **패키지 소스**로 "nuget.org"가 선택되어 있는지 확인하고, **찾아보기** 탭을 선택하여 Aspose.GIS를 검색하고 목록에서 해당 패키지를 선택한 다음 **설치**를 클릭합니다.

![todo:image_alt_text](installation_2.png)

1. [Aspose 최종 사용자 라이선스 계약](https://about.aspose.com/legal/eula)을 숙지하십시오.
1. 변경 사항 검토 메시지가 표시되면 **확인**을 선택합니다.
#### **패키지 관리자 콘솔**
1. **도구** > **NuGet 패키지 관리자** > **패키지 관리자 콘솔** 메뉴 명령을 선택합니다.
1. 콘솔이 열리면 드롭다운 목록에서 **기본 프로젝트**가 패키지를 설치하려는 프로젝트를 가리키는지 확인합니다. 솔루션에 단일 프로젝트만 있는 경우 이미 선택되어 있습니다.

![todo:image_alt_text](installation_3.png)

1. Install-Package Aspose.GIS 명령을 입력합니다. 콘솔 창에 명령 출력 내용이 표시됩니다.
### **MSI 설치 프로그램 또는 ZIP 아카이브에서**
NuGet 설치 외에도 [다운로드 섹션](https://downloads.aspose.com/gis/net)에서 MSI 설치 프로그램 또는 ZIP 아카이브로 패키징된 Aspose.GIS를 다운로드할 수 있습니다.

## **플랫폼별 지침**
### **Linux**
Aspose.GIS의 맵 렌더링 기능을 Linux에서 사용하는 경우 System.Drawing.Common 라이브러리가 올바르게 구성되었는지 확인하십시오. "Gdip" 유형 초기화 프로그램이 예외를 발생시켰습니다. ---> System.DllNotFoundException: 공유 라이브러리 'libdl' 또는 해당 종속성을 로드할 수 없습니다."와 유사한 오류 메시지가 표시되면 시스템에서 System.Drawing.Common의 종속성이 누락된 것입니다. 이를 수정하려면 다음을 실행하십시오.

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev

## **Aspose.GIS for .NET에 대한 시스템 요구 사항**
모든 Aspose .NET 구성 요소에는 전체 신뢰 권한 세트가 필요합니다.

Aspose.GIS는 다음을 위해 빌드된 어셈블리의 두 가지 변형을 포함합니다.

- .NET Framework 4.7,
- .NET Standard 2.0.

### **.NET Framework v4.7 이상**
운영 체제: 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `32비트 및 64비트 버전 모두 지원됩니다.
### **.NET Core v2.0 이상**
` `운영 체제:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (버전 1607) 또는 이후 버전
- Microsoft Windows Server 2008 R2 SP1 (Full Server 또는 Server Core), 2012 SP1 (Full Server 또는 Server Core), 2012 R2 (Full Server 또는 Server Core), 2016 또는 이후 버전 (Full Server, Server Core 또는 Nano Server)
- macOS 10.12 "Sierra" 및 이후 버전
- Linux (64비트, x86_64 또는 amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64비트, arm32), 8.7 또는 이후 버전
  - Ubuntu 18.04 (64비트, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 또는 이후 버전
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 또는 이후 버전
  - Alpine Linux 3.7 또는 이후 버전

자세한 내용은 .NET Core 가이드에서 확인할 수 있습니다: [Windows 필수 구성 요소](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [macOS 필수 구성 요소](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Linux 필수 구성 요소](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **실험적 지원**
- Mono 5.4 이상
- Xamarin:
  - Xamarin.iOS: 버전 10.14 이후
  - Xamarin.Android: 버전 8.0 이후
  - Xamarin.Mac: 버전 3.8 이후
