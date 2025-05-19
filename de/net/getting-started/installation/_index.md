---
title: "Installation"
second_title: Aspose.GIS for .NET
type: docs
url: /de/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: Install GIS C#.NET Bibliothek oder API von NuGet mit Package Manager UI oder Konsole, aus ZIP-Archiv. Es kann auch in .NET Core und Linux OS verwendet werden.
---

## **Installieren Sie Aspose.GIS**
### **Von NuGet**
Um Aspose.GIS zu installieren, verwenden Sie entweder die Package Manager UI oder die Package Manager Console. Wenn Sie ein Paket installieren, speichert NuGet die Abhängigkeit entweder in Ihrer Projektdatei oder in einer packages.config-Datei.
#### **Package Manager UI**
1. Klicken Sie im Solution Explorer mit der rechten Maustaste auf **References** und wählen Sie **Manage NuGet Packages**.

![todo:image_alt_text](installation_1.png)

1. Stellen Sie sicher, dass "nuget.org" als **Paketquelle** ausgewählt ist, wählen Sie den Browse-Tab, suchen Sie nach Aspose.GIS, wählen Sie dieses Paket in der Liste aus und klicken Sie auf Installieren:

![todo:image_alt_text](installation_2.png)

1. Machen Sie sich mit der [Aspose End User License Agreement](https://about.aspose.com/legal/eula) vertraut.
1. Wenn Sie aufgefordert werden, die Änderungen zu überprüfen, wählen Sie **OK**.
#### **Package Manager Console**
1. Wählen Sie den Befehl **Tools** > **NuGet Package Manager** > **Package Manager Console** im Menü.
1. Nachdem sich die Konsole geöffnet hat, stellen Sie sicher, dass das Dropdown-Menü **Standardprojekt** das Projekt anzeigt, in das Sie das Paket installieren möchten. Wenn Sie nur ein Projekt in der Lösung haben, ist es bereits ausgewählt.

![todo:image_alt_text](installation_3.png)

1. Geben Sie den Befehl Install-Package Aspose.GIS ein. Das Konsolenfenster zeigt die Ausgabe für den Befehl an.
### **Mit MSI Installer oder aus ZIP-Archiv**
Als Alternative zur NuGet-Installation können Sie Aspose.GIS aus dem [Downloads section](https://downloads.aspose.com/gis/net) als MSI-Installer oder ZIP-Archiv herunterladen.
## **Plattformspezifische Anweisungen**
### **Linux**
Wenn Sie die Kartenrenderfunktion von Aspose.GIS unter Linux verwenden, stellen Sie sicher, dass die System.Drawing.Common Bibliothek korrekt konfiguriert ist. Wenn Sie eine Fehlermeldung ähnlich wie 

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

erhalten, bedeutet dies, dass Abhängigkeiten von System.Drawing.Common dem System fehlen. Um dies zu beheben, führen Sie aus:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev
## **Systemanforderungen für Aspose.GIS for .NET**
Alle Aspose .NET Komponenten erfordern eine Full Trust Berechtigungsmenge.

Aspose.GIS enthält zwei Varianten der Assembly, die erstellt wurden für:

- .NET Framework 4.7,
- .NET Standard 2.0.

### **.NET Framework v4.7 oder höher**
Betriebssysteme: 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `Sowohl 32- als auch 64-Bit-Versionen werden unterstützt.
### **.NET Core v2.0 oder höher**
` `Betriebssysteme:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (Version 1607) oder spätere Versionen
- Microsoft Windows Server 2008 R2 SP1 (Full Server oder Server Core), 2012 SP1 (Full Server oder Server Core), 2012 R2 (Full Server oder Server Core), 2016 oder spätere Versionen (Full Server, Server Core oder Nano Server)
- macOS 10.12 "Sierra" und spätere Versionen
- Linux (64-Bit, x86_64 oder amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64-Bit, arm32), 8.7 oder spätere Versionen
  - Ubuntu 18.04 (64-Bit, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 oder spätere Versionen
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 oder später
  - Alpine Linux 3.7 oder spätere Versionen

Weitere Details finden Sie im .NET Core Guide: [Windows Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [macOS Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Linux Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **Experimentelle Unterstützung**
- Mono 5.4 oder höher
- Xamarin:
  - Xamarin.iOS: Version 10.14 oder höher
  - Xamarin.Android: Version 8.0 oder höher
  - Xamarin.Mac: Version 3.8 oder höher
