---
title: "Einfache Beschriftung"
type: docs
url: /de/net/simple-labeling/
weight: 10
---

## **Einfache Beschriftung**
Die einfache Beschriftung legt fest, wie Features beschriftet werden müssen.

Unterstützte Optionen sind:

|**Eigenschaft**|**Beschreibung**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Gibt den Attributnamen an, der als Quelle für die Beschriftungen verwendet werden soll.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Bietet eine Möglichkeit zum Anpassen und Formatieren des Beschriftungstextes. Überschreibt LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Gibt die Schriftfamilie an, die zum Rendern des Textes verwendet werden soll. Der Standardwert ist ein systemabhängiger Wert.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Stil, der auf den Text angewendet werden soll.</p><p>- FontStyle.Regular - normaler Text.</p><p>- FontStyle.Bold - fetter Text.</p><p>- FontStyle.Italic - kursiver Text.</p><p>- FontStyle.Underine - unterstrichener Text.</p><p>- FontStyle.StrikeOut - Text mit einer Linie in der Mitte.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Gibt die Größe des Textes an.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Bestimmt die Farbe des Textes.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Bestimmt die Größe des Halos (oder der Umrandung) um den Text.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Bestimmt die Farbe des Halos um den Text.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Geometrieausdruck, der verwendet werden soll, um Geometrien zu transformieren, bevor sie an die Beschriftungs-Engine übergeben werden.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Gibt das Renderingverhalten für mehrteilige Geometrien an.</p><p>- MultipartMode.All - Platzieren Sie eine Beschriftung in der Nähe jedes Teils der Geometrie.</p><p>- MultipartMode.Any - Platzieren Sie eine Beschriftung in der Nähe eines beliebigen Teils der Geometrie.</p><p>- MultipartMode.Largest - Platzieren Sie eine Beschriftung in der Nähe des größten Teils der Geometrie.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Gibt an, wie Beschriftungen relativ zur Geometrie platziert werden.</p><p>- PointLabelPlacement - Platziert die Beschriftung in der Nähe des Zentrums der Geometrie.</p><p>- LineLabelPlacement - Platziert die Beschriftung entlang der Geometrie oder ihres Umfangs.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Gibt die Priorität der Beschriftung an, falls sie sich mit einer anderen Beschriftung überschneidet.<br>Die Beschriftung mit niedrigerer Priorität wird nicht gerendert. Standardmäßig ist 1000.|

## **Beispiele**
### **Punktbeschriftungsbeispiele**
Standardmäßig zeichnet SimpleLabeling Text über Punkte:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
So gestalten Sie eine Schrift:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
Um die Textposition relativ zum Punktfeature zu steuern, muss die Eigenschaft Placement gesetzt werden:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
Für fortgeschrittenere Szenarien möchten Sie möglicherweise verschiedene Beschriftungen für Features auswählen. So geht's:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **Linienbeschriftungsbeispiele**
Standardmäßig zeichnet SimpleLabeling eine Beschriftung in der Nähe des Zentrums der Linie:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
Um die Beschriftungen so zu drehen, dass sie parallel zu den Linien verlaufen, kann LineLabelPlacement mit LineLabelAlignment.Parallel verwendet werden:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
Wenn Sie möchten, dass Texte die Linie präzise verfolgen, kann LineLabelPlacement mit LineLabelAlignment.Curved verwendet werden:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
Wenn Sie nicht möchten, dass sich Texte mit der Linie überschneiden, verwenden Sie LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
Für fortgeschrittenere Szenarien möchten Sie möglicherweise den Beschriftungsstil dynamisch basierend auf den Attributwerten des Features anpassen. So geht's:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
