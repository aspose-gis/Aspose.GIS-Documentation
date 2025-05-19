---
title: "Instalasi"
second_title: Aspose.GIS untuk .NET
type: docs
url: /id/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: Instal pustaka atau API GIS C#.NET dari NuGet menggunakan UI Package Manager atau Konsol, dari ZIP Archive. Ini juga dapat digunakan di .NET Core dan OS Linux.
---

## **Instal Aspose.GIS**
### **Dari NuGet**
Untuk menginstal Aspose.GIS, Anda menggunakan Package Manager UI atau Package Manager Console. Saat Anda menginstal paket, NuGet mencatat dependensi dalam file proyek Anda atau file packages.config.
#### **Package Manager UI**
1. Di Solution Explorer, klik kanan **References** dan pilih **Manage NuGet Packages**.

![todo:image_alt_text](installation_1.png)

1. Pastikan "nuget.org" dipilih sebagai **Package Source**, pilih tab Browse, cari Aspose.GIS, pilih paket tersebut dalam daftar, dan klik Install:

![todo:image_alt_text](installation_2.png)

1. Biasakan diri dengan [Aspose End User License Agreement](https://about.aspose.com/legal/eula).
1. Jika diminta untuk meninjau perubahan, pilih **OK**.
#### **Package Manager Console**
1. Pilih menu perintah **Tools** > **NuGet Package Manager** > **Package Manager Console**.
1. Setelah konsol terbuka, pastikan daftar drop-down **Default project** menunjukkan proyek tempat Anda ingin menginstal paket. Jika Anda memiliki satu proyek dalam solusi, itu sudah dipilih.

![todo:image_alt_text](installation_3.png)

1. Masukkan perintah Install-Package Aspose.GIS. Jendela konsol akan menampilkan output untuk perintah tersebut.
### **Dengan MSI Installer atau Dari ZIP Archive**
Sebagai alternatif untuk instalasi NuGet, Anda dapat mengunduh Aspose.GIS dari [Downloads section](https://downloads.aspose.com/gis/net) dikemas sebagai MSI installer atau ZIP archive.
## **Instruksi Spesifik Platform**
### **Linux**
Saat menggunakan fungsionalitas rendering peta Aspose.GIS di Linux, pastikan pustaka System.Drawing.Common dikonfigurasi dengan benar. Jika Anda mendapatkan pesan kesalahan seperti 

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

itu berarti bahwa dependensi dari System.Drawing.Common hilang dari sistem. Untuk memperbaikinya, jalankan:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev
## **System Requirements untuk Aspose.GIS untuk .NET**
Semua komponen Aspose .NET memerlukan izin set Full Trust.

Aspose.GIS menyertakan dua varian rakitan yang dibuat untuk

- .NET Framework 4.7,
- .NET Standard 2.0.

---
### **.NET Framework v4.7 atau lebih baru**
Sistem operasi: 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `Baik versi 32 dan 64 bit didukung.
### **.NET Core v2.0 atau lebih baru**
` `Sistem operasi:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (versi 1607) atau versi yang lebih baru
- Microsoft Windows Server 2008 R2 SP1 (Full Server atau Server Core), 2012 SP1 (Full Server atau Server Core), 2012 R2 (Full Server atau Server Core), 2016 atau versi yang lebih baru (Full Server, Server Core, atau Nano Server)
- macOS 10.12 "Sierra" dan versi yang lebih baru
- Linux (64-bit, x86_64 atau amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64-bit, arm32), 8.7 atau versi yang lebih baru
  - Ubuntu 18.04 (64-bit, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 atau versi yang lebih baru
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 atau versi yang lebih baru
  - Alpine Linux 3.7 atau versi yang lebih baru

Lebih detail tersedia di .NET Core Guide: [Windows Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [macOS Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Linux Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **Experimental Support**
- Mono 5.4 atau lebih baru
- Xamarin:
  - Xamarin.iOS: versi 10.14 atau lebih baru
  - Xamarin.Android: versi 8.0 atau lebih baru
  - Xamarin.Mac: versi 3.8 atau lebih baru
