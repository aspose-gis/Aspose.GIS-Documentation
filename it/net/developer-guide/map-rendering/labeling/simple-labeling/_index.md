---
title: "Etichettatura Semplice"
type: docs
url: /it/net/simple-labeling/
weight: 10
---

## **Etichettatura Semplice**
L'etichettatura semplice specifica come devono essere eticchettate le entità.

Le opzioni supportate sono:

|**Proprietà**|**Descrizione**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Specifica il nome dell'attributo da utilizzare come fonte delle etichette.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Fornisce un modo per personalizzare e formattare il testo dell'etichetta. Sovrascrive LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Specifica la famiglia di caratteri da utilizzare per renderizzare il testo. Il valore predefinito dipende dal sistema.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Stile da applicare al testo.</p><p>- FontStyle.Regular - testo normale.</p><p>- FontStyle.Bold - testo in grassetto.</p><p>- FontStyle.Italic - testo corsivo.</p><p>- FontStyle.Underine - testo sottolineato.</p><p>- FontStyle.StrikeOut - testo barrato.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Specifica la dimensione del testo.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Determina il colore del testo.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Determina la dimensione dell'alone (o contorno) attorno al testo.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Determina il colore dell'alone attorno al testo.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Espressione geometrica da utilizzare per trasformare le geometrie prima di passarle al motore di etichettatura.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Specifica il comportamento di rendering per le geometrie multipart.</p><p>- MultipartMode.All - posiziona un'etichetta vicino a ogni parte della geometria.</p><p>- MultipartMode.Any - posiziona un'etichetta vicino a qualsiasi parte della geometria.</p><p>- MultipartMode.Largest - posiziona un'etichetta vicino alla parte più grande della geometria.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Specifica come le etichette sono posizionate rispetto alla geometria.</p><p>- PointLabelPlacement - posiziona l'etichetta vicino al centro della geometria.</p><p>- LineLabelPlacement - posiziona l'etichetta lungo la geometria o il suo perimetro.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Specifica la priorità dell'etichetta nel caso in cui si sovrapponga ad un'altra etichetta.<br>L'etichetta con priorità inferiore non viene renderizzata. Il valore predefinito è 1000.|

## **Esempi**
### **Esempi di Etichettatura Punti**
Per impostazione predefinita, SimpleLabeling disegna il testo sopra i punti:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
Ecco come stilizzare il font:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
Per controllare la posizione del testo rispetto all'entità punto, è necessario impostare la proprietà di posizionamento:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
Per scenari più avanzati, potrebbe essere necessario scegliere etichettature diverse per le entità. Ecco come farlo:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **Esempi di Etichettatura Linee**
Per impostazione predefinita, SimpleLabeling disegna l'etichetta vicino al centro della linea:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
Per ruotare le etichette in modo che siano parallele alle linee, è possibile utilizzare LineLabelPlacement con LineLabelAlignment.Parallel:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
Se si desidera che i testi seguano la linea con precisione, è possibile utilizzare LineLabelPlacement con LineLabelAlignment.Curved:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
Se non si desidera che i testi si sovrappongano alla linea, utilizzare LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
Per scenari più avanzati, potrebbe essere necessario regolare lo stile delle etichette dinamicamente in base ai valori degli attributi dell'entità. Ecco come farlo:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
