---
title: "安装"
second_title: Aspose.GIS for .NET
type: docs
url: /zh/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: 使用包管理器 UI 或控制台从 NuGet 安装 GIS C#.NET 库或 API，或者从 ZIP 压缩包安装。它也可以在 .NET Core 和 Linux OS 上使用。
---

## **安装 Aspose.GIS**
### **来自 NuGet**
要安装 Aspose.GIS，您可以使用包管理器 UI 或包管理器控制台。当您安装一个包时，NuGet 会将依赖关系记录在您的项目文件或 packages.config 文件中。
#### **包管理器 UI**
1. 在解决方案资源管理器中，右键单击“引用”，然后选择“管理 NuGet 包”。

![todo:image_alt_text](installation_1.png)

1. 检查是否选择了 “nuget.org” 作为“程序包源”，选择浏览选项卡，搜索 Aspose.GIS，在列表中选择该包，然后单击安装：

![todo:image_alt_text](installation_2.png)

1. 熟悉 [Aspose 最终用户许可协议](https://about.aspose.com/legal/eula)。
1. 如果系统提示您查看更改，请选择“确定”。
#### **包管理器控制台**
1. 选择“工具”>“NuGet 包管理器”>“包管理器控制台”菜单命令。
1. 在控制台打开后，确保“默认项目”下拉列表显示您想要安装该包的项目。如果解决方案中只有一个项目，则已自动选中它。

![todo:image_alt_text](installation_3.png)

1. 输入命令 Install-Package Aspose.GIS。控制台窗口将显示命令的输出。
### **使用 MSI 安装程序或从 ZIP 压缩包**
作为 NuGet 安装程序的替代方法，您可以从 [下载部分](https://downloads.aspose.com/gis/net) 下载 Aspose.GIS，该软件打包为 MSI 安装程序或 ZIP 压缩包。

## **特定平台说明**
### **Linux**
在使用 Aspose.GIS 在 Linux 下的地图渲染功能时，请确保 System.Drawing.Common 库已正确配置。 如果您收到类似于以下消息的错误：

“Gdip 的类型初始化器引发了异常。---> System.DllNotFoundException: 无法加载共享库 'libdl' 或其依赖项之一。”

这意味着 System.Drawing.Common 的依赖项缺失于系统中。 要解决此问题，请运行：

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev

## **Aspose.GIS for .NET 的系统要求**
所有 Aspose .NET 组件都需要完全信任权限集。

Aspose.GIS 包含为以下内容构建的程序集的两种变体：

- .NET Framework 4.7，
- .NET Standard 2.0。

### **.NET Framework v4.7 或更高版本**
操作系统：

- Microsoft Windows 10、8、7 SP1
- Microsoft Windows Server 2016、2012 R2、2012、2008 R2 SP1

` `支持 32 位和 64 位版本。
### **.NET Core v2.0 或更高版本**
` `操作系统：

- Microsoft Windows 7 SP1、8.1、10 Anniversary Update（版本 1607）或更高版本
- Microsoft Windows Server 2008 R2 SP1 (Full Server 或 Server Core)、2012 SP1 (Full Server 或 Server Core)、2012 R2 (Full Server 或 Server Core)、2016 或更高版本（Full Server、Server Core 或 Nano Server）
- macOS 10.12 "Sierra" 及更高版本
- Linux（64 位，x86_64 或 amd64）：
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64 位，arm32), 8.7 或更高版本
  - Ubuntu 18.04 (64 位，arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 或更高版本
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 或更高版本
  - Alpine Linux 3.7 或更高版本

更多详细信息请参阅 .NET Core 指南：[Windows 先决条件](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies)、[macOS 先决条件](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies)、[Linux 先决条件](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x)。
### **实验性支持**
- Mono 5.4 或更高版本
- Xamarin：
  - Xamarin.iOS: 版本 10.14 或更高版本
  - Xamarin.Android: 版本 8.0 或更高版本
  - Xamarin.Mac: 版本 3.8 或更高版本
