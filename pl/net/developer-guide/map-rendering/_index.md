---
title: Renderowanie mapy do obrazu SVG, PNG, JPG za pomocą biblioteki GIS C#
linktitle: "Renderowanie mapy"
type: docs
url: /pl/net/map-rendering/
weight: 50
description: Dzięki API GIS C# możesz renderować mapę z plików Shapefile, FileGDB, GeoJSON, KML, wykonywać zaawansowane style i rysować mapy z formatów rastrowych.
---

## **Przegląd renderowania map**
Dzięki API Aspose.GIS dla .NET C# możesz renderować mapę z pliku Shapefile, FileGDB, GeoJSON, KML lub innych [obsługiwanych formatów plików](/gis/net/supported-file-formats/) do SVG, PNG, JPEG lub BMP.

Oto kod C#, który ilustruje sposób renderowania mapy z pliku shapefile do SVG przy użyciu domyślnych ustawień:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



Oto wynik:



![renderowanie mapy](map_rendering.png)

Przyjrzyjmy się bliżej kodowi.

Najpierw tworzymy obiekt [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map). Reprezentuje on kolekcję warstw z różnych źródeł, które mogą być renderowane. Mapa ma rozmiar, w którym ma być wyświetlana. Tutaj ustawiamy mapę na 800 pikseli szerokości i 400 pikseli wysokości.

Zauważ, że mapa jest zamknięta w instrukcji using. Jest to konieczne, ponieważ mapa śledzi wszystkie zasoby dodane do niej i usuwa je po zakończeniu renderowania i usunięciu obiektu Mapy.

Następnie dodajemy warstwę z pliku do mapy. Każda warstwa jest renderowana na wierzchu poprzedniej warstwy, w kolejności, w jakiej zostały dodane do mapy. Więcej szczegółów o tym, jak otwierać warstwy wektorowe, można znaleźć [tutaj](/gis/net/working-with-vector-layers/).

Na koniec wywołujemy metodę [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1), aby renderować mapę do pliku. Określamy ścieżkę, w której ma zostać zapisany wynikowy plik i renderer do użycia. Klasa [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) zawiera odwołania do wszystkich rendererów zawartych w Aspose.GIS. Na przykład możesz określić Renderers.Png zamiast Renderers.Svg w powyższym przykładzie, aby renderować mapę do pliku PNG

## **Zaawansowane stylizowanie**
Dzięki API Aspose.GIS możesz dostosowywać renderowanie i style cech, aby osiągnąć pożądany wygląd.

![zaawansowane stylizowanie](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **Rysowanie rastra na mapie**
Dzięki Aspose.GIS dla .NET możesz renderować mapę z formatów rastrowych.
### **Renderowanie z domyślnymi ustawieniami**
Oto jak renderować mapę z GeoTIFF do SVG przy użyciu domyślnych ustawień:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![domyślny rastr](default_raster.png)
### **Renderowanie skośnych rastrów**
Dzięki Aspose.GIS możesz renderować rastry ze skośnymi komórkami rastrowymi.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![skośny rastr](skew_raster.png)
### **Renderowanie w biegunowym układzie współrzędnych**
Aspose.GIS umożliwia używanie biegunowych układów współrzędnych w procesie renderowania mapy.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![gnomoniczne kraje](gnomonic_countries.png)
