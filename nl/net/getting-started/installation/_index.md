---
title: "Installatie"
second_title: Aspose.GIS voor .NET
type: docs
url: /nl/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: Installeer GIS C#.NET bibliotheek of API van NuGet met behulp van Package Manager UI of Console, van ZIP Archive. Het kan ook worden gebruikt in .NET Core en Linux OS.
---

## **Installeer Aspose.GIS**
### **Van NuGet**
Om Aspose.GIS te installeren, kunt u de Package Manager UI of de Package Manager Console gebruiken. Wanneer u een pakket installeert, registreert NuGet de afhankelijkheid in uw projectbestand of een packages.config-bestand.
#### **Package Manager UI**
1. Klik met de rechtermuisknop op **References** in Solution Explorer en kies **Manage NuGet Packages**.

![todo:image_alt_text](installation_1.png)

1. Controleer of "nuget.org" is geselecteerd als de **Package Source**, selecteer het tabblad Browse, zoek naar Aspose.GIS, selecteer dat pakket in de lijst en klik op Installeren:

![todo:image_alt_text](installation_2.png)

1. Maak uzelf vertrouwd met de [Aspose End User License Agreement](https://about.aspose.com/legal/eula).
1. Als u wordt gevraagd om wijzigingen te bekijken, selecteer **OK**.
#### **Package Manager Console**
1. Selecteer het menucommando **Tools** > **NuGet Package Manager** > **Package Manager Console**.
1. Nadat de console is geopend, zorgt u ervoor dat de drop-downlijst **Default project** het project weergeeft waarin u het pakket wilt installeren. Als u slechts één project in de oplossing hebt, is deze al geselecteerd.

![todo:image_alt_text](installation_3.png)

1. Voer het commando Install-Package Aspose.GIS in. Het consolevenster toont uitvoer voor het commando.
### **Met MSI Installer of Van ZIP Archive**
Als alternatief voor de NuGet-installatie kunt u Aspose.GIS downloaden van [Downloads section](https://downloads.aspose.com/gis/net) verpakt als een MSI-installer of ZIP-archief.
## **Platformspecifieke instructies**
### **Linux**
Wanneer u de kaartrenderingfunctionaliteit van Aspose.GIS onder Linux gebruikt, zorgt u ervoor dat de System.Drawing.Common bibliotheek correct is geconfigureerd. Als u een foutmelding krijgt die lijkt op

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

betekent dit dat de afhankelijkheden van System.Drawing.Common ontbreken in het systeem. Om dit te verhelpen, voert u uit:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev
## **Systeemvereisten voor Aspose.GIS voor .NET**
Alle Aspose .NET componenten vereisen een Full Trust permission set.

Aspose.GIS bevat twee varianten van de assembly die zijn gebouwd voor

- .NET Framework 4.7,
- .NET Standard 2.0.



### **.NET Framework v4.7 of later**
Besturingssystemen: 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `Zowel de 32-bits als de 64-bits versies worden ondersteund.
### **.NET Core v2.0 of later**
` `Besturingssystemen:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (versie 1607) of latere versies
- Microsoft Windows Server 2008 R2 SP1 (Full Server of Server Core), 2012 SP1 (Full Server of Server Core), 2012 R2 (Full Server of Server Core), 2016 of latere versies (Full Server, Server Core, of Nano Server)
- macOS 10.12 "Sierra" en latere versies
- Linux (64-bit, x86_64 of amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64-bit, arm32), 8.7 of latere versies
  - Ubuntu 18.04 (64-bit, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 of latere versies
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 of later
  - Alpine Linux 3.7 of latere versies

Meer details zijn beschikbaar in de .NET Core Guide: [Windows Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [macOS Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Linux Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **Experimentele Ondersteuning**
- Mono 5.4 of later
- Xamarin:
  - Xamarin.iOS: versie 10.14 of later
  - Xamarin.Android: versie 8.0 of later
  - Xamarin.Mac: versie 3.8 of later
