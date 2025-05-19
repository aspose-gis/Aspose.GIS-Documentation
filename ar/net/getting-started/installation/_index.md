---
title: "التثبيت"
second_title: Aspose.GIS لـ .NET
type: docs
url: /ar/net/installation/
weight: 40
keywords: مكتبة جيس C#، مكتبة جيس .NET
description: قم بتثبيت مكتبة أسبوز جيس ا for C#.NET أو API من NuGet باستخدام واجهة إدارة الحزم أو الوحدة النمطية لمدير الحزم، من الأرشيف المضغوط بتنسيق ZIP. يمكن استخدامه أيضًا في .NET Core ونظام تشغيل Linux.
---

## **تثبيت Aspose.GIS**
### **من NuGet**
لتثبيت Aspose.GIS، يمكنك استخدام إما واجهة إدارة الحزم أو الوحدة النمطية لمدير الحزم. عند تثبيت حزمة، يقوم NuGet بتسجيل التبعية إما في ملف المشروع الخاص بك أو ملف packages.config.
#### **واجهة إدارة الحزم**
1. في مستكشف الحلول، انقر بزر الماوس الأيمن على **المراجع** واختر **إدارة حزم NuGet**.

![todo:image_alt_text](installation_1.png)

1. تحقق من تحديد "nuget.org" كـ **مصدر الحزم**, اختر علامة التبويب المعرض، ابحث عن Aspose.GIS، حدد تلك الحزمة في القائمة، وانقر فوق تثبيت:

![todo:image_alt_text](installation_2.png)

1. اطّلع على [اتفاقية ترخيص مستخدم نهائي Aspose](https://about.aspose.com/legal/eula).
1. إذا طلبت منك مراجعة التغييرات، حدد **موافق**.
#### **وحدة التحكم لمدير الحزم**
1. حدد الأمر **Tools** > **مدير حزم NuGet** > **وحدة التحكم لمدير الحزم** من القائمة.
1. بعد فتح الوحدة، تأكد من أن قائمة السحب **المشروع الافتراضي** تظهر العمل الذي تريد تثبيت الحزمة فيه. إذا كان لديك مشروع واحد في الحل، فسيكون محددًا بالفعل.

![todo:image_alt_text](installation_3.png)

1. أدخل الأمر Install-Package Aspose.GIS. سيظهر نافذة الوحدة النمطية الناتج للأمر.
### **باستخدام برنامج التثبيت MSI أو من الأرشيف المضغوط بتنسيق ZIP**
كبديل لتثبيت NuGet، يمكنك تنزيل Aspose.GIS من [قسم التنزيلات](https://downloads.aspose.com/gis/net) بصيغة مثبت MSI أو أرشيف ZIP.
## **تعليمات خاصة بالمنصة**
### **Linux**
عند استخدام وظيفة رسم الخرائط لـ Aspose.GIS على Linux، تأكد أن مكتبة System.Drawing.Common مكونة بشكل صحيح. إذا حصلت على رسالة خطأ مشابهة لـ

"تم إلقاء استثناء من النوع المعدل 'Gdip' ---> System.DllNotFoundException: غير قادر على تحميل المكتبة المشتركة 'libdl' أو إحدى تبعياتها."

فإن هذا يعني أن تبعيات System.Drawing.Common مفقودة من النظام. لحل هذه المشكلة، قم بتشغيل:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev
## **متطلبات النظام لـ Aspose.GIS for .NET**
تتطلب جميع مكونات Aspose.NET وجود مجموعة إذن Full Trust.

تضم Aspose.GIS نوعين من التجميعات المبنية لـ

- .NET Framework 4.7,
- .NET Standard 2.0.

-----

### **.NET Framework v4.7 أو الأحدث**
أنظمة التشغيل: 

- Microsoft Windows 10، 8، 7 SP1
- Microsoft Windows Server 2016، 2012 R2، 2012، 2008 R2 SP1

` `كلا الإصدارين 32 بت و 64 بت مدعومان.
### **.NET Core v2.0 أو الأحدث**
` `أنظمة التشغيل:

- Microsoft Windows 7 SP1، 8.1، 10 Anniversary Update (الإصدار 1607) أو الإصدارات الأحدث
- Microsoft Windows Server 2008 R2 SP1 (نسخة كاملة أو Server Core)، 2012 SP1 (نسخة كاملة أو Server Core)، 2012 R2 (نسخة كاملة أو Server Core)، 2016 أو الإصدارات الأحدث (نسخة كاملة، Server Core، أو Nano Server)
- macOS 10.12 "Sierra" والإصدارات الأحدث
- Linux (بت 64، x86_64 أو amd64):
  - Red Hat Enterprise Linux 7، 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28، 27
  - Debian 9 (بت 64، arm32)، 8.7 أو الإصدارات الأحدث
  - Ubuntu 18.04 (بت 64، arm32)، 16.04، 14.04
  - Linux Mint 18، 17
  - openSUSE 42.3 أو الإصدارات الأحدث
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 أو الإصدارات الأحدث
  - Alpine Linux 3.7 أو الإصدارات الأحدث

المزيد من التفاصيل متوفرة في دليل .NET Core: [متطلبات Windows](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies)، [متطلبات macOS](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies)، [متطلبات Linux](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **الدعم التجريبي**
- Mono 5.4 أو الأحدث
- Xamarin:
  - Xamarin.iOS: الإصدار 10.14  أو الأحدث
  - Xamarin.Android: الإصدار 8.0 أو الأحدث
  - Xamarin.Mac: الإصدار 3.8 أو الأحدث
