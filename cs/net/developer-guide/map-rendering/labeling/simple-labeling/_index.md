---
title: "Jednoduché označování"
type: docs
url: /cs/net/simple-labeling/
weight: 10
---

## **Jednoduché označování**
Jednoduché označování specifikuje, jak musí být prvky označeny.

Podporované možnosti jsou:

|**Vlastnost**|**Popis**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Specifikuje název atributu, který se má použít jako zdroj popisků.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Poskytuje způsob, jak přizpůsobit a formátovat text popisku. Přepíše LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Specifikuje rodinu písma, která se má použít pro vykreslování textu. Výchozí hodnota závisí na systému.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Styl, který se má použít na text.</p><p>- FontStyle.Regular - běžný text.</p><p>- FontStyle.Bold - tučný text.</p><p>- FontStyle.Italic - kurzíva.</p><p>- FontStyle.Underine - podtržený text.</p><p>- FontStyle.StrikeOut - text s přeškrtnutím uprostřed.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Specifikuje velikost textu.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Určuje barvu textu.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Určuje velikost lemu (nebo obrysu) kolem textu.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Určuje barvu lemu kolem textu.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Geometrický výraz, který se má použít k transformaci geometrií před jejich předáním do modulu označování.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Specifikuje chování vykreslování pro vícedílné geometrie.</p><p>- MultipartMode.All - umístěte popisek poblíž každé části geometrie.</p><p>- MultipartMode.Any - umístěte jeden popisek poblíž libovolné části geometrie.</p><p>- MultipartMode.Largest - umístěte popisek poblíž největší části geometrie.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Specifikuje, jak jsou popisky umístěny vzhledem k geometrii.</p><p>- PointLabelPlacement - umístí popisek do středu geometrie.</p><p>- LineLabelPlacement - umístí popisek podél geometrie nebo jejího obvodu.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Specifikuje prioritu popisky v případě, že se překrývá s jiným popiskem.<br>Popisek s nižší prioritou není vykreslen. Výchozí hodnota je 1000.|

## **Příklady**
### **Příklady označování bodů**
Ve výchozím nastavení SimpleLabeling kreslí text přes body:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
Zde je postup pro úpravu stylu písma:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
Aby bylo možné ovládat pozici textu vzhledem k bodovému prvku, musí být nastavena vlastnost umístění:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
Pro pokročilejší scénáře můžete chtít zvolit různá označování pro prvky. Zde je postup:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **Příklady označování čar**
Ve výchozím nastavení SimpleLabeling kreslí popisek poblíž středu čáry:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
Aby se popisky otáčely tak, že jsou rovnoběžné s čarami, lze použít LineLabelPlacement s LineLabelAlignment.Parallel:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
Pokud chcete, aby text přesně sledoval čáru, lze použít LineLabelPlacement s LineLabelAlignment.Curved:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
Pokud nechcete, aby se text překrýval s čarou, použijte LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
Pro pokročilejší scénáře můžete chtít upravit styl popisků dynamicky na základě hodnot atributů prvků. Zde je postup:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
