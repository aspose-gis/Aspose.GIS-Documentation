---
title: "Marker Symbolizer"
type: docs
url: /nl/marker-symbolizer/
weight: 10
description: GIS C# Library of API ondersteunt Simple Marker symbolizer die een vooraf gedefinieerde vorm tekent met aanpasbare vulling en omtrek op geometrieën van elk type zoals Punt, Lijn, Oppervlak.
---

## **Marker Symbolizer**
De Simple Marker symbolizer tekent een vooraf gedefinieerde vorm met aanpasbare vulling en omtrek. Dit is de standaard symbolizer voor 0-dimensionale geometrieën (punten). 

Ondersteunde vormen zijn:

|![todo:image_alt_text](marker-symbolizer_1.png)|Cirkel| |![todo:image_alt_text](marker-symbolizer_2.png)|Ster|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Vierkant| |![todo:image_alt_text](marker-symbolizer_4.png)|Kruis|
|![todo:image_alt_text](marker-symbolizer_5.png)|Driehoek| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

Ondersteunde styling opties:

|**Eigenschap**|**Beschrijving**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|Specificeert de vorm van de marker.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|Specificeert de grootte van de markervorm|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|Specificeert de kleur en transparantie die aan de vulling worden gegeven|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|Specificeert de kleur en transparantie die aan de lijn worden gegeven|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|Specificeert de breedte van de lijn|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|Bepaalt hoe lijnen worden weergegeven op kruispunten van lijnsegmenten.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|Specificeert hoe het symbol linework moet worden getekend.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|Specificeert een array van afstanden die de lengtes van alternerende streepjes en spaties in gestreepte lijnen specificeren.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|Specificeert de afstand vanaf het begin van een lijn tot het begin van een streepjespatroon.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|Specificeert de rotatie van het symbool rond zijn middelpunt, in decimalen graden. Positieve waarden geven rotatie aan in de klok mee richting, negatieve waarden geven tegen de klok in rotatie aan. Standaard is 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|Specificeert horizontale offset van een puntlocatie naar het vormankerpunt.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|Specificeert verticale offset van een puntlocatie naar het vormankerpunt.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|Specificeert welke kant van een markervorm horizontaal uitgelijnd zal worden met de puntlocatie.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|Specificeert welke kant van een markervorm verticaal uitgelijnd zal worden met de puntlocatie.|

### **Geometry Types**
` `De symbolizer kan worden toegepast op geometrieën van elk type.

|**Geometry Dimension**|**Geometry Types**|**Rendering Behavior**|
| :-: | :-: | :-: |
|**Point**|Point, MultiPoint|Tekent de vorm gecentreerd op de puntcoördinaat.|
|**Line**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>Tekent de vorm gecentreerd op het zwaartepunt van de geometrie</p><p> </p>|
|**Surface**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

Voor GeometryCollections wordt het renderinggedrag afzonderlijk bepaald voor elke geometrie in de collectie. Lagen met Mixed geometry type volgen de logica voor GeometryCollections.

Gebruik MixedGeometrySymbolizer om een symbolizer te beperken tot specifieke geometrietypen.

### **Examples**
Standaard tekent de marker symbolizer zwarte cirkels:



Hier is hoe u de vulkleur kunt wijzigen in rood:




|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

Een ander voorbeeld van styling met een vooraf gedefinieerde vorm (driehoek):




|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----
Voor meer geavanceerde scenario's wilt u mogelijk de markerstijl dynamisch aanpassen op basis van kenmerkwaarden van features. Zo doet u dat:




|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
U wilt mogelijk ook labels toevoegen aan uw markers. Bezoek [Points Labeling Examples](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) voor voorbeelden.
