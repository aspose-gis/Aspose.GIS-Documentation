---
title: "Optymalny Wyszukiwarka Ścieżek"
type: docs
url: /pl/net/optimal-path-finder
weight: 70
---

## Podsumowanie

Wyszukiwanie najkrótszej ścieżki w sieci dróg to proces analizy mający na celu określenie najbardziej efektywnego sposobu podróżowania między punktami na mapie. To narzędzie może być przydatne do tworzenia optymalnych tras z wieloma przystankami lub mierzenia odległości i czasu podróży między różnymi lokalizacjami. Przy każdym wywołaniu nasza technologia może znaleźć optymalne trasy dla jednego lub wielu pojazdów. Na przykład, może pomóc kierowcom w znalezieniu optymalnych tras do dostarczania towarów lub określić optymalną odległość dojazdu z domu do pracy dla różnych pasażerów.

## Możliwości Algorytmu

Nasza biblioteka zapewnia możliwość zbudowania najbardziej **optymalnej trasy między dwoma punktami** na mapie. Posiada następujące główne funkcje:

1. Wyszukiwanie optymalnej ścieżki na mapie, uwzględniające szlaki i przeszkody: Bierzemy pod uwagę nie tylko drogi, ale także ścieżki poza drogowe, takie jak szlaki turystyczne, chodniki dla pieszych oraz przeszkody, które mogą wpłynąć na wybór optymalnej ścieżki.

2. Wyszukiwanie optymalnej ścieżki wyłącznie po drogach: Jeśli musisz znaleźć trasę wyłącznie po drogach, zapewniamy tę możliwość. Jest to przydatne na przykład dla pojazdów ograniczone do poruszania się tylko po drogach.

3. Ustawianie różnych prędkości dla dróg: Mamy możliwość przypisywania różnych prędkości różnym drogom. Na przykład, wyższe prędkości można ustawić dla głównych autostrad, a niższe dla wąskich jezdni.

4. Ustawianie prostokątnych przeszkód: Możesz zdefiniować prostokątne przeszkody na mapie, które należy uwzględnić podczas budowania optymalnej ścieżki. Jest to przydatne, gdy występują znane przeszkody, takie jak budynki lub jeziora (ich przybliżenie).

5. Ograniczenie promienia wyszukiwania dla dróg: Możesz ograniczyć promień wyszukiwania dla dróg, aby skrócić czas wyszukiwania i skupić się tylko na określonym obszarze.

6. Kontrola wydajności i dokładności: Zapewniamy możliwość kontrolowania wydajności i dokładności algorytmu. Możesz go dostosować, aby osiągnąć pożądane równowagę między szybkością wyszukiwania a dokładnością budowania trasy.

Następnie przedstawimy bardziej szczegółowy opis każdej z tych funkcji i przeanalizujemy przykłady ich zastosowań.

## Podejście do Rozwiązania

Chociaż znajdowanie ścieżki to nietrywialne zadanie, istnieje kilka dobrych i niezawodnych algorytmów, które są rozpoznawane w społeczności programistycznej.

W naszej implementacji użyliśmy zmodyfikowanego algorytmu Lee. Mamy siatkę komórek na płaszczyźnie. Z punktu początkowego rozchodzi się fala w 8 kierunkach (włącznie z przekątnymi) do sąsiednich komórek, obliczając czas potrzebny do dotarcia do każdej z nich. Sąsiednia komórka może zawierać przeszkodę lub drogę. Drogi mogą mieć różne współczynniki prędkości. Zatem „oznaczamy” naszą siatkę czasem potrzebnym na dotarcie do każdej komórki z komórki początkowej w określonym promieniu lub do osiągnięcia punktu docelowego. Jeśli dotrzemy do punktu docelowego, budujemy odwrotną ścieżkę przy użyciu naszej siatki.

