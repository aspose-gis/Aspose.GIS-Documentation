---
title: "Kurulum"
second_title: Aspose.GIS for .NET
type: docs
url: /tr/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: GIS C#.NET kütüphanesini veya API'sini NuGet kullanarak Paket Yöneticisi UI veya Konsol aracılığıyla veya ZIP Arşivinden yükleyin. Ayrıca .NET Core ve Linux İşletim Sistemlerinde de kullanılabilir.
---

## **Aspose.GIS Kurulumu**
### **NuGet'ten**
Aspose.GIS'i kurmak için Paket Yöneticisi UI veya Paket Yöneticisi Konsolunu kullanırsınız. Bir paketi yüklediğinizde, NuGet bağımlılığı projeniz dosyasına veya packages.config dosyasına kaydeder.
#### **Paket Yöneticisi UI**
1. Çözüm Gezgini'nde **Referanslar** üzerine sağ tıklayın ve **NuGet Paketlerini Yönet** seçeneğini seçin.

![todo:image_alt_text](installation_1.png)

1. **Paket Kaynağı** olarak "nuget.org"un seçili olduğundan emin olun, Gözat sekmesini seçin, Aspose.GIS'i arayın, listedeki paketi seçin ve Yükle'ye tıklayın:

![todo:image_alt_text](installation_2.png)

1. [Aspose Kullanıcı Lisans Sözleşmesi](https://about.aspose.com/legal/eula) ile tanışın.
1. Değişiklikleri incelemeniz istenirse **Tamam** seçeneğini belirleyin.
#### **Paket Yöneticisi Konsolu**
1. **Araçlar** > **NuGet Paket Yöneticisi** > **Paket Yöneticisi Konsolu** menü komutunu seçin.
1. Konsol açıldıktan sonra, **Varsayılan proje** açılır listesinin paketi yüklemek istediğiniz projeyi gösterdiğinden emin olun. Çözümde tek bir projeniz varsa zaten seçilidir.

![todo:image_alt_text](installation_3.png)

1. Install-Package Aspose.GIS komutunu girin. Konsol penceresi komut için çıktı gösterecektir.
### **MSI Kurulumu veya ZIP Arşivinden**
NuGet kurulumuna alternatif olarak, Aspose.GIS'i [İndirmeler bölümü](https://downloads.aspose.com/gis/net)nden MSI kurulum dosyası veya ZIP arşivi olarak indirebilirsiniz.

## **Platforma Özgü Talimatlar**
### **Linux**
Aspose.GIS'in map rendering işlevselliğini Linux altında kullanırken, System.Drawing.Common kütüphanesinin doğru yapılandırıldığından emin olun. "Gdip" başlatıcısı için bir istisna oluştuğuna benzer bir hata mesajı alırsanız. ---> System.DllNotFoundException: Paylaşımlı kitaplık 'libdl' veya bağımlılıklarından biri yüklenemiyor."

bu, System.Drawing.Common bağımlılıklarının sistemden eksik olduğu anlamına gelir. Bunu düzeltmek için şunu çalıştırın:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev

## **Aspose.GIS for .NET için Sistem Gereksinimleri**
Tüm Aspose .NET bileşenleri Tam Güven izni kümesi gerektirir.

Aspose.GIS, şunlar için oluşturulmuş iki varyant içerir:

- .NET Framework 4.7,
- .NET Standard 2.0.

### **.NET Framework v4.7 veya daha yeni**
İşletim sistemleri: 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `Hem 32 hem de 64 bit sürümleri desteklenir.
### **.NET Core v2.0 veya daha yeni**
` `İşletim sistemleri:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (sürüm 1607) veya sonraki sürümleri
- Microsoft Windows Server 2008 R2 SP1 (Tam Sunucu veya Sunucu Çekirdeği), 2012 SP1 (Tam Sunucu veya Sunucu Çekirdeği), 2012 R2 (Tam Sunucu veya Sunucu Çekirdeği), 2016 veya sonraki sürümleri (Tam Sunucu, Sunucu Çekirdeği veya Nano Sunucu)
- macOS 10.12 "Sierra" ve sonraki sürümleri
- Linux (64-bit, x86_64 veya amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64-bit, arm32), 8.7 veya sonraki sürümleri
  - Ubuntu 18.04 (64-bit, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 veya sonraki sürümleri
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 veya sonraki sürümleri
  - Alpine Linux 3.7 veya sonraki sürümleri

Daha fazla ayrıntı .NET Core Kılavuzu'nda mevcuttur: [Windows Önkoşulları](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [macOS Önkoşulları](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Linux Önkoşulları](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).

### **Deneysel Destek**
- Mono 5.4 veya daha yeni
- Xamarin:
  - Xamarin.iOS: sürüm 10.14 veya sonraki sürümleri
  - Xamarin.Android: sürüm 8.0 veya sonraki sürümleri
  - Xamarin.Mac: sürüm 3.8 veya sonraki sürümleri
