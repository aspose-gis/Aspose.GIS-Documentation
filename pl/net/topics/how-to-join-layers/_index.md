---
title: "Jak łączyć warstwy za pomocą geometrii lub atrybutów"
type: docs
url: /pl/net/how-to-join-layers
weight: 70
---

## Podsumowanie

W GIS, łączenia są potężnym mechanizmem do łączenia informacji z różnych warstw na podstawie wspólnego atrybutu lub relacji przestrzennej. Łączenia pozwalają połączyć dane atrybutów z jednej warstwy (warstwy źródłowej) z inną warstwą (warstwą docelową), używając wspólnego pola lub lokalizacji przestrzennej. Pierwszy to łączenie danych przez klucz (atrybut w tabeli). Używając wspólnego pola, takiego jak unikalny klucz, można powiązać rekordy w jednej tabeli z rekordami w innej tabeli. Drugie podejście to łączenie danych przez lokalizację (przestrzennie). Obsługujemy oba podejścia i oferujemy możliwość ich wykorzystania w zależności od Twoich potrzeb.

Załóżmy, że otrzymałeś dane opisujące procentową zmianę populacji dla różnych okręgów i chcesz wygenerować kilka map wzrostu populacji na podstawie tych informacji. Podczas gdy Twoje dane dotyczące populacji są przechowywane w tabeli w Twojej bazie danych i dzielą wspólne pole z Twoją warstwą, możesz połączyć te dane ze swoimi obiektami geograficznymi i wykorzystać dodatkowe pola do etykietowania, kategoryzacji, wykonywania zapytań lub analizy obiektów warstwy.

Zazwyczaj wykonujesz łączenia danych na podstawie wartości pola, która istnieje w obu tabelach. Nazwy pól nie muszą być identyczne, ale typy danych powinny być takie same - liczby z liczbami, ciągi znaków z ciągami znaków i tak dalej. Możesz wykonać łączenie danych za pomocą narzędzia geoprocesingu "Add Join" (Dodaj połączenie). Podczas łączenia atrybutów dołączane pola są dynamicznie dodawane do istniejącej tabeli. Właściwości pól, takie jak aliasy, widoczność i formatowanie liczb, są zachowywane podczas dodawania lub usuwania połączenia.

## Możliwości łączenia przez kluczowe pole

- To podejście pozwala na **powiązanie rekordów z różnych tabel** na podstawie wspólnego pola klucza. Możesz określić pole klucza, które ma być użyte do porównania w celu ustalenia relacji między rekordami. Jest to szczególnie przydatne, gdy musisz połączyć dane na podstawie identyfikatora lub innego unikalnego atrybutu.

Określanie metody porównywania danych na podstawie pola klucza:

- Możesz zdefiniować **różne metody porównania** dla pola klucza podczas łączenia danych. Na przykład możesz wybrać dopasowanie dokładne, porównanie oparte na wzorcu lub w zakresie wartości. Pozwala to na bardziej precyzyjne określenie relacji między rekordami i daje kontrolę nad procesem łączenia danych.

Określanie listy nazw atrybutów do połączenia:

- Podczas łączenia danych możesz określić **konkretne atrybuty**, które mają zostać połączone. Pozwala to wybrać tylko niezbędne atrybuty do połączenia i zarządzać strukturą wynikowej tabeli.

## Możliwości łączenia za pomocą geometrii

- To podejście umożliwia powiązanie danych na podstawie ich **lokalizacji przestrzennej**. Możesz zdefiniować promień wyszukiwania, w którym będą szukane najbliższe obiekty geometryczne do połączenia. Jest to przydatne, gdy musisz połączyć dane na podstawie ich położenia geograficznego.

Kontrolowanie promienia wyszukiwania w celu znalezienia najbliższych obiektów geometrycznych:

- Możesz kontrolować **promień wyszukiwania** podczas łączenia danych na podstawie lokalizacji. Określając wartość promienia, określasz odległość, w której będą szukane najbliższe obiekty do połączenia. Daje to kontrolę nad tym, które obiekty wezmą udział w procesie łączenia danych na podstawie ich relacji przestrzennej.