Aby określić optymalną trasę w sieci dróg, należy podjąć kilka kroków. Najpierw musisz zdefiniować drogi i określić prędkość ruchu na każdej z nich. Należy również uwzględnić obecność sztucznych i naturalnych przeszkód, które mogą wpłynąć na przebieg ścieżki. Po tym należy określić punkty początkowe i docelowe wyszukiwania. Gdy te wstępne kroki zostaną wykonane, można przejść do właściwego znajdowania ścieżki. Wynikiem będzie ścieżka reprezentowana na przykład jako lista współrzędnych punktów.

Warto zauważyć, że optymalna ścieżka może zależeć od wybranego środka transportu, ponieważ prędkość ruchu i zestaw przeszkód mogą się różnić. Dlatego podczas wyszukiwania optymalnej ścieżki należy używać różnych zestawów dróg i przeszkód dla każdego rodzaju transportu.

## Projekt Demonstracyjny na GitHubie

Aby lepiej zrozumieć funkcjonalność naszej biblioteki, rozważmy [przykład jej użycia](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths). Ten kod ilustruje, jak skonfigurować drogi i przeszkody w algorytmie znajdowania ścieżki oraz znaleźć optymalną trasę.

Przykład składa się z następujących kroków:

1. Tworzenie listy informacji o drogach (RoadInfo), która zawiera informacje o segmencie drogi (Segment) i prędkości ruchu (Velocity).
2. Dodawanie szybkich dróg do listy.
3. Dodawanie wolnych dróg okrężnych do listy.
4. Tworzenie generatora warstw dróg (WayLayerGenerator) i dodawanie dróg do generatora.
5. Wyszukiwanie wielu ścieżek z punktu początkowego (startPoint) do punktów docelowych (goalPoint01, goalPoint02, goalPoint03) przy użyciu określonego promienia (radius).
6. Przygotowanie warstwy dróg (roadsLayer) do wyświetlenia na mapie i dodanie obiektów drogowych.
7. Przygotowanie warstwy drogi (wayLayer) do wyświetlenia na mapie i tworzenie obiektów geometrycznych dla każdej znalezionej ścieżki.
8. [Wyświetlanie mapy](https://docs.aspose.com/gis/net/how-to-draw-geometry/) za pomocą funkcji ShowMap, zapisanie mapy w określonej ścieżce.

Ten kod buduje i wyświetla ścieżki drogowe na mapie dla określonych punktów przy użyciu informacji o drogach i generatora warstw drogi.

## Opcje Wyszukiwania

Znajdowanie ścieżki odbywa się za pomocą klasy **WayLayerGenerator** znajdującej się w przestrzeni nazw Aspose.Gis.GeoTools.WayAnalyzer.

Klasa WayLayerGenerator ma metodę **FindTheWay** do znajdowania ścieżki z punktu początkowego do celu. Aby utworzyć instancję klasy WayLayerGenerator, przekazujemy parametry WayOptions (wszystkie parametry są opcjonalne):

- StartPoint: Punkt początkowy

- GoalPoint: Punkt docelowy

- Radius: Promień wyszukiwania

- Scale: Skala siatki

- IsMoveOnlyRoad: Czy szukać ścieżki tylko po drogach

Zauważalną cechą jest parametr Scale. Jeśli zostanie określony w konstruktorze, ustalamy stałą skalę dla kolejnych wyszukiwań. Jeśli parametr Scale nie jest ustawiony, ale StartPoint i GoalPoint są ustawione, obliczamy skalę jako odległość między punktem początkowym a docelowym podzieloną przez 100. We wszystkich innych przypadkach domyślna wartość Scale wynosi 1. Dla doświadczonych użytkowników lepiej ustawić Scale lub bezpośrednio ustawić StartPoint i GoalPoint, aby najbardziej efektywnie reprezentować drogi i przeszkody na siatce (szczególnie jeśli jest ich wiele).

Aby użyć metody FindTheWay, musimy określić punkty początkowe i docelowe. Możemy również ustawić promień wyszukiwania (odległość, do której rozchodzi się fala). Domyślnie promień obliczany jest jako odległość między punktem początkowym a docelowym pomnożona przez 3. Punkty początkowe i docelowe mogą być blisko lub bardzo daleko od siebie, więc na podstawie odległości między nimi obliczamy skalę naszej siatki. Jeśli bieżąca skala nie pasuje do poprzedniej, ponownie obliczamy siatkę. Skalę można ustalić za pomocą parametru Scale. W tym przypadku nie jest ona obliczana i siatka nie jest przeliczana.

Przed rozpoczęciem wyszukiwania musimy zdefiniować mapę dróg i przeszkód przy użyciu odpowiednich metod AddRoad i AddBlock klasy WayLayerGenerator.

Dla metody **AddRoad** musimy określić:

- startPoint: Punkt początkowy drogi

- endPoint: Punkt końcowy drogi

- velocity: Prędkość ruchu na drodze

Dla metody **AddBlock** musimy określić:

- x: Współrzędna x lewego górnego rogu bloku

- y: Współrzędna y lewego górnego rogu bloku

- sizeX: Rozmiar w osi x

- sizeY: Rozmiar w osi y

Te metody pozwalają nam zdefiniować mapę dróg i przeszkód przed rozpoczęciem procesu znajdowania ścieżki.

## Przykłady Kodu

Oto kilka przykładów kodu, które ilustrują, jak skonfigurować drogi i przeszkody w algorytmie znajdowania ścieżki oraz znaleźć optymalną trasę.

Przykład 1: Znajdowanie ścieżki między punktami początkowymi i docelowymi.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Przykład 2**: Ustawianie parametru Scale i posiadanie ujemnych współrzędnych dla punktu.

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Przykład 3**: Ustawianie parametru IsMoveOnlyRoad i promienia wyszukiwania.

```
WayOptions mapGeneratorOptions = new WayOptions();
mapGeneratorOptions.IsMoveOnlyRoad = true;
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddRoad(new Point(100, 100), new Point(140, 150), 10);
generator.AddRoad(new Point(140, 150), new Point(190, 100), 10);
Point startPoint = new Point(100, 100);
Point goalPoint = new Point(190, 100);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 100);
```

**Przykład 4**: Ustawianie parametru Scale w celu szybszego wyszukiwania.

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**Przykład 5**: Przykład wielokrotnego wyszukiwania.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddBlock(200, 1700, 1500, 100, 0);
generator.AddBlock(1700, 200, 100, 1600, 0);
generator.AddBlock(200, 200, 1500, 100, 0);
generator.AddRoad(new Point(1000, 1150), new Point(200, 600), 10);
generator.AddRoad(new Point(50, 450), new Point(150, 1850), 10);

Point startPoint = new Point(1000, 1000);
Point goalPoint = new Point(1900, 1000);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 3500);

