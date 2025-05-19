---
title: "Symbolizér čar"
type: docs
url: /cs/net/line-symbolizer/
weight: 20
description: GIS C# knihovna nebo API podporuje jednoduchý symbolizér čar pro 1-dimenzionální geometrie čar a lze jej aplikovat na geometrie jakéhokoli typu, jako je bod, čára, plocha.
---

## **Symbolizér čar**
Jednoduchý symbolizér čar vykreslí čáru s přizpůsobitelným stylem. Toto je výchozí symbolizér pro 1-dimenzionální geometrie (čáry). 

Podporované možnosti stylingu:

|**Vlastnost**|**Popis**|
| :- | :- |
|[Barva](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simpleline/properties/color)|Specifikuje barvu a průhlednost čáry.|
|[Šířka](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simpleline/properties/width)|Specifikuje šířku čáry|
|[LineJoin](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|Určuje, jak se vykreslují čáry v průsečíkách segmentů čar.|
|[Styl](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simpleline/properties/style)|Specifikuje, jak by měl být symbol linework kreslen.|
|[DashPattern](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|Specifikuje pole vzdáleností, které určují délky střídavých pomlček a mezer v čárkovaných čarách.|
|[DashOffset](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|Specifikuje vzdálenost od začátku čáry k začátku vzoru pomlček.|
|[CapStyle](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>Specifikuje, jak se vykreslují konce čar.</p><p>- Butt - ostrá hranatá hrana</p><p>- Round - zaoblená hrana</p><p>- Square - mírně protáhlá hranatá hrana</p>|
|[Offset](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|Specifikuje odsazení od původní čáry. Pro kladnou vzdálenost bude odsazení na levé straně vstupní čáry (vzhledem k směru čáry). Pro zápornou vzdálenost bude na pravé straně.|

### **Typy geometrií**
` `Symbolizér lze aplikovat na geometrie jakéhokoli typu.

|**Dimenze geometrie**|**Typy geometrií**|**Vykreslovací chování**|
| :-: | :-: | :-: |
|**Bod**|Bod, MultiPoint|Kreslí čáru malé délky s horizontální orientací centrovanou na bodu se dvěma koncovými víčky.|
|**Čára**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Kreslí čáru.|
|**Plocha**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Uzavřený obrys geometrie se používá jako řetězec čar (bez koncových víček)|

Pro GeometryCollections je vykreslovací chování určováno samostatně pro každou geometrii uvnitř kolekce. Vrstvy s Mixed geometry type sledují logiku pro GeometryCollections.

Použijte MixedGeometrySymbolizer k omezení symbolizéru na specifické typy geometrií.

### **Příklady**
Ve výchozím nastavení symbolizér čar kreslí černé čáry:




Zde je postup změny barvy čáry na modrou:



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

-----

Pro pokročilejší scénáře můžete chtít upravit styl čáry dynamicky na základě hodnot atributů prvků. Zde je postup:



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |

-----

Můžete také chtít přidat popisky ke svým čarám. Navštivte [Příklady popiskování čar](/gis/cs/simple-labeling/#simplelabeling-lineslabelingexamples) pro příklady.