## Projekt demonstracyjny

Aby lepiej zrozumieć funkcjonalność naszej biblioteki, rozważmy [przykład jej użycia](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Layers.Join). Ten kod ilustruje sposób łączenia warstw wektorowych za pomocą atrybutów lub geometrii.

Dostarczony kod składa się z dwóch metod, JoinByIndex() i JoinByCoords(), które demonstrują operacje łączenia danych przy użyciu klasy LayerConstructor.

W metodzie JoinByIndex():

- Tworzone są listy geometrii z powiązanymi atrybutami.

- Inicjalizowany jest obiekt LayerConstructor.

- Metoda tworzy warstwę wektorową i warstwę geometrii, korzystając z dostarczonych geometrii.

- Warstwa geometrii jest łączona na podstawie unikalnego identyfikatora ("Id") za pomocą metody JoinLayersById().

- Wynikowa połączona warstwa wektorowa jest zwracana.

W metodzie JoinByCoords():

- Tworzone są listy geometrii z powiązanymi atrybutami.

- Inicjalizowany jest obiekt LayerConstructor.

- Warstwy geometrii są tworzone przy użyciu dostarczonych geometrii.

- Warstwy geometrii są łączone na podstawie dopasowywania współrzędnych za pomocą metody JoinLayersByCoords().

- Wynikowa połączona warstwa wektorowa jest zwracana.

Podsumowując, te metody demonstrują dwa różne podejścia do łączenia danych: jedno oparte na unikalnym identyfikatorze, a drugie oparte na dopasowywaniu współrzędnych. Klasa LayerConstructor ułatwia te operacje łączenia danych.

## Opcje łączenia dla indeksu

Klasa JoinOptions zapewnia zestaw opcji konfigurowania łączenia warstw. Przyjrzyjmy się bliżej każdej opcji:

- **JoinAttributeName**: Ta opcja pozwala określić nazwę atrybutu z łączonej warstwy, której wartość będzie używana w porównaniu warunkowym. Ustanawia ona połączenie między dwiema warstwami na podstawie tego atrybutu.

- **TargetAttributeName**: Dzięki tej opcji możesz określić nazwę atrybutu z głównej warstwy, która zostanie porównana z atrybutem z łączonej warstwy. Pomaga to w określeniu dopasowujących się cech między warstwami.

- **JoinAttributeNames**: Ta opcja umożliwia określenie listy nazw atrybutów, które chcesz połączyć. Jeśli ta lista zostanie pusta lub ustawiona na null, wszystkie atrybuty z łączonej warstwy zostaną uwzględnione w operacji łączenia. Wybierając jednak określone nazwy atrybutów, możesz kontrolować atrybuty, które są łączone, co może być przydatne do optymalizacji zużycia pamięci i czasu przetwarzania.

- **ConditionComparer**: Ta opcja pozwala zdefiniować niestandardową logikę porównywania wartości atrybutów między cechami dwóch warstw. Domyślnie używa komparatora EqualityComparer.Default, który sprawdza równość. Możesz jednak dostarczyć własny niestandardowy komparator, który implementuje IEqualityComparer w celu uzyskania bardziej wyspecjalizowanych wymagań dotyczących porównywania.

- **JoinedAttributesPrefix**: Ta opcja pozwala określić prefiks ciągu znaków dla nazw atrybutów łączonej warstwy. Domyślna wartość to "joined_", co oznacza, że dołączone atrybuty zostaną poprzedzone prefiksem "joined_" w wynikowej połączonej warstwie. Ten prefiks pomaga odróżnić dołączone atrybuty od oryginalnych atrybutów głównej warstwy.