Point startPoint = new Point(50, 50);
Point goalPoint = new Point(70, 70);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

Te przykłady kodu budują i wyświetlają ścieżki drogowe na mapie dla określonych punktów, używając informacji o drogach i generatora warstw drogi.

**Podsumowując**, optymalny wyszukiwarka ścieżek to potężne narzędzie do analizy sieci dróg i określania najbardziej efektywnych tras między punktami na mapie. Uwzględnia różne czynniki, takie jak typy dróg, przeszkody oraz różne prędkości, aby obliczyć optymalną ścieżkę. Dzięki możliwości wyszukiwania ścieżek zarówno po drogach, jak i poza drogowych szlakach, a także kontrolowaniu promienia wyszukiwania i dostosowywaniu wydajności i dokładności, ten algorytm zapewnia wszechstronne rozwiązanie do optymalizacji tras. Uwzględniając różne środki transportu i dostosowując zestawy dróg i przeszkód odpowiednio, można go używać w różnych scenariuszach, takich jak planowanie dostaw lub optymalizacja dojazdów do pracy. Kodowe przykłady i wyjaśnienia przedstawione tutaj demonstrują możliwości algorytmu i kroki zaangażowane w jego wykorzystanie. Ostatecznie optymalny wyszukiwarka ścieżek oferuje solidny sposób na znalezienie najbardziej efektywnych tras i poprawę nawigacji w sieci dróg.