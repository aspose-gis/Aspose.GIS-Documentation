---
title: "Instalace"
second_title: Aspose.GIS for .NET
type: docs
url: /cs/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: Nainstalujte knihovnu nebo API GIS C#.NET z NuGet pomocí uživatelského rozhraní správce balíčků nebo konzole, ze ZIP archivu. Může být také použita v .NET Core a OS Linux.
---

## **Instalace Aspose.GIS**
### **Z NuGet**
Pro instalaci Aspose.GIS používáte buď uživatelské rozhraní správce balíčků, nebo konzoli správce balíčků. Když nainstalujete balíček, NuGet zaznamená závislost do souboru projektu nebo souboru packages.config.
#### **Uživatelské rozhraní Správce balíčků**
1. V Průzkumníku řešení klikněte pravým tlačítkem na **References** a zvolte **Manage NuGet Packages**.

![todo:image_alt_text](installation_1.png)

1. Zkontrolujte, zda je jako **Package Source** vybráno "nuget.org", vyberte kartu Browse, vyhledejte Aspose.GIS, vyberte tento balíček ze seznamu a klikněte na Install:

![todo:image_alt_text](installation_2.png)

1. Seznamte se s [Aspose End User License Agreement](https://about.aspose.com/legal/eula).
1. Pokud budete vyzváni k přezkoumání změn, vyberte **OK**.
#### **Konzole Správce balíčků**
1. Vyberte příkaz menu **Tools** > **NuGet Package Manager** > **Package Manager Console**.
1. Po otevření konzole se ujistěte, že rozbalovací seznam **Default project** zobrazuje projekt, do kterého chcete nainstalovat balíček. Pokud máte v řešení pouze jeden projekt, je již vybrán.

![todo:image_alt_text](installation_3.png)

1. Zadejte příkaz Install-Package Aspose.GIS. Okno konzole zobrazí výstup pro tento příkaz.
### **S MSI instalačním programem nebo ze ZIP archivu**
Jako alternativa k instalaci NuGet můžete stáhnout Aspose.GIS z [sekce Downloads](https://downloads.aspose.com/gis/net) zabalené jako MSI instalační program nebo ZIP archiv.

## **Platformově specifické instrukce**
### **Linux**
Při používání funkce vykreslování map Aspose.GIS v Linuxu se ujistěte, že je knihovna System.Drawing.Common správně nakonfigurována. Pokud obdržíte chybovou zprávu podobnou

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

znamená to, že závislosti System.Drawing.Common chybí v systému. Pro opravu spusťte:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev

## **Systémové požadavky pro Aspose.GIS for .NET**
Všechny komponenty Aspose .NET vyžadují oprávnění Full Trust.

Aspose.GIS obsahuje dvě varianty sestavení vytvořené pro

- .NET Framework 4.7,
- .NET Standard 2.0.

### **.NET Framework v4.7 nebo novější**
Operační systémy: 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `Podporovány jsou jak 32bitové, tak 64bitové verze.
### **.NET Core v2.0 nebo novější**
` `Operační systémy:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (verze 1607) nebo novější verze
- Microsoft Windows Server 2008 R2 SP1 (Full Server or Server Core), 2012 SP1 (Full Server or Server Core), 2012 R2 (Full Server or Server Core), 2016 nebo novější verze (Full Server, Server Core, or Nano Server)
- macOS 10.12 "Sierra" a novější verze
- Linux (64bitový, x86_64 nebo amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64bitový, arm32), 8.7 nebo novější verze
  - Ubuntu 18.04 (64bitový, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 nebo novější verze
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 nebo novější

More details available in the .NET Core Guide: [Windows Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [macOS Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Linux Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **Experimentální podpora**
- Mono 5.4 nebo novější
- Xamarin:
  - Xamarin.iOS: verze 10.14 nebo novější
  - Xamarin.Android: verze 8.0 nebo novější
  - Xamarin.Mac: verze 3.8 nebo novější
