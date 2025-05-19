---
title: "Licencjonowanie"
second_title: Aspose.GIS for .NET
type: docs
url: /pl/net/licensing/
weight: 50
keywords: c# gis library, .net gis library
description: Oceń bibliotekę C# .NET GIS lub API z pewnymi ograniczeniami. Zastosuj licencję za pomocą obiektu Pliku lub Strumienia lub jako Zasobu Osadzonego.
---

## **Oceń Aspose.GIS for .NET**
Możesz pobrać Aspose.GIS for .NET bezpłatnie. Przed zastosowaniem licencji komponent działa w trybie ewaluacyjnym. Po zakupie licencji i dodaniu kilku linii kodu, aby ją zastosować, usuwane są ograniczenia wersji próbnej.

{{% alert color="primary" %}} Jeśli chcesz przetestować Aspose.GIS bez ograniczeń trybu ewaluacyjnego, możesz poprosić o 30-dniową licencję tymczasową. Zapoznaj się z [Uzyskaj licencję tymczasową](https://purchase.aspose.com/temporary-license). {{% /alert %}}
### **Ograniczenia Trybu Ewalucyjnego**
Uruchamiając w trybie ewaluacyjnym (bez zastosowanej licencji), Aspose.GIS zapewnia pełną funkcjonalność produktu z wyjątkiem pewnych ograniczeń wersji próbnej.

1. Nie więcej niż **15 dokumentów** może być otwartych i/lub tworzonych **na godzinę**.
1. Nie więcej niż **100 cech** może być dostępnych w każdym dokumencie (odczyt lub zapis).
1. Nie więcej niż **10 000 danych rastrowych** może być dostępnych w każdym dokumencie (odczyt lub zapis).
1. Maksymalna dopuszczalna liczba cech w dokumencie dla operacji konwersji wynosi **50**.

Uruchamiając w trybie licencjonowanym, możesz przetwarzać nieograniczoną liczbę dokumentów i cech.
## **Zastosowanie Licencji**
Licencja to zwykły plik XML zawierający szczegóły takie jak nazwa produktu, liczba programistów, na których jest wydana, data wygaśnięcia subskrypcji i tak dalej. Plik jest cyfrowo podpisany, więc nie modyfikuj go. Nawet przypadkowe dodanie dodatkowego znaku nowej linii do pliku spowoduje jego unieważnienie.

Musisz ustawić licencję przed użyciem Aspose.GIS, jeśli chcesz uniknąć ograniczeń wersji próbnej. Ustawienie licencji jest wymagane tylko raz dla aplikacji (lub procesu).
### **Ustawianie Licencji w Aspose.GIS for .NET**
W Aspose.GIS licencja może być ładowana z pliku, strumienia lub zasobu osadzonego. Aspose.GIS próbuje znaleźć licencję w następujących lokalizacjach:

- Ścieżka jawna
- Folder zawierający Aspose.GIS.dll
- Folder zawierający zestaw, który wywołał Aspose.GIS.dll
- Folder zawierający zestaw startowy (twój .exe)
- Zasób osadzony w zestawie, który wywołał Aspose.GIS.dll. Istnieją dwie powszechne metody ustawiania licencji, które zostaną omówione poniżej:
### **Zastosuj Licencję za Pomocą Obiektu Pliku lub Strumienia**
Najłatwiejszym sposobem ustawienia licencji jest umieszczenie pliku licencyjnego w tym samym folderze co Aspose.GIS.dll i podanie tylko nazwy pliku bez jego ścieżki.

{{< highlight java >}}

 // Utwórz instancję klasy licencji i ustaw plik licencyjny za pomocą jego ścieżki

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // Utwórz instancję klasy licencji i ustaw licencję za pomocą strumienia

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}

Kiedy wywołujesz metodę SetLicense, nazwa licencji powinna być taka sama jak nazwa pliku licencyjnego. Na przykład możesz zmienić nazwę pliku licencyjnego na „Aspose.GIS.lic.xml”. Następnie w kodzie należy użyć zmodyfikowanej nazwy licencji (tj. Aspose.GIS.lic.xml) dla metody SetLicense.

## **Dołączenie Pliku Licencyjnego jako Zasobu Osadzonego**
Innym dobrym sposobem na zapakowanie licencji wraz z aplikacją i upewnienie się, że jej nie zgubisz, jest dołączenie jej jako zasobu osadzonego do jednego z zestawów wywołujących bibliotekę komponentu (zawartą w Aspose.GIS). Aby uwzględnić plik licencyjny jako zasób osadzony, wykonaj następujące kroki:

- W Visual Studio dodaj plik licencji (.lic) do projektu za pomocą menu Plik | Dodaj istniejący element...
- Zaznacz plik w Eksploratorze rozwiązań i ustaw Akcję kompilacji na Zasób osadzony w oknie Właściwości.
- Aby uzyskać dostęp do licencji osadzonej w zestawie (jako zasobu osadzonego), nie trzeba wywoływać metod GetExecutingAssembly i GetManifestResourceStream klasy System.Reflection.Assembly .NET Framework. Wszystko, co musisz zrobić, to dodać plik licencyjny jako zasób osadzony do projektu i przekazać nazwę pliku licencji do metody License.SetLicense. Klasa Licencji automatycznie znajdzie plik licencji w zasobach osadzonych.

Zapoznaj się z przykładem poniżej, aby zrozumieć tę metodę ustawiania licencji (osadzonej) w aplikacjach.

{{< highlight java >}}

 // Utwórz klasę Licencji

Aspose.Gis.License license = new Aspose.Gis.License();

// Przekaż tylko nazwę pliku licencyjnego osadzonego w zestawie

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **Zastosowanie Klucza Mierzonego**
[API Aspose.GIS for .NET](/gis/net/) umożliwia programistom stosowanie klucza mierzonego. Jest to nowy mechanizm licencjonowania. Nowy mechanizm licencjonowania będzie używany wraz z istniejącą metodą licencjonowania. Klienci, którzy chcą być rozliczani na podstawie wykorzystania funkcji API, mogą korzystać z licencjonowania mierzonego. Więcej informacji można znaleźć w sekcji [FAQ dotyczące licencjonowania mierzonego](https://purchase.aspose.com/faqs/licensing/metered).

Wprowadzono nową klasę **Metered**, aby zastosować klucz mierzony. Poniżej znajduje się przykładowy kod demonstrujący, jak ustawić publiczny i prywatny klucz mierzonego.

**[C#]**

{{< highlight csharp >}}

 // ustaw mierzone klucze publiczne i prywatne
 
Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();
 
// Uzyskaj dostęp do właściwości setMeteredKey i przekaż klucze publiczne i prywatne jako parametry
 
metered.SetMeteredKey("*****", "*****");
 
// WYKONAJ PRZETWARZANIE
 
// pobierz ilość zużytych danych
 
decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();
 
// Wyświetl informacje
 
Console.WriteLine("Zużyta kwota: " + amount.ToString());

{{< /highlight >}}
