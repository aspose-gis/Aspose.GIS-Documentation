---
title: "Eenvoudige Labeling"
type: docs
url: /nl/net/simple-labeling/
weight: 10
---

## **Eenvoudige Labeling**
De Simple Labeling specificeert hoe features gelabeld moeten worden.

Ondersteunde opties zijn:

|**Property**|**Beschrijving**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Specificeert de attribuutnaam die als bron voor labels moet worden gebruikt.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Biedt een manier om labeltekst aan te passen en op te maken. Overschrijft LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Specificeert het lettertype dat gebruikt moet worden om de tekst weer te geven. De standaardwaarde is afhankelijk van het systeem.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Stijl die op de tekst moet worden toegepast.</p><p>- FontStyle.Regular - normale tekst.</p><p>- FontStyle.Bold - vetgedrukte tekst.</p><p>- FontStyle.Italic - cursieve tekst.</p><p>- FontStyle.Underine - onderstreepte tekst.</p><p>- FontStyle.StrikeOut - tekst met een lijn erdoorheen.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Specificeert de grootte van de tekst.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Bepaalt de kleur van de tekst.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Bepaalt de grootte van de halo (of omtrek) rond de tekst.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Bepaalt de kleur van de halo rond de tekst.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Geometrie-expressie die gebruikt moet worden om geometrieën te transformeren voordat deze naar de labeling engine worden doorgegeven.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Specificeert het rendergedrag voor multipart-geometrieën.</p><p>- MultipartMode.All - plaats een label bij elk onderdeel van de geometrie.</p><p>- MultipartMode.Any - plaats één label bij een willekeurig onderdeel van de geometrie.</p><p>- MultipartMode.Largest - plaats een label bij het grootste onderdeel van de geometrie.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Specificeert hoe labels ten opzichte van de geometrie worden geplaatst.</p><p>- PointLabelPlacement - plaatst label in het midden van de geometrie.</p><p>- LineLabelPlacement - plaatst label langs de geometrie of de omtrek ervan.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Specificeert de prioriteit van het label in geval van overlap met een ander label.<br>Het label met een lagere prioriteit wordt niet weergegeven. Standaard is 1000.|

## **Voorbeelden**
### **Punten Labeling Voorbeelden**
Standaard tekent SimpleLabeling tekst over punten:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
Hier is hoe je de lettertype kunt stylen:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
Om de tekstpositie ten opzichte van het puntkenmerk te regelen, moet de placement property worden ingesteld:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
Voor meer geavanceerde scenario's wilt u mogelijk verschillende labelings voor kenmerken kiezen. Zo doe je dat:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **Lijnen Labeling Voorbeelden**
Standaard tekent SimpleLabeling een label in het midden van de lijn:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
Om labels te roteren zodat ze parallel aan de lijnen lopen, kan LineLabelPlacement met LineLabelAlignment.Parallel worden gebruikt:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
Als u wilt dat teksten de lijn precies volgen, kan LineLabelPlacement met LineLabelAlignment.Curved worden gebruikt:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
Als u niet wilt dat teksten de lijn overlappen, gebruikt u LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
Voor meer geavanceerde scenario's wilt u mogelijk de labelstijl dynamisch aanpassen op basis van kenmerkattribuutwaarden. Zo doe je dat:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
