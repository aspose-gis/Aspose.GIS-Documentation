---
title: "Symbolizator znaczników"
type: docs
url: /pl/net/marker-symbolizer/
weight: 10
description: Biblioteka GIS C# lub API obsługuje symbolizator prostych znaczników, który rysuje zdefiniowany kształt z konfigurowalnym wypełnieniem i obrysem na geometriach dowolnego typu, takiego jak Punkt, Linia, Powierzchnia.
---

## **Symbolizator znaczników**
Prosty symbolizator znaczników rysuje zdefiniowany kształt z konfigurowalnym wypełnieniem i obrysem. Jest to domyślny symbolizator dla geometrii 0-wymiarowych (punktów). 

Obsługiwane kształty to:

|![todo:image_alt_text](marker-symbolizer_1.png)|Koło| |![todo:image_alt_text](marker-symbolizer_2.png)|Gwiazda|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Kwadrat| |![todo:image_alt_text](marker-symbolizer_4.png)|Krzyż|
|![todo:image_alt_text](marker-symbolizer_5.png)|Trójkąt| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

Obsługiwane opcje stylizacji:

|**Właściwość**|**Opis**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|Określa kształt znacznika.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|Określa rozmiar kształtu znacznika|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|Określa kolor i przezroczystość wypełnienia|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|Określa kolor i przezroczystość linii|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|Określa szerokość linii|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|Określa, jak linie są renderowane w miejscach przecięcia segmentów linii.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|Określa, jak linia symbolu powinna być rysowana.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|Określa tablicę odległości, która określa długości naprzemiennych kresek i odstępów w liniach kreskowanych.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|Określa odległość od początku linii do początku wzorca kresek.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|Określa rotację symbolu wokół jego środka, w stopniach dziesiętnych. Wartości dodatnie wskazują rotację zgodnie z ruchem wskazówek zegara, wartości ujemne wskazują rotację przeciwnie do ruchu wskazówek zegara. Domyślnie 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|Określa przesunięcie poziome z lokalizacji punktu do punktu zakotwiczenia kształtu.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|Określa przesunięcie pionowe z lokalizacji punktu do punktu zakotwiczenia kształtu.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|Określa, która strona kształtu znacznika będzie wyrównana poziomo do lokalizacji punktu.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|Określa, która strona kształtu znacznika będzie wyrównana pionowo do lokalizacji punktu.|

### **Typy geometrii**
` `Symbolizator może być stosowany do geometrii dowolnego typu.

|**Wymiar geometrii**|**Typy geometrii**|**Zachowanie renderowania**|
| :-: | :-: | :-: |
|**Punkt**|Punkt, MultiPoint|Rysuje kształt wycentrowany na współrzędnej punktu.|
|**Linia**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>Rysuje kształt wycentrowany w środku masy geometrii</p><p> </p>|
|**Powierzchnia**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

W przypadku GeometryCollections zachowanie renderowania jest określane oddzielnie dla każdej geometrii w kolekcji. Warstwy z mieszanym typem geometrii podążają logiką dla GeometryCollections.

Użyj MixedGeometrySymbolizer, aby ograniczyć symbolizator do określonych typów geometrii.

### **Przykłady**
Domyślnie symbolizator znaczników rysuje czarne koła:



Oto jak zmienić kolor wypełnienia na czerwony:




|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

Kolejny przykład stylizacji zdefiniowanym kształtem (trójkąt):




|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----
W bardziej zaawansowanych scenariuszach możesz chcieć dostosować styl znacznika dynamicznie na podstawie wartości atrybutów cech. Oto jak to zrobić:




|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
Możesz również chcieć dodać etykiety do znaczników. Odwiedź [Przykłady etykietowania punktów](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) aby zobaczyć przykłady.
