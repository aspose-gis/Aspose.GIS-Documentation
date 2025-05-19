---
title: "Installation"
second_title: Aspose.GIS for .NET
type: docs
url: /fr/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: Installez la bibliothèque ou l'API GIS C#.NET à partir de NuGet en utilisant l'interface utilisateur Package Manager ou Console, à partir d'une archive ZIP. Elle peut également être utilisée dans .NET Core et le système d'exploitation Linux.
---

## **Installer Aspose.GIS**
### **À partir de NuGet**
Pour installer Aspose.GIS, vous utilisez soit l'interface utilisateur Package Manager, soit la console Package Manager. Lorsque vous installez un package, NuGet enregistre la dépendance dans votre fichier de projet ou un fichier packages.config.
#### **Interface utilisateur Package Manager**
1. Dans l'Explorateur de solutions, faites un clic droit sur **Références** et choisissez **Gérer les paquets NuGet**.

![todo:image_alt_text](installation_1.png)

1. Vérifiez que "nuget.org" est sélectionné comme **Source du package**, sélectionnez l'onglet Parcourir, recherchez Aspose.GIS, sélectionnez ce paquet dans la liste et cliquez sur Installer :

![todo:image_alt_text](installation_2.png)

1. Familiarisez-vous avec [le contrat de licence utilisateur final d'Aspose](https://about.aspose.com/legal/eula).
1. Si vous y êtes invité pour examiner les modifications, sélectionnez **OK**.
#### **Console Package Manager**
1. Sélectionnez la commande de menu **Outils** > **Gestionnaire de paquets NuGet** > **Console du gestionnaire de paquets**.
1. Après l'ouverture de la console, assurez-vous que la liste déroulante **Projet par défaut** affiche le projet dans lequel vous souhaitez installer le paquet. Si vous avez un seul projet dans la solution, il est déjà sélectionné.

![todo:image_alt_text](installation_3.png)

1. Entrez la commande Install-Package Aspose.GIS. La fenêtre de la console affichera les résultats de la commande.
### **Avec MSI Installer ou à partir d'une archive ZIP**
Comme alternative à l'installation NuGet, vous pouvez télécharger Aspose.GIS depuis la [section Téléchargements](https://downloads.aspose.com/gis/net) sous forme d'installateur MSI ou d'archive ZIP.
## **Instructions spécifiques à la plateforme**
### **Linux**
Lorsque vous utilisez la fonctionnalité de rendu cartographique d'Aspose.GIS sous Linux, assurez-vous que la bibliothèque System.Drawing.Common est configurée correctement. Si vous recevez un message d'erreur similaire à 

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

cela signifie que les dépendances de System.Drawing.Common manquent dans le système. Pour résoudre ce problème, exécutez :

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev
## **Configuration requise pour Aspose.GIS for .NET**
Tous les composants Aspose .NET nécessitent un jeu d'autorisations Full Trust.

Aspose.GIS comprend deux variantes de l'assembly construit pour

- .NET Framework 4.7,
- .NET Standard 2.0.



### **.NET Framework v4.7 ou ultérieur**
Systèmes d'exploitation : 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `Les versions 32 et 64 bits sont toutes deux prises en charge.
### **.NET Core v2.0 ou ultérieur**
` `Systèmes d'exploitation :

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (version 1607) ou versions ultérieures
- Microsoft Windows Server 2008 R2 SP1 (Full Server ou Server Core), 2012 SP1 (Full Server ou Server Core), 2012 R2 (Full Server ou Server Core), 2016 ou versions ultérieures (Full Server, Server Core ou Nano Server)
- macOS 10.12 "Sierra" et versions ultérieures
- Linux (64 bits, x86_64 ou amd64) :
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64 bits, arm32), 8.7 ou versions ultérieures
  - Ubuntu 18.04 (64 bits, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 ou versions ultérieures
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 ou version ultérieure
  - Alpine Linux 3.7 ou version ultérieure

Plus de détails sont disponibles dans le guide .NET Core : [Prérequis Windows](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [Prérequis macOS](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Prérequis Linux](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **Support expérimental**
- Mono 5.4 ou ultérieur
- Xamarin :
  - Xamarin.iOS : version 10.14 ou ultérieure
  - Xamarin.Android : version 8.0 ou ultérieure
  - Xamarin.Mac : version 3.8 ou ultérieure
