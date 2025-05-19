---
title: "Symbolizér značek"
type: docs
url: /cs/net/marker-symbolizer/
weight: 10
description: GIS C# knihovna nebo API podporuje jednoduchý symbolizér značek, který kreslí předdefinovaný tvar s přizpůsobitelným výplní a obrysem na geometriích jakéhokoli typu, jako je bod, čára, plocha.
---

## **Symbolizér značek**
Jednoduchý symbolizér značek kreslí předdefinovaný tvar s přizpůsobitelným výplní a obrysem. Toto je výchozí symbolizér pro 0-rozměrné geometrie (body). 

Podporované tvary jsou:

|![todo:image_alt_text](marker-symbolizer_1.png)|Kruh| |![todo:image_alt_text](marker-symbolizer_2.png)|Hvězda|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Čtverec| |![todo:image_alt_text](marker-symbolizer_4.png)|Kříž|
|![todo:image_alt_text](marker-symbolizer_5.png)|Trojúhelník| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

Podporované možnosti stylingu:

|**Vlastnost**|**Popis**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|Specifikuje tvar značky.|
|[Size](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|Specifikuje velikost tvaru značky|
|[FillColor](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|Specifikuje barvu a průhlednost výplně|
|[StrokeColor](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|Specifikuje barvu a průhlednost čáry|
|[StrokeWidth](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|Specifikuje šířku čáry|
|[StrokeLineJoin](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|Určuje, jak se čáry vykreslují v průsečících segmentů.|
|[StrokeStyle](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|Specifikuje, jak by měl být linework symbolu kreslen.|
|[StrokeDashPattern](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|Specifikuje pole vzdáleností, které určují délky střídavých čárek a mezer v přerušovaných čarách.|
|[StrokeDashOffset](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|Specifikuje vzdálenost od začátku čáry k začátku vzoru čárkování.|
|[Rotation](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|Specifikuje otočení symbolu kolem jeho středního bodu, v desetinných stupních. Kladné hodnoty označují otáčení ve směru hodinových ručiček, záporné hodnoty označují otáčení proti směru hodinových ručiček. Výchozí hodnota je 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|Specifikuje horizontální posun od umístění bodu k kotvícímu bodu tvaru.|
|[VerticalOffset](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|Specifikuje vertikální posun od umístění bodu ke kotvícímu bodu tvaru.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|Specifikuje, která strana tvaru značky bude vodorovně zarovnána s umístěním bodu.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/cs/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|Specifikuje, která strana tvaru značky bude vertikálně zarovnána s umístěním bodu.|

### **Typy geometrií**
` `Symbolizér lze použít na geometrie jakéhokoli typu.

|**Dimenze geometrie**|**Typy geometrií**|**Vykreslovací chování**|
| :-: | :-: | :-: |
|**Bod**|Bod, MultiPoint|Kreslí tvar centrovaný v souřadnici bodu.|
|**Čára**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>Kreslí tvar centrovaný ve středu geometrie</p><p> </p>|
|**Plocha**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

Pro GeometryCollections se vykreslovací chování určuje samostatně pro každou geometrii uvnitř kolekce. Vrstvy s mícháním geometrií sledují logiku pro GeometryCollections.

Použijte MixedGeometrySymbolizer k omezení symbolizéru na specifické typy geometrií.

### **Příklady**
Ve výchozím nastavení symbolizér značek kreslí černé kruhy:



Zde je postup změny barvy výplně na červenou:



|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

Další příklad stylingu s předdefinovaným tvarem (trojúhelník):



|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----

Pro pokročilejší scénáře můžete chtít upravit styl značky dynamicky na základě hodnot atributů prvků. Zde je postup:



|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----

Můžete také chtít přidat popisky ke svým značkám. Navštivte [Příklady označování bodů](/gis/cs/simple-labeling/#simplelabeling-pointslabelingexamples) pro příklady.
