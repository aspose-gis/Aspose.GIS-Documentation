---
title: "Встановлення"
second_title: Aspose.GIS for .NET
type: docs
url: /uk/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: Встановіть GIS C#.NET бібліотеку або API з NuGet за допомогою UI Package Manager або Console, із ZIP Archive. Також може бути використано в .NET Core та Linux OS.
---

## **Встановити Aspose.GIS**
### **З NuGet**
Щоб встановити Aspose.GIS, ви використовуєте або UI Package Manager, або Package Manager Console. Коли ви встановлюєте пакет, NuGet записує залежність у ваш файл проекту або файл packages.config.
#### **Package Manager UI**
1. У Solution Explorer клацніть правою кнопкою миші **References** та виберіть **Manage NuGet Packages**.

![todo:image_alt_text](installation_1.png)

1. Перевірте, чи вибрано "nuget.org" як **Package Source**, виберіть вкладку Browse, знайдіть Aspose.GIS, виберіть цей пакет зі списку та натисніть Install:

![todo:image_alt_text](installation_2.png)

1. Ознайомтеся з [Aspose End User License Agreement](https://about.aspose.com/legal/eula).
1. Якщо буде запропоновано переглянути зміни, виберіть **OK**.
#### **Package Manager Console**
1. Виберіть команду меню **Tools** > **NuGet Package Manager** > **Package Manager Console**.
1. Після відкриття консолі переконайтеся, що в спадному списку **Default project** відображається проект, у який ви хочете встановити пакет. Якщо у вашому рішенні є лише один проект, він вже вибраний.

![todo:image_alt_text](installation_3.png)

1. Введіть команду Install-Package Aspose.GIS. У вікні консолі буде показано вивід для команди.
### **З MSI Installer або ZIP Archive**
Як альтернатива встановленню NuGet, ви можете завантажити Aspose.GIS з [Downloads section](https://downloads.aspose.com/gis/net) у вигляді MSI installer або ZIP archive.
## **Інструкції для конкретних платформ**
### **Linux**
При використанні функціональності рендерингу карт Aspose.GIS під Linux переконайтеся, що бібліотека System.Drawing.Common налаштована правильно. Якщо ви отримаєте повідомлення про помилку, подібне до 

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

це означає, що залежності System.Drawing.Common відсутні в системі. Щоб виправити це, виконайте:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev
## **Системні вимоги для Aspose.GIS for .NET**
Усі компоненти Aspose .NET вимагають дозволу Full Trust permission set.

Aspose.GIS включає два варіанти збірки, створених для

- .NET Framework 4.7,
- .NET Standard 2.0.



### **.NET Framework v4.7 або новіша**
Операційні системи: 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `Підтримуються як 32-біт і 64-біт версії.
### **.NET Core v2.0 або новіша**
` `Операційні системи:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (версія 1607) або пізніші версії
- Microsoft Windows Server 2008 R2 SP1 (Full Server or Server Core), 2012 SP1 (Full Server or Server Core), 2012 R2 (Full Server or Server Core), 2016 або пізніші версії (Full Server, Server Core, or Nano Server)
- macOS 10.12 "Sierra" та пізніші версії
- Linux (64-bit, x86_64 або amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64-bit, arm32), 8.7 або пізніші версії
  - Ubuntu 18.04 (64-bit, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 або пізніші версії
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 або пізніші версії
  - Alpine Linux 3.7 або пізніші версії

Більше деталей доступно в .NET Core Guide: [Windows Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [macOS Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Linux Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **Експериментальна підтримка**
- Mono 5.4 або пізніша
- Xamarin:
  - Xamarin.iOS: версія 10.14 або пізніша
  - Xamarin.Android: версія 8.0 або пізніша
  - Xamarin.Mac: версія 3.8 або пізніша
