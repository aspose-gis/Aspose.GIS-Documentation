---
title: "Rotulagem Simples"
type: docs
url: /pt/net/simple-labeling/
weight: 10
---

## **Rotulagem Simples**
A Rotulagem Simples especifica como os recursos devem ser rotulados.

Opções suportadas são:

|**Propriedade**|**Descrição**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Especifica o nome do atributo a ser usado como fonte dos rótulos.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Fornece uma maneira de personalizar e formatar o texto do rótulo. Substitui LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Especifica a família da fonte a ser usada para renderizar o texto. O padrão é um valor dependente do sistema.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Estilo a ser aplicado ao texto.</p><p>- FontStyle.Regular - texto normal.</p><p>- FontStyle.Bold - texto em negrito.</p><p>- FontStyle.Italic - texto em itálico.</p><p>- FontStyle.Underine - texto sublinhado.</p><p>- FontStyle.StrikeOut - texto com uma linha no meio.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Especifica o tamanho do texto.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Determina a cor do texto.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Determina um tamanho do halo (ou contorno) ao redor do texto.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Determina a cor do halo ao redor do texto.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Expressão de geometria a ser usada para transformar geometrias antes de passá-la para o mecanismo de rotulagem.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Especifica o comportamento de renderização para geometrias multipartes.</p><p>- MultipartMode.All - coloque um rótulo perto de cada parte da geometria.</p><p>- MultipartMode.Any - coloque um rótulo perto de qualquer parte da geometria.</p><p>- MultipartMode.Largest - coloque um rótulo perto da maior parte da geometria.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Especifica como os rótulos são colocados em relação à geometria.</p><p>- PointLabelPlacement - coloca o rótulo perto do centro da geometria.</p><p>- LineLabelPlacement - coloca o rótulo ao longo da geometria ou de seu perímetro.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Especifica a prioridade do rótulo caso ele se sobreponha a outro rótulo.<br>O rótulo com menor prioridade não é renderizado. O padrão é 1000.|

## **Exemplos**
### **Exemplos de Rotulagem de Pontos**
Por padrão, SimpleLabeling desenha texto sobre pontos:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
Aqui está como estilizar a fonte:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
Para controlar a posição do texto em relação ao recurso de ponto, a propriedade de posicionamento deve ser definida:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
Para cenários mais avançados, você pode querer escolher diferentes rotulagens para recursos. Veja como fazer isso:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **Exemplos de Rotulagem de Linhas**
Por padrão, SimpleLabeling desenha um rótulo perto do centro da linha:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
Para girar os rótulos para que sejam paralelos às linhas, LineLabelPlacement com LineLabelAlignment.Parallel pode ser usado:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
Se você quiser que os textos sigam a linha precisamente, LineLabelPlacement com LineLabelAlignment.Curved pode ser usado:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
Se você não quiser que os textos se sobreponham à linha, use LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
Para cenários mais avançados, você pode querer ajustar o estilo dos rótulos dinamicamente com base nos valores do atributo do recurso. Veja como fazer isso:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
