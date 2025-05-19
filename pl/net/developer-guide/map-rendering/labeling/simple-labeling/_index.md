---
title: "Proste Oznaczanie"
type: docs
url: /pl/net/simple-labeling/
weight: 10
---

## **Proste Oznaczanie**
Proste Oznaczanie określa, jak cechy muszą być oznakowane.

Obsługiwane opcje to:

|**Właściwość**|**Opis**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Określa nazwę atrybutu, który ma być używany jako źródło etykiet.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Zapewnia sposób na dostosowanie i sformatowanie tekstu etykiety. Nadpisuje LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Określa rodzinę czcionek, której należy użyć do renderowania tekstu. Domyślna wartość zależy od systemu.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Styl do zastosowania do tekstu.</p><p>- FontStyle.Regular - zwykły tekst.</p><p>- FontStyle.Bold - pogrubiony tekst.</p><p>- FontStyle.Italic - kursywa.</p><p>- FontStyle.Underine - podkreślony tekst.</p><p>- FontStyle.StrikeOut - tekst z linią przez środek.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Określa rozmiar tekstu.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Określa kolor tekstu.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Określa rozmiar halo (lub obrysu) wokół tekstu.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Określa kolor halo wokół tekstu.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Wyrażenie geometrii, które ma być używane do transformacji geometrii przed przekazaniem jej do silnika oznaczania.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Określa zachowanie renderowania dla geometrii wieloczęściowych.</p><p>- MultipartMode.All - umieść etykietę w pobliżu każdej części geometrii.</p><p>- MultipartMode.Any - umieść jedną etykietę w pobliżu dowolnej części geometrii.</p><p>- MultipartMode.Largest - umieść etykietę w pobliżu największej części geometrii.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Określa, jak etykiety są umieszczane względem geometrii.</p><p>- PointLabelPlacement - umieszcza etykietę w pobliżu środka geometrii.</p><p>- LineLabelPlacement - umieszcza etykietę wzdłuż geometrii lub jej obwodu.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Określa priorytet etykiety w przypadku nakładania się z inną etykietą.<br>Etykieta o niższym priorytecie nie jest renderowana. Domyślna wartość to 1000.|

## **Przykłady**
### **Przykłady Oznaczania Punktów**
Domyślnie SimpleLabeling rysuje tekst nad punktami:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
Oto jak stylizować czcionkę:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
Aby kontrolować pozycję tekstu względem cechy punktowej, należy ustawić właściwość placement:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
W bardziej zaawansowanych scenariuszach możesz chcieć wybrać różne etykietowanie dla cech. Oto jak to zrobić:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **Przykłady Oznaczania Linii**
Domyślnie SimpleLabeling rysuje etykietę w pobliżu środka linii:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
Aby obrócić etykiety, aby były równoległe do linii, można użyć LineLabelPlacement z LineLabelAlignment.Parallel:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
Jeśli chcesz, aby teksty precyzyjnie podążały za linią, można użyć LineLabelPlacement z LineLabelAlignment.Curved:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
Jeśli nie chcesz, aby teksty nakładały się na linię, użyj LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
W bardziej zaawansowanych scenariuszach możesz chcieć dostosować styl etykiet dynamicznie w oparciu o wartości atrybutów cech. Oto jak to zrobić:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
