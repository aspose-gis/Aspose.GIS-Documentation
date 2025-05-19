---
title: "Инсталация"
second_title: Aspose.GIS for .NET
type: docs
url: /bg/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: Инсталирайте GIS C#.NET библиотека или API от NuGet с помощта на Package Manager UI или Console, от ZIP архив. Тя може да се използва и в .NET Core и Linux OS.
---

## **Инсталиране на Aspose.GIS**
### **От NuGet**
За да инсталирате Aspose.GIS, можете да използвате или Package Manager UI, или Package Manager Console. Когато инсталирате пакет, NuGet записва зависимостта в проектния ви файл или в packages.config файл.
#### **Package Manager UI**
1. В Solution Explorer щракнете с десен бутон върху **References** и изберете **Manage NuGet Packages**.

![todo:image_alt_text](installation_1.png)

1. Уверете се, че "nuget.org" е избран като **Package Source**, изберете раздела Browse, потърсете Aspose.GIS, изберете пакета от списъка и щракнете върху Install:

![todo:image_alt_text](installation_2.png)

1. Запознайте се с [Лицензионното споразумение за краен потребител на Aspose](https://about.aspose.com/legal/eula).
1. Ако бъдете подканени да прегледате промените, изберете **OK**.
#### **Package Manager Console**
1. Изберете менюто **Tools** > **NuGet Package Manager** > **Package Manager Console**.
1. След като конзолата се отвори, уверете се, че падащият списък **Default project** показва проекта, в който искате да инсталирате пакета. Ако имате само един проект в решението, той вече е избран.

![todo:image_alt_text](installation_3.png)

1. Въведете командата Install-Package Aspose.GIS. Прозорецът на конзолата ще покаже изхода за командата.
### **С MSI Installer или от ZIP архив**
Като алтернатива на инсталацията чрез NuGet, можете да изтеглите Aspose.GIS от [раздел Downloads](https://downloads.aspose.com/gis/net) опакован като MSI installer или ZIP архив.
## **Инструкции специфични за платформата**
### **Linux**
Когато използвате функционалността за рендиране на карти на Aspose.GIS под Linux, уверете се, че библиотеката System.Drawing.Common е конфигурирана правилно. Ако получите съобщение за грешка подобно на 

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

това означава, че зависимостите на System.Drawing.Common липсват от системата. За да го поправите, изпълнете:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev
## **Системни изисквания за Aspose.GIS for .NET**
Всички компоненти на Aspose .NET изискват разрешение Full Trust permission set.

Aspose.GIS включва два варианта на асембли, компилирани за

- .NET Framework 4.7,
- .NET Standard 2.0.



### **.NET Framework v4.7 или по-нова**
Операционни системи: 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `И двете 32 и 64 битови версии се поддържат.
### **.NET Core v2.0 или по-нова**
` `Операционни системи:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (версия 1607) или по-нови версии
- Microsoft Windows Server 2008 R2 SP1 (Full Server или Server Core), 2012 SP1 (Full Server или Server Core), 2012 R2 (Full Server или Server Core), 2016 или по-нови версии (Full Server, Server Core, или Nano Server)
- macOS 10.12 "Sierra" и по-нови версии
- Linux (64-битов, x86_64 или amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64-битов, arm32), 8.7 или по-нови версии
  - Ubuntu 18.04 (64-битов, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 или по-нови версии
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 или по-нова
  - Alpine Linux 3.7 или по-нови версии

Повече подробности са достъпни в .NET Core Guide: [Windows Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [macOS Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Linux Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **Експериментална поддръжка**
- Mono 5.4 или по-нова
- Xamarin:
  - Xamarin.iOS: версия 10.14 или по-нова
  - Xamarin.Android: версия 8.0 или по-нова
  - Xamarin.Mac: версия 3.8 или по-нова
