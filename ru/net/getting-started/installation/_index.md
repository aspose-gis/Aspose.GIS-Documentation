---
title: "Установка"
second_title: Aspose.GIS for .NET
type: docs
url: /ru/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: Установите GIS C#.NET библиотеку или API из NuGet с помощью UI Package Manager или Console, из ZIP Archive. Ее также можно использовать в .NET Core и Linux OS.
---

## **Установка Aspose.GIS**
### **Из NuGet**
Для установки Aspose.GIS вы можете использовать либо UI Package Manager, либо Package Manager Console. При установке пакета NuGet записывает зависимость в ваш проект файл или файл packages.config.
#### **Package Manager UI**
1. В Solution Explorer щелкните правой кнопкой мыши **References** и выберите **Manage NuGet Packages**.

![todo:image_alt_text](installation_1.png)

1. Убедитесь, что "nuget.org" выбран в качестве **Package Source**, перейдите на вкладку Browse, найдите Aspose.GIS, выберите этот пакет из списка и нажмите Install:

![todo:image_alt_text](installation_2.png)

1. Ознакомьтесь с [Лицензионным соглашением конечного пользователя Aspose](https://about.aspose.com/legal/eula).
1. Если будет предложено просмотреть изменения, выберите **OK**.
#### **Package Manager Console**
1. Выберите команду меню **Tools** > **NuGet Package Manager** > **Package Manager Console**.
1. После открытия консоли убедитесь, что в раскрывающемся списке **Default project** отображается проект, в который вы хотите установить пакет. Если в решении есть только один проект, он уже выбран.

![todo:image_alt_text](installation_3.png)

1. Введите команду Install-Package Aspose.GIS. Окно консоли покажет вывод команды.
### **С MSI Installer или из ZIP Archive**
В качестве альтернативы установке NuGet вы можете загрузить Aspose.GIS из [раздела Downloads](https://downloads.aspose.com/gis/net) в виде MSI installer или ZIP archive.
## **Инструкции для конкретных платформ**
### **Linux**
При использовании функциональности рендеринга карт Aspose.GIS под Linux убедитесь, что библиотека System.Drawing.Common настроена правильно. Если вы получаете сообщение об ошибке типа 

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

это означает, что зависимости System.Drawing.Common отсутствуют в системе. Чтобы исправить это, выполните:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev
## **Системные требования для Aspose.GIS for .NET**
Все компоненты Aspose .NET требуют набора разрешений Full Trust.

Aspose.GIS включает в себя два варианта сборки, созданные для

- .NET Framework 4.7,
- .NET Standard 2.0.

### **.NET Framework v4.7 или новее**
Операционные системы: 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `Поддерживаются как 32-битные, так и 64-битные версии.
### **.NET Core v2.0 или новее**
` `Операционные системы:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (version 1607) или более поздние версии
- Microsoft Windows Server 2008 R2 SP1 (Full Server or Server Core), 2012 SP1 (Full Server or Server Core), 2012 R2 (Full Server or Server Core), 2016 или более поздние версии (Full Server, Server Core, or Nano Server)
- macOS 10.12 "Sierra" и более поздние версии
- Linux (64-bit, x86_64 or amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64-bit, arm32), 8.7 или более поздние версии
  - Ubuntu 18.04 (64-bit, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 или более поздние версии
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 или более поздние версии
  - Alpine Linux 3.7 или более поздние версии

Более подробная информация доступна в .NET Core Guide: [Windows Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [macOS Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Linux Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **Экспериментальная поддержка**
- Mono 5.4 или новее
- Xamarin:
  - Xamarin.iOS: version 10.14  or later
  - Xamarin.Android: version 8.0 or later
  - Xamarin.Mac: version 3.8 or later
