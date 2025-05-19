---
title: "نصب"
second_title: Aspose.GIS for .NET
type: docs
url: /fa/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: نصب کتابخانه GIS C#.NET یا API از NuGet با استفاده از رابط کاربری Package Manager یا Console، از ZIP Archive. همچنین می تواند در .NET Core و سیستم عامل Linux استفاده شود.
---

## **نصب Aspose.GIS**
### **از NuGet**
برای نصب Aspose.GIS، شما از رابط کاربری Package Manager یا کنسول Package Manager استفاده می کنید. هنگامی که یک بسته را نصب می کنید، NuGet وابستگی را در فایل پروژه خود یا یک فایل packages.config ثبت می کند.
#### **رابط کاربری Package Manager**
1. در Solution Explorer، روی **References** راست کلیک کرده و **Manage NuGet Packages** را انتخاب کنید.

![todo:image_alt_text](installation_1.png)

1. بررسی کنید که "nuget.org" به عنوان **Package Source** انتخاب شده باشد، تب Browse را انتخاب کنید، Aspose.GIS را جستجو کنید، بسته را در لیست انتخاب کرده و روی Install کلیک کنید:

![todo:image_alt_text](installation_2.png)

1. با [Aspose End User License Agreement](https://about.aspose.com/legal/eula) آشنا شوید.
1. اگر از شما خواسته شد تغییرات را بررسی کنید، **OK** را انتخاب کنید.
#### **Package Manager Console**
1. دستور **Tools** > **NuGet Package Manager** > **Package Manager Console** را انتخاب کنید.
1. پس از باز شدن کنسول، اطمینان حاصل کنید که لیست کشویی **Default project** پروژه ای را نشان می دهد که می خواهید بسته را در آن نصب کنید. اگر یک پروژه واحد در راه حل دارید، قبلاً انتخاب شده است.

![todo:image_alt_text](installation_3.png)

1. دستور Install-Package Aspose.GIS را وارد کنید. پنجره کنسول خروجی مربوط به دستور را نشان می دهد.
### **با MSI Installer یا از ZIP Archive**
به عنوان جایگزینی برای نصب NuGet، می توانید Aspose.GIS را از [Downloads section](https://downloads.aspose.com/gis/net) با بسته بندی MSI installer یا ZIP archive دانلود کنید.

## **دستورالعمل های خاص پلتفرم**
### **Linux**
هنگام استفاده از عملکرد نقشه برداری Aspose.GIS در Linux، اطمینان حاصل کنید که کتابخانه System.Drawing.Common به درستی پیکربندی شده است. اگر پیام خطایی مشابه زیر دریافت می کنید:

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

به این معنی است که وابستگی های System.Drawing.Common از سیستم گم شده اند. برای رفع آن، اجرا کنید:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev

## **سیستم مورد نیاز Aspose.GIS for .NET**
همه اجزای Aspose .NET به مجموعه مجوز Full Trust نیاز دارند.

Aspose.GIS شامل دو نوع از اسمبلی است که برای موارد زیر ساخته شده اند:

- .NET Framework 4.7،
- .NET Standard 2.0.

### **.NET Framework v4.7 یا بالاتر**
سیستم عامل ها:

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` ` هر دو نسخه 32 و 64 بیتی پشتیبانی می شوند.
### **.NET Core v2.0 یا بالاتر**
` ` سیستم عامل ها:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (version 1607) or later versions
- Microsoft Windows Server 2008 R2 SP1 (Full Server or Server Core), 2012 SP1 (Full Server or Server Core), 2012 R2 (Full Server or Server Core), 2016 or later versions (Full Server, Server Core, or Nano Server)
- macOS 10.12 "Sierra" and later versions
- Linux (64-bit, x86_64 or amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64-bit, arm32), 8.7 or later versions
  - Ubuntu 18.04 (64-bit, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 or later versions
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later

More details available in the .NET Core Guide: [Windows Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [macOS Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Linux Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).

### **پشتیبانی آزمایشی**
- Mono 5.4 یا بالاتر
- Xamarin:
  - Xamarin.iOS: version 10.14 or later
  - Xamarin.Android: version 8.0 or later
  - Xamarin.Mac: version 3.8 or later
