---
title: "Fill Symbolizer"
type: docs
url: /nl/fill-symbolizer/
weight: 30
description: GIS C# Library API ondersteunt Simple Fill symbolizer om stijl en streep voor 2-dimensionale geometrie polygonen van elk type toe te passen, zoals Punt, Lijn, Oppervlakte.
---

## **Fill Symbolizer**
De Simple Fill symbolizer vult een gebied met een aanpasbare vulstijl en streep. Dit is de standaard symbolizer voor 2-dimensionale geometrieën (polygonen). 

Als een polygoon “gaten” heeft, worden deze niet gevuld, maar worden de randen rond de gaten op de gebruikelijke manier gestrepen. “Eilanden” binnen gaten worden gevuld en gestrepen, enzovoort.

Ondersteunde stijlmogelijkheden:

|**Property**|**Description**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Specificeert de kleur en transparantie die aan de vulling wordt gegeven.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - Effen vulling</p><p>- None - Vul de polygoon niet</p><p>- Horizontal Hatch - Een patroon van horizontale lijnen.</p><p>- Vertical Hatch - Een patroon van verticale lijnen.</p><p>- Cross Hatch - Specificeert horizontale en verticale lijnen die elkaar kruisen.</p><p>- Forward Diagonal Hatch - Een patroon van lijnen op een diagonaal van linksboven naar rechtsonder.</p><p>- Backward Diagonal Hatch - Een patroon van lijnen op een diagonaal van rechtsboven naar linksonder.</p><p>- Diagonal Cross Hatch - Een patroon van kruisende diagonale lijnen.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Specificeert de kleur en transparantie die aan de streep lijn wordt gegeven.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Specificeert hoe het symbool liniewerk moet worden getekend.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Specificeert de breedte van de streep lijn.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Specificeert een array van afstanden die de lengtes van alternerende strepen en tussenruimtes in gestreepte lijnen specificeren.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Specificeert de afstand vanaf het begin van een lijn tot het begin van een streep patroon.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Bepaalt hoe lijnen worden weergegeven op kruispunten van lijnsegmenten.</p><p>- Miter - scherpe hoek</p><p>- Round - afgeronde hoek</p><p>- Bevel - diagonale hoek</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Specificeert horizontale offset van een puntlocatie naar het vormankerpunt.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Specificeert verticale offset van een puntlocatie naar het vormankerpunt.|

### **Geometry Types**
` `De symbolizer kan worden toegepast op geometrieën van elk type.

|**Geometry Dimension**|**Geometry Types**|**Rendering Behavior**|
| :-: | :-: | :-: |
|**Point**|Point, MultiPoint|Tekent een klein vierkant orthogonaal polygoon.|
|**Line**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|De lijn wordt gesloten voor vulling door het eindpunt met het startpunt te verbinden. Alleen de originele lijn wordt gestrepen.|
|**Surface**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Tekent de polygoon.|

Voor GeometryCollections wordt het renderinggedrag afzonderlijk bepaald voor elke geometrie in de collectie. Lagen met Mixed geometry type volgen de logica voor GeometryCollections.

Gebruik MixedGeometrySymbolizer om een symbolizer te beperken tot specifieke geometrietypen.

### **Examples**
Standaard tekent de Simple Fill symbolizer een zwarte streep lijn en effen witte vulling:



Hier is hoe u styling kunt wijzigen:




|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

-----
U wilt mogelijk ook labels aan uw polygonen toevoegen. Bezoek [Lines Labeling Examples](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) voor voorbeelden over hoe u de rand van polygonen kunt labelen of [Points Labeling Examples](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) op voorbeelden over hoe u de centra van polygonen kunt labelen.
