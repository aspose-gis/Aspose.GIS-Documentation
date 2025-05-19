---
title: "Étiquetage simple"
type: docs
url: /fr/net/simple-labeling/
weight: 10
---

## **Étiquetage simple**
L'étiquetage simple spécifie comment les entités doivent être étiquetées.

Les options prises en charge sont :

|**Propriété**|**Description**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Spécifie le nom de l'attribut à utiliser comme source des étiquettes.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Fournit un moyen de personnaliser et de formater le texte de l'étiquette. Remplace LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Spécifie la famille de polices à utiliser pour rendre le texte. La valeur par défaut dépend du système.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Style à appliquer au texte.</p><p>- FontStyle.Regular - texte normal.</p><p>- FontStyle.Bold - texte en gras.</p><p>- FontStyle.Italic - texte italique.</p><p>- FontStyle.Underine - texte souligné.</p><p>- FontStyle.StrikeOut - texte barré.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Spécifie la taille du texte.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Détermine la couleur du texte.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Détermine la taille de l'auréole (ou du contour) autour du texte.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Détermine la couleur de l'auréole autour du texte.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Expression géométrique à utiliser pour transformer les géométries avant de les transmettre au moteur d'étiquetage.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Spécifie le comportement du rendu pour les géométries multiparts.</p><p>- MultipartMode.All - place une étiquette près de chaque partie de la géométrie.</p><p>- MultipartMode.Any - place une étiquette près d'une quelconque partie de la géométrie.</p><p>- MultipartMode.Largest - place une étiquette près de la plus grande partie de la géométrie.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Spécifie comment les étiquettes sont placées par rapport à la géométrie.</p><p>- PointLabelPlacement - place l'étiquette près du centre de la géométrie.</p><p>- LineLabelPlacement - place l'étiquette le long de la géométrie ou de son périmètre.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Spécifie la priorité de l'étiquette en cas de chevauchement avec une autre étiquette.<br>L'étiquette ayant la priorité la plus faible n'est pas rendue. La valeur par défaut est 1000.|

## **Exemples**
### **Exemples d'étiquetage des points**
Par défaut, SimpleLabeling dessine du texte sur les points :

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
Voici comment styliser la police :

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
Afin de contrôler la position du texte par rapport à l'entité ponctuelle, la propriété placement doit être définie :

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
Pour des scénarios plus avancés, vous pouvez souhaiter choisir différents étiquetages pour les entités. Voici comment faire :

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **Exemples d'étiquetage des lignes**
Par défaut, SimpleLabeling dessine une étiquette près du centre de la ligne :

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
Afin de faire pivoter les étiquettes afin qu'elles soient parallèles aux lignes, LineLabelPlacement avec LineLabelAlignment.Parallel peut être utilisé :

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
Si vous voulez que les textes suivent précisément la ligne, LineLabelPlacement avec LineLabelAlignment.Curved peut être utilisé :

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
Si vous ne voulez pas que les textes chevauchent la ligne, utilisez LineLabelPlacement.Offset :

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
Pour des scénarios plus avancés, vous pouvez souhaiter ajuster le style des étiquettes dynamiquement en fonction des valeurs d'attribut de l'entité. Voici comment faire :

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
