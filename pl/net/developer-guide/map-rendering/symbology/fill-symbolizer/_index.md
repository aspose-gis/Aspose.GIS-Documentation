---
title: "Symbolizer wypełnienia"
type: docs
url: /pl/net/fill-symbolizer/
weight: 30
description: Biblioteka GIS C# obsługuje symbolizator prostego wypełnienia, aby styl i obrysować dwuwymiarowe geometrie wielokątów dowolnego typu, takie jak Punkt, Linia, Powierzchnia.
---

## **Symbolizer wypełnienia**
Prosty symbolizator wypełnienia wypełnia obszar konfigurowalnym stylem wypełnienia i obrysem. Jest to domyślny symbolizator dla geometrii dwuwymiarowych (wielokątów). 

Jeśli wielokąt ma „dziury”, nie są one wypełniane, ale granice wokół dziur są rysowane w zwykły sposób. „Wyspy” wewnątrz dziur są wypełnione i obrysowane i tak dalej.

Obsługiwane opcje stylizacji:

|**Właściwość**|**Opis**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Określa kolor i przezroczystość wypełnienia.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - Pełne wypełnienie</p><p>- None - Nie wypełniaj wielokąta</p><p>- Horizontal Hatch - Wzór poziomych linii.</p><p>- Vertical Hatch - Wzór pionowych linii.</p><p>- Cross Hatch - Określa poziome i pionowe linie, które się krzyżują.</p><p>- Forward Diagonal Hatch - Wzór linii po przekątnej od lewego górnego rogu do prawego dolnego rogu.</p><p>- Backward Diagonal Hatch - Wzór linii po przekątnej od prawego górnego rogu do lewego dolnego rogu.</p><p>- Diagonal Cross Hatch - Wzór krzyżujących się linii po przekątnej.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Określa kolor i przezroczystość obrysu.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Określa, jak mają być rysowane linie symbolu.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Określa szerokość linii obrysu.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Określa tablicę odległości, która określa długości naprzemiennych kresek i odstępów w liniach kreskowanych.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Określa odległość od początku linii do początku wzoru kresek.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Określa, jak linie są renderowane w miejscach przecięcia segmentów linii.</p><p>- Miter - ostry róg</p><p>- Round - zaokrąglony róg</p><p>- Bevel - ukośny róg</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Określa przesunięcie poziome od lokalizacji punktu do punktu zakotwiczenia kształtu.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Określa przesunięcie pionowe od lokalizacji punktu do punktu zakotwiczenia kształtu.|

### **Typy geometrii**
` `Symbolizator może być stosowany do geometrii dowolnego typu.

|**Wymiar geometrii**|**Typy geometrii**|**Zachowanie renderowania**|
| :-: | :-: | :-: |
|**Punkt**|Punkt, MultiPoint|Rysuje mały kwadratowy wielokąt prostopadny.|
|**Linia**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Linia jest zamykana w celu wypełnienia przez połączenie punktu końcowego z punktem początkowym. Tylko oryginalna linia jest obrysowana.|
|**Powierzchnia**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Rysuje wielokąt.|

W przypadku GeometryCollections zachowanie renderowania jest określane oddzielnie dla każdej geometrii w kolekcji. Warstwy z mieszanym typem geometrii podążają logiką dla GeometryCollections.

Użyj MixedGeometrySymbolizer, aby ograniczyć symbolizator do określonych typów geometrii.

### **Przykłady**
Domyślnie Simple Fill symbolizer rysuje czarną linię obrysu i pełne białe wypełnienie:



Tutaj jak zmienić stylizację:



|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

-----
Możesz również dodać etykiety do swoich wielokątów. Odwiedź [Przykłady etykietowania linii](/gis/pl/simple-labeling/#simplelabeling-lineslabelingexamples) aby zobaczyć przykłady, jak etykietować granice wielokątów lub [Przykłady etykietowania punktów](/gis/pl/simple-labeling/#simplelabeling-pointslabelingexamples) na przykładach, jak etykietować centra wielokątów.
