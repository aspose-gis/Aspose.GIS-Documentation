---
title: "Jak rysować geometrię na mapie"
type: docs
url: /pl/net/how-to-draw-geometry
weight: 70
---

Aby tworzyć i wyświetlać obiekty geometryczne na mapie, musisz zacząć od **utworzenia obiektu geometrii**. Istnieją dwie metody, których możesz użyć:

- **Konstruktor dla każdego typu cechy geometrii**
Ta metoda polega na użyciu niestandardowego konstruktora dla każdego typu cechy geometrii. Na przykład, aby utworzyć punkt, użyjesz następującego kodu:

```
Point point = new Point(40.7128, -74.006);
```

Jednak ta metoda może stać się skomplikowana i uciążliwa w zarządzaniu podczas tworzenia złożonych obiektów, takich jak polilinie lub kolekcje. W rezultacie programista może potrzebować dodać wiele linii kodu, co powoduje spadek czytelności kodu. Zapewnienie integralności danych podczas inicjalizacji również może być trudne. Na przykład rozważ następujący przykład tworzący wielokąt z dziurą w środku:

```
Polygon polygon = new Polygon();

LinearRing ring = new LinearRing();
ring.AddPoint(50.02, 36.22);
ring.AddPoint(49.99, 36.26);
ring.AddPoint(49.97, 36.23);
ring.AddPoint(49.98, 36.17);
ring.AddPoint(50.02, 36.22);

LinearRing hole = new LinearRing();
hole.AddPoint(50.00, 36.22);
hole.AddPoint(49.99, 36.20);
hole.AddPoint(49.98, 36.23);
hole.AddPoint(50.00, 36.24);
hole.AddPoint(50.00, 36.22);

polygon.ExteriorRing = ring;
polygon.AddInteriorRing(hole);
```

Inną wadą tego podejścia jest brak jednolitości danych do inicjalizacji. Nie możesz utworzyć repozytorium stałych lub plików w swoim projekcie.

- **WKT (Well-Known Text)**
Ta metoda polega na generowaniu geometrii z WKT (Well-Known Text), co oferuje standardowy sposób tworzenia geometrii. Poniższy kod demonstruje, jak utworzyć punkt i linię:

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

Chociaż to podejście może nieznacznie zmniejszyć wydajność ze względu na potrzebę parsowania ciągu znaków, upraszcza tworzenie bardziej złożonych obiektów.

Więcej szczegółów na temat WKT można znaleźć w następnym artykule: "Eksportowanie i importowanie danych z/do WKT i WKB".

Wyświetlanie obiektów geometrycznych na mapie
Po utworzeniu obiektu geometrycznego kolejnym krokiem jest wyświetlenie go na mapie. Chociaż mapa może wyświetlać warstwy załadowane z różnych źródeł i formatów, InMemoryLayer to warstwa, która nie wymaga źródła.

**Aby wyświetlić obiekt geometryczny**, możesz utworzyć InMemoryLayer i dodać do niego obiekt:

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

Teraz możesz **wyświetlić tę warstwę na mapie i utworzyć plik w jednym z obsługiwanych formatów**, takich jak SVG, używając następującego kodu:

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

Po dodaniu warstwy i wyświetleniu jej na mapie możesz ją zapisać w dowolnym z obsługiwanych formatów. W tym przykładzie wybrano format SVG, aby uniknąć potencjalnych problemów z obsługą Bitmapy. Ważne jest, aby zauważyć, że Net 6.0 ma ograniczoną obsługę Bitmapy, co może skutkować ograniczeniami, takimi jak niemożność renderowania obrazów Bitmapy za pomocą Blazor WebAsm po stronie klienta. Dlatego przy wyborze formatu do zapisania mapy ważne jest uwzględnienie ograniczeń platformy docelowej i wybranie z nią kompatybilnego formatu.

Artykuł wyjaśnia, jak tworzyć i wyświetlać obiekty geometryczne na mapie w domyślnym, prostym stylu. Jednak biblioteka Aspose oferuje szeroki zakres opcji stylizacji, które można dostosować do swoich potrzeb. Aby zapoznać się z tymi opcjami, zalecamy zapoznanie się z [dokumentacją Aspose.MapRendering]( https://docs.aspose.com/gis/net/map-rendering/), która zawiera szczegółowe informacje o sposobie korzystania z różnych technik stylizacji w celu poprawy atrakcyjności wizualnej mapy.

**Podsumowując**, aby tworzyć obiekty geometryczne na mapie, możesz użyć konstruktora dla każdego typu cechy geometrii lub generować geometrię z WKT. Aby wyświetlić obiekt, umieść go na warstwie i wyświetl warstwę na mapie w domyślnej stylizacji mapy. Zapisz mapę w obsługiwanym formacie, takim jak SVG, i użyj naszej biblioteki, aby zapoznać się z opcjami stylizacji. Dodatkowo nasza biblioteka zapewnia możliwość zobaczenia gotowego przykładu, klikając [link]( https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer) podany w dokumentacji, który może pomóc w zrozumieniu sposobu implementacji tych technik we własnych projektach.
