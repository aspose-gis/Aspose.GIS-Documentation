---
title: "Instalacja"
second_title: Aspose.GIS for .NET
type: docs
url: /pl/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: Zainstaluj bibliotekę lub API GIS C#.NET z NuGet za pomocą interfejsu użytkownika Package Manager lub Konsoli, z Archiwum ZIP. Może być również używana w .NET Core i systemie operacyjnym Linux.
---

## **Zainstaluj Aspose.GIS**
### **Z NuGet**
Aby zainstalować Aspose.GIS, możesz użyć interfejsu użytkownika Package Manager lub Konsoli Package Manager. Podczas instalacji pakietu, NuGet zapisuje zależność w pliku projektu lub pliku packages.config.
#### **Interfejs użytkownika Package Manager**
1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy **References** i wybierz **Manage NuGet Packages**.

![todo:image_alt_text](installation_1.png)

1. Upewnij się, że "nuget.org" jest wybrane jako **Źródło pakietu**, wybierz zakładkę Przeglądaj, wyszukaj Aspose.GIS, wybierz ten pakiet z listy i kliknij Zainstaluj:

![todo:image_alt_text](installation_2.png)

1. Zapoznaj się z [Umową licencyjną użytkownika końcowego Aspose](https://about.aspose.com/legal/eula).
1. Jeśli zostaniesz poproszony o sprawdzenie zmian, wybierz **OK**.
#### **Konsola Package Manager**
1. Wybierz polecenie menu **Narzędzia** > **NuGet Package Manager** > **Package Manager Console**.
1. Po otwarciu konsoli upewnij się, że lista rozwijana **Domyślny projekt** pokazuje projekt, do którego chcesz zainstalować pakiet. Jeśli w rozwiązaniu znajduje się tylko jeden projekt, jest on już wybrany.

![todo:image_alt_text](installation_3.png)

1. Wprowadź polecenie Install-Package Aspose.GIS. Okno konsoli wyświetli dane wyjściowe dla tego polecenia.
### **Za pomocą Instalatora MSI lub z Archiwum ZIP**
Jako alternatywa dla instalacji NuGet, możesz pobrać Aspose.GIS z [sekcji Pobieranie](https://downloads.aspose.com/gis/net) spakowanego jako instalator MSI lub archiwum ZIP.
## **Instrukcje specyficzne dla platformy**
### **Linux**
Korzystając z funkcjonalności renderowania map Aspose.GIS w systemie Linux, upewnij się, że biblioteka System.Drawing.Common jest poprawnie skonfigurowana. Jeśli otrzymasz komunikat o błędzie podobny do 

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

oznacza to, że zależności System.Drawing.Common są brakujące w systemie. Aby to naprawić, uruchom:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev
## **Wymagania systemowe dla Aspose.GIS for .NET**
Wszystkie komponenty Aspose .NET wymagają zestawu uprawnień Full Trust.

Aspose.GIS zawiera dwie warianty zestawienia zbudowanego dla

- .NET Framework 4.7,
- .NET Standard 2.0.



### **.NET Framework v4.7 lub nowszy**
Systemy operacyjne: 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `Obsługiwane są wersje 32-bitowe i 64-bitowe.
### **.NET Core v2.0 lub nowszy**
` `Systemy operacyjne:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (wersja 1607) lub późniejsze wersje
- Microsoft Windows Server 2008 R2 SP1 (Full Server lub Server Core), 2012 SP1 (Full Server lub Server Core), 2012 R2 (Full Server lub Server Core), 2016 lub nowsze wersje (Full Server, Server Core lub Nano Server)
- macOS 10.12 "Sierra" i późniejsze wersje
- Linux (64-bitowy, x86_64 lub amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64-bitowy, arm32), 8.7 lub późniejsze wersje
  - Ubuntu 18.04 (64-bitowy, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 lub późniejsze wersje
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 lub późniejsze wersje
  - Alpine Linux 3.7 lub późniejsze wersje

Więcej szczegółów dostępnych w przewodniku .NET Core: [Wymagania wstępne systemu Windows](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [Wymagania wstępne macOS](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Wymagania wstępne systemu Linux](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **Obsługa eksperymentalna**
- Mono 5.4 lub nowszy
- Xamarin:
  - Xamarin.iOS: wersja 10.14 lub późniejsza
  - Xamarin.Android: wersja 8.0 lub późniejsza
  - Xamarin.Mac: wersja 3.8 lub późniejsza
