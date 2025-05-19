---
title: "Symbolizator Linii"
type: docs
url: /pl/net/line-symbolizer/
weight: 20
description: Biblioteka GIS C# lub API obsługuje symbolizator linii prostych dla geometrii jednowymiarowych linii i może być stosowany do geometrii dowolnego typu, takiego jak Punkt, Linia, Powierzchnia.
---

## **Symbolizator Linii**
Symbolizator linii prostych rysuje linię ze spersonalizowanym stylem. Jest to domyślny symbolizator dla geometrii jednowymiarowych (linii). 

Obsługiwane opcje stylizacji:

|**Właściwość**|**Opis**|
| :- | :- |
|[Kolor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|Określa kolor i przezroczystość linii.|
|[Szerokość](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|Określa szerokość linii|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|Określa, jak linie są renderowane w miejscach przecięcia segmentów linii.|
|[Styl](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|Określa, jak linia symbolu powinna być rysowana.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|Określa tablicę odległości, która określa długości naprzemiennych kresek i odstępów w liniach kreskowanych.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|Określa odległość od początku linii do początku wzorca kresek.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>Określa, jak linie są renderowane na swoich końcach.</p><p>- Butt - ostry kwadratowy brzeg</p><p>- Round - zaokrąglony brzeg</p><p>- Square - lekko wydłużony kwadratowy brzeg</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|Określa przesunięcie od oryginalnej linii. Dla dodatniej odległości przesunięcie będzie po lewej stronie linii wejściowej (względem kierunku linii). Dla ujemnej odległości będzie po prawej stronie.|

### **Typy Geometrii**
` `Symbolizator może być stosowany do geometrii dowolnego typu.

|**Wymiar Geometrii**|**Typy Geometrii**|**Zachowanie Renderowania**|
| :-: | :-: | :-: |
|**Punkt**|Punkt, MultiPoint|Rysuje linię małej długości z orientacją poziomą wycentrowaną na punkcie, z dwoma zakończeniami.|
|**Linia**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Rysuje linię.|
|**Powierzchnia**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Zamknięty obrys geometrii jest używany jako linia (bez zakończeń)|

Dla GeometryCollections zachowanie renderowania jest określane oddzielnie dla każdej geometrii w kolekcji. Warstwy z mieszanym typem geometrii podążają logiką dla GeometryCollections.

Użyj MixedGeometrySymbolizer, aby ograniczyć symbolizator do określonych typów geometrii.

### **Przykłady**
Domyślnie symbolizator linii rysuje czarne linie:




Oto jak zmienić kolor linii na niebieski:



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

Dla bardziej zaawansowanych scenariuszy możesz chcieć dostosować styl linii dynamicznie w oparciu o wartości atrybutów cech. Oto jak to zrobić:



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |



Możesz również chcieć dodać etykiety do linii. Odwiedź [Przykłady Etykietowania Linii](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) aby zobaczyć przykłady.
