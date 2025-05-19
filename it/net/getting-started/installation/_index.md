---
title: "Installazione"
second_title: Aspose.GIS for .NET
type: docs
url: /it/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: Installa la libreria o API GIS C#.NET da NuGet utilizzando l'interfaccia utente Package Manager o Console, da ZIP Archive. Può anche essere utilizzato in .NET Core e sistemi operativi Linux.
---

## **Installa Aspose.GIS**
### **Da NuGet**
Per installare Aspose.GIS, puoi utilizzare sia l'interfaccia utente di Package Manager che la Package Manager Console. Quando si installa un pacchetto, NuGet registra la dipendenza nel file del progetto o in un file packages.config.
#### **Package Manager UI**
1. In Solution Explorer, fai clic con il pulsante destro del mouse su **References** e scegli **Manage NuGet Packages**.

![todo:image_alt_text](installation_1.png)

1. Verifica che "nuget.org" sia selezionato come **Package Source**, seleziona la scheda Browse, cerca Aspose.GIS, seleziona il pacchetto nell'elenco e fai clic su Install:

![todo:image_alt_text](installation_2.png)

1. Familiarizza con [Aspose End User License Agreement](https://about.aspose.com/legal/eula).
1. Se richiesto di rivedere le modifiche, seleziona **OK**.
#### **Package Manager Console**
1. Seleziona il comando del menu **Tools** > **NuGet Package Manager** > **Package Manager Console**.
1. Dopo l'apertura della console, assicurati che l'elenco a discesa **Default project** mostri il progetto in cui desideri installare il pacchetto. Se hai un solo progetto nella soluzione, è già selezionato.

![todo:image_alt_text](installation_3.png)

1. Inserisci il comando Install-Package Aspose.GIS. La finestra della console mostrerà l'output del comando.
### **Con MSI Installer o Da ZIP Archive**
Come alternativa all'installazione di NuGet, puoi scaricare Aspose.GIS da [Downloads section](https://downloads.aspose.com/gis/net) confezionato come installatore MSI o archivio ZIP.
## **Istruzioni specifiche della piattaforma**
### **Linux**
Quando si utilizza la funzionalità di rendering delle mappe di Aspose.GIS sotto Linux, assicurati che la libreria System.Drawing.Common sia configurata correttamente. Se ricevi un messaggio di errore simile a 

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

significa che le dipendenze di System.Drawing.Common mancano dal sistema. Per risolvere questo problema, esegui:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev
## **Requisiti di sistema per Aspose.GIS for .NET**
Tutti i componenti Aspose .NET richiedono il set di autorizzazioni Full Trust.

Aspose.GIS include due varianti dell'assembly compilato per

- .NET Framework 4.7,
- .NET Standard 2.0.

### **.NET Framework v4.7 o successivo**
Sistemi operativi: 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `Sono supportate sia le versioni a 32 che a 64 bit.
### **.NET Core v2.0 o successivo**
` `Sistemi operativi:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (versione 1607) o versioni successive
- Microsoft Windows Server 2008 R2 SP1 (Full Server or Server Core), 2012 SP1 (Full Server or Server Core), 2012 R2 (Full Server or Server Core), 2016 o versioni successive (Full Server, Server Core, or Nano Server)
- macOS 10.12 "Sierra" e versioni successive
- Linux (64 bit, x86_64 o amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64 bit, arm32), 8.7 o versioni successive
  - Ubuntu 18.04 (64 bit, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 o versioni successive
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 o versioni successive
  - Alpine Linux 3.7 o versioni successive

Maggiori dettagli disponibili nella guida .NET Core: [Windows Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [macOS Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Linux Prerequisites](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **Supporto sperimentale**
- Mono 5.4 o successivo
- Xamarin:
  - Xamarin.iOS: versione 10.14  o successiva
  - Xamarin.Android: versione 8.0 o successiva
  - Xamarin.Mac: versione 3.8 o successiva