Klasa JoinOptions zapewnia elastyczność i kontrolę nad różnymi aspektami procesu łączenia warstw. Możesz określić atrybuty do połączenia, dostosować logikę porównywania i zdefiniować prefiks dla wynikowych połączonych atrybutów. Te opcje umożliwiają dopasowanie operacji łączenia do konkretnych potrzeb i uzyskanie znaczących spostrzeżeń z połączonych warstw.

## Opcje łączenia dla geometrii

Klasa **JoinByGeometryOptions** reprezentuje opcje łączenia warstw na podstawie geometrii. Przyjrzyjmy się funkcjonalności każdej opcji:

- **Radius**: Ta opcja określa promień, w obrębie którego będą wyszukiwane dołączone geometrie. Określa ona bliskość, w której cechy z głównej warstwy zostaną dopasowane do cech z łączonej warstwy na podstawie ich relacji przestrzennej.

- **ConditionComparer**: Ta opcja pozwala zdefiniować niestandardową logikę porównywania wartości atrybutów z cech dwóch warstw. Domyślnie używa EqualityComparer.Default, który sprawdza równość. Możesz jednak dostarczyć własny niestandardowy komparator, który implementuje IEqualityComparer w celu uzyskania bardziej specyficznych wymagań dotyczących porównywania.

- **JoinedAttributesPrefix**: Ta opcja umożliwia określenie prefiksu ciągu znaków dla nazw atrybutów łączonej warstwy. Domyślna wartość to "joined_", co oznacza, że dołączone atrybuty zostaną poprzedzone prefiksem "joined_" w wynikowej połączonej warstwie. Ten prefiks pomaga odróżnić dołączone atrybuty od oryginalnych atrybutów głównej warstwy.

Klasa JoinByGeometryOptions zapewnia możliwość dostosowania procesu łączenia warstw na podstawie ich relacji przestrzennej. Określając promień wyszukiwania, możesz kontrolować zakres, w którym geometrie zostaną dopasowane. Pozwala to na precyzyjne dostrojenie operacji łączenia na podstawie pożądanej bliskości między cechami. Możliwość podania niestandardowego komparatora daje elastyczność w porównywaniu wartości atrybutów, a możliwość prefiksowania dołączonych atrybutów pomaga je odróżnić w wynikowej połączonej warstwie.

Korzystając z tych opcji, możesz wykonywać świadome przestrzenne łączenie danych i uzyskiwać spostrzeżenia z połączonych warstw, które są oparte na ich bliskości przestrzennej i wartościach atrybutów.

## Podsumowanie

Mechanizm łączenia danych w GIS umożliwia łączenie obiektów geometrycznych z odpowiednimi atrybutami z różnych warstw. Zapewnia to możliwość analizowania i wyodrębniania informacji na podstawie relacji przestrzennych i atrybutowych w danych. Dostępne opcje umożliwiają dostosowanie procesu łączenia do konkretnych wymagań i potrzeb analitycznych w danych GIS.

Łączenie danych ułatwia różne zadania, w tym:

- Znajdowanie obiektów spełniających określone kryteria przestrzenne, takie jak identyfikacja wszystkich budynków w promieniu 500 metrów od określonego punktu.

- Łączenie danych geograficznych w celu stworzenia bardziej kompleksowego i informatywnego przeglądu sytuacji.

- Analizowanie wartości atrybutów obiektów na podstawie określonych warunków przestrzennych w celu identyfikacji trendów i wzorców.

Opcje łączenia danych umożliwiają precyzyjną konfigurację procesu dopasowywania obiektów. Te opcje obejmują wybór atrybutów do połączenia, zdefiniowanie niestandardowej logiki porównywania wartości atrybutów oraz dodanie prefiksu do nazw atrybutów połączonych danych. Te opcje zapewniają elastyczność i zdolność adaptacji do procesu łączenia, dostosowując się do konkretnych wymagań i celów analizy danych w GIS.

Mechanizm łączenia danych odgrywa znaczącą rolę w integrowaniu i analizowaniu danych geograficznych, prowadząc do bardziej kompleksowego zrozumienia przestrzennej i atrybutowej natury badanych obiektów.