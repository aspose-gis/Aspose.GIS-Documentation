---
title: "การติดตั้ง"
second_title: Aspose.GIS for .NET
type: docs
url: /th/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: ติดตั้ง GIS C#.NET library หรือ API จาก NuGet โดยใช้ Package Manager UI หรือ Console จาก ZIP Archive นอกจากนี้ยังสามารถใช้งานได้ใน .NET Core และระบบปฏิบัติการ Linux
---

## **ติดตั้ง Aspose.GIS**
### **จาก NuGet**
หากต้องการติดตั้ง Aspose.GIS คุณสามารถใช้ Package Manager UI หรือ Package Manager Console เมื่อคุณติดตั้งแพ็กเกจ NuGet จะบันทึก dependency ในไฟล์โปรเจกต์ของคุณหรือไฟล์ packages.config
#### **Package Manager UI**
1. ใน Solution Explorer คลิกขวาที่ **References** และเลือก **Manage NuGet Packages**.

![todo:image_alt_text](installation_1.png)

1. ตรวจสอบให้แน่ใจว่าได้เลือก "nuget.org" เป็น **Package Source** เลือกแท็บ Browse ค้นหา Aspose.GIS เลือกแพ็กเกจนั้นในรายการ และคลิก Install:

![todo:image_alt_text](installation_2.png)

1. ทำความคุ้นเคยกับ [Aspose End User License Agreement](https://about.aspose.com/legal/eula).
1. หากระบบแจ้งให้ตรวจสอบการเปลี่ยนแปลง ให้เลือก **OK**.
#### **Package Manager Console**
1. เลือกเมนูคำสั่ง **Tools** > **NuGet Package Manager** > **Package Manager Console**.
1. หลังจากเปิดคอนโซล ตรวจสอบให้แน่ใจว่ารายการแบบหล่นลง **Default project** แสดงโปรเจกต์ที่คุณต้องการติดตั้งแพ็กเกจ หากคุณมีเพียงโปรเจกต์เดียวใน solution ก็จะถูกเลือกไว้แล้ว

![todo:image_alt_text](installation_3.png)

1. ป้อนคำสั่ง Install-Package Aspose.GIS หน้าต่างคอนโซลจะแสดงผลลัพธ์สำหรับคำสั่ง
### **ด้วย MSI Installer หรือจาก ZIP Archive**
นอกเหนือจากการติดตั้ง NuGet คุณสามารถดาวน์โหลด Aspose.GIS จาก [Downloads section](https://downloads.aspose.com/gis/net) ในรูปแบบของ MSI installer หรือ ZIP archive

## **คำแนะนำเฉพาะแพลตฟอร์ม**
### **Linux**
เมื่อใช้ฟังก์ชันการแสดงผลแผนที่ของ Aspose.GIS ภายใต้ Linux ตรวจสอบให้แน่ใจว่าได้กำหนดค่า System.Drawing.Common library อย่างถูกต้อง หากคุณได้รับข้อความผิดพลาดที่คล้ายกับ

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

หมายความว่า dependency ของ System.Drawing.Common หายไปจากระบบ ในการแก้ไข ให้รัน:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev
## **ข้อกำหนดของระบบสำหรับ Aspose.GIS for .NET**
ส่วนประกอบ Aspose .NET ทั้งหมดต้องการชุดสิทธิ์ Full Trust

Aspose.GIS มีรูปแบบการประกอบสองแบบที่สร้างขึ้นสำหรับ:

- .NET Framework 4.7,
- .NET Standard 2.0.

-----
### **.NET Framework v4.7 หรือใหม่กว่า**
ระบบปฏิบัติการ:

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `รองรับทั้งเวอร์ชัน 32 และ 64 บิต
### **.NET Core v2.0 หรือใหม่กว่า**
` `ระบบปฏิบัติการ:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (version 1607) หรือเวอร์ชันที่ใหม่กว่า
- Microsoft Windows Server 2008 R2 SP1 (Full Server หรือ Server Core), 2012 SP1 (Full Server หรือ Server Core), 2012 R2 (Full Server หรือ Server Core), 2016 หรือเวอร์ชันที่ใหม่กว่า (Full Server, Server Core, หรือ Nano Server)
- macOS 10.12 "Sierra" และเวอร์ชันที่ใหม่กว่า
- Linux (64 บิต, x86_64 หรือ amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64 บิต, arm32), 8.7 หรือเวอร์ชันที่ใหม่กว่า
  - Ubuntu 18.04 (64 บิต, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 หรือเวอร์ชันที่ใหม่กว่า
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 หรือเวอร์ชันที่ใหม่กว่า
  - Alpine Linux 3.7 หรือเวอร์ชันที่ใหม่กว่า

รายละเอียดเพิ่มเติมมีอยู่ใน .NET Core Guide: [Windows Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [macOS Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Linux Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **Experimental Support**
- Mono 5.4 หรือใหม่กว่า
- Xamarin:
  - Xamarin.iOS: version 10.14 หรือใหม่กว่า
  - Xamarin.Android: version 8.0 หรือใหม่กว่า
  - Xamarin.Mac: version 3.8 หรือใหม่กว่า
