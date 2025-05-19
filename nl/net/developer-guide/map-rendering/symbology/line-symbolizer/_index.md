---
title: "Lijn Symbolizer"
type: docs
url: /nl/net/line-symbolizer/
weight: 20
description: GIS C# Bibliotheek of API ondersteunt Simple Line symbolizer voor 1-dimensionale geometrieën lijnen en kan worden toegepast op geometrieën van elk type zoals Punt, Lijn, Oppervlak.
---

## **Lijn Symbolizer**
De Simple Line symbolizer tekent een lijn met aanpasbare stijl. Dit is de standaard symbolizer voor 1-dimensionale geometrieën (lijnen). 

Ondersteunde styling opties:

|**Eigenschap**|**Beschrijving**|
| :- | :- |
|[Kleur](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|Specificeert de kleur en transparantie die aan de lijn worden gegeven.|
|[Breedte](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|Specificeert de breedte van de lijn|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|Bepaalt hoe lijnen worden weergegeven op kruispunten van lijnsegmenten.|
|[Stijl](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|Specificeert hoe de symbool linework moet worden getekend.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|Specificeert een array van afstanden die de lengtes van alternerende streepjes en spaties in gestreepte lijnen specificeren.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|Specificeert de afstand vanaf het begin van een lijn tot het begin van een dashpatroon.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>Specificeert hoe lijnen worden weergegeven aan hun uiteinden.</p><p>- Butt - scherpe vierkante rand</p><p>- Round - afgeronde rand</p><p>- Square - lichtelijk verlengde vierkante rand</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|Specificeert offset van de originele lijn. Voor een positieve afstand bevindt de offset zich aan de linkerkant van de invoerlijn (relatief ten opzichte van de lijndichting). Voor een negatieve afstand bevindt deze zich aan de rechterkant.|

### **Geometrie Types**
` `De symbolizer kan worden toegepast op geometrieën van elk type.

|**Geometrie Dimensie**|**Geometrie Types**|**Rendering Gedrag**|
| :-: | :-: | :-: |
|**Punt**|Punt, MultiPoint|Tekent een lijn met een kleine lengte met een horizontale oriëntatie gecentreerd op het punt, met twee eindkappen.|
|**Lijn**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Tekent de lijn.|
|**Oppervlak**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Gesloten omtrek van de geometrie wordt gebruikt als de lijnstring (zonder eindkappen)|

Voor GeometryCollections wordt het rendering gedrag afzonderlijk bepaald voor elke geometrie in de collectie. Lagen met Mixed geometry type volgen de logica voor GeometryCollections.

Gebruik MixedGeometrySymbolizer om een symbolizer te beperken tot specifieke geometrietypes.

### **Voorbeelden**
Standaard tekent de lijn symbolizer zwarte lijnen:




Hier is hoe je de lijnkleur naar blauw kunt veranderen:



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

Voor meer geavanceerde scenario's wilt u mogelijk de lijnstijl dynamisch aanpassen op basis van kenmerkwaarden. Zo doe je dat:



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |




U wilt mogelijk ook labels aan uw lijnen toevoegen. Bezoek [Lijn Labeling Voorbeelden](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) voor voorbeelden.
