---
title: "Výplňový Symbolizér"
type: docs
url: /cs/net/fill-symbolizer/
weight: 30
description: GIS C# knihovna API podporuje jednoduchý výplňový symbolizér pro vyplnění stylu a obrysu pro 2-dimenzionální geometrie polygonů jakéhokoli typu, jako je bod, čára, plocha.
---

## **Výplňový Symbolizér**
Jednoduchý výplňový symbolizér vyplní oblast přizpůsobitelným stylem výplně a obrysem. Toto je výchozí symbolizér pro 2-dimenzionální geometrie (polygony).

Pokud má polygon „díry“, nejsou vyplněny, ale okraje kolem děr jsou obrysovány běžným způsobem. „Ostrov“ uvnitř děr je vyplněn a obrysován a tak dále.

Podporované možnosti stylingu:

|**Vlastnost**|**Popis**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Specifikuje barvu a průhlednost výplně.|
|[FillStyle](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - Pevná výplň</p><p>- None - Nevyplňovat polygon</p><p>- Horizontal Hatch - Vzor vodorovných čar.</p><p>- Vertical Hatch - Vzor svislých čar.</p><p>- Cross Hatch - Specifikuje vodorovné a svislé čáry, které se kříží.</p><p>- Forward Diagonal Hatch - Vzor čar diagonálně zleva nahoře doprava dolů.</p><p>- Backward Diagonal Hatch - Vzor čar diagonálně zprava nahoře doleva dolů.</p><p>- Diagonal Cross Hatch - Vzor zkřížených diagonálních čar.</p>|
|[StrokeColor](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Specifikuje barvu a průhlednost obrysové čáry.|
|[StrokeStyle](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Specifikuje, jak by měly být kresleny symbolové linky.|
|[StrokeWidth](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Specifikuje šířku obrysové čáry.|
|[StrokeDashPattern](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Specifikuje pole vzdáleností, které určují délky střídavých pomlček a mezer v přerušovaných čarách.|
|[StrokeDashOffset](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Specifikuje vzdálenost od začátku čáry k začátku vzoru pomlček.|
|[StrokeLineJoin](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Určuje, jak se čáry vykreslují v průsečících segmentů čar.</p><p>- Miter - ostrý roh</p><p>- Round - zaoblený roh</p><p>- Bevel - diagonální roh</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Specifikuje horizontální posun od umístění bodu k kotvícímu bodu tvaru.|
|[VerticalOffset](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Specifikuje vertikální posun od umístění bodu k kotvícímu bodu tvaru.|

### **Typy Geometrií**
` `Symbolizér lze použít na geometrie jakéhokoli typu.

|**Rozměr Geometrie**|**Typy Geometrií**|**Vykreslovací Chování**|
| :-: | :-: | :-: |
|**Bod**|Bod, MultiPoint|Kreslí malý čtvercový ortogonální polygon.|
|**Čára**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Čára je uzavřena pro vyplnění spojením koncového bodu se startovním bodem. Pouze původní čára je obrysována.|
|**Plocha**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Kreslí polygon.|

Pro GeometryCollections je vykreslovací chování určováno samostatně pro každou geometrii uvnitř kolekce. Vrstvy s mísící geometrií sledují logiku pro GeometryCollections.

Použijte MixedGeometrySymbolizer k omezení symbolizéru na specifické typy geometrií.

### **Příklady**
Ve výchozím nastavení Simple Fill symbolizér kreslí černou obrysovou čáru a pevnou bílou výplň:




Zde je, jak změnit styl:



|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

-----
Měli byste také chtít přidat popisky k polygonům. Navštivte [Příklady Popisování Čar](/gis/cs/simple-labeling/#simplelabeling-lineslabelingexamples) pro příklady, jak označovat okraje polygonů nebo [Příklady Popisování Bodů](/gis/cs/simple-labeling/#simplelabeling-pointslabelingexamples) na příkladech, jak označovat středy polygonů.
