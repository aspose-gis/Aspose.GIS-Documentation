---
title: "Etiquetado Simple"
type: docs
url: /es/net/simple-labeling/
weight: 10
---

## **Etiquetado Simple**
El Etiquetado Simple especifica cómo se deben etiquetar las entidades.

Opciones compatibles son:

|**Propiedad**|**Descripción**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Especifica el nombre del atributo que se utilizará como fuente de las etiquetas.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Proporciona una forma de personalizar y formatear el texto de la etiqueta. Anula LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Especifica la familia de fuentes que se utilizará para renderizar el texto. El valor predeterminado depende del sistema.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Estilo a aplicar al texto.</p><p>- FontStyle.Regular - texto normal.</p><p>- FontStyle.Bold - texto en negrita.</p><p>- FontStyle.Italic - texto en cursiva.</p><p>- FontStyle.Underine - texto subrayado.</p><p>- FontStyle.StrikeOut - texto tachado.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Especifica el tamaño del texto.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Determina el color del texto.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Determina el tamaño del halo (o contorno) alrededor del texto.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Determina el color del halo alrededor del texto.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Expresión de geometría que se utilizará para transformar las geometrías antes de pasarlas al motor de etiquetado.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Especifica el comportamiento de renderizado para geometrías multipartes.</p><p>- MultipartMode.All - coloca una etiqueta cerca de cada parte de la geometría.</p><p>- MultipartMode.Any - coloca una etiqueta cerca de cualquier parte de la geometría.</p><p>- MultipartMode.Largest - coloca una etiqueta cerca de la parte más grande de la geometría.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Especifica cómo se colocan las etiquetas en relación con la geometría.</p><p>- PointLabelPlacement - coloca la etiqueta cerca del centro de la geometría.</p><p>- LineLabelPlacement - coloca la etiqueta a lo largo de la geometría o su perímetro.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Especifica la prioridad de la etiqueta en caso de que se superponga con otra etiqueta.<br>La etiqueta con menor prioridad no se renderiza. El valor predeterminado es 1000.|

## **Ejemplos**
### **Ejemplos de Etiquetado de Puntos**
Por defecto, SimpleLabeling dibuja texto sobre los puntos:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
Aquí te mostramos cómo estilizar la fuente:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
Para controlar la posición del texto en relación con la entidad de punto, se debe establecer la propiedad placement:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
Para escenarios más avanzados, es posible que desees elegir diferentes etiquetados para las entidades. Así es como puedes hacerlo:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **Ejemplos de Etiquetado de Líneas**
Por defecto, SimpleLabeling dibuja la etiqueta cerca del centro de la línea:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
Para rotar las etiquetas de modo que sean paralelas a las líneas, se puede utilizar LineLabelPlacement con LineLabelAlignment.Parallel:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
Si deseas que los textos sigan la línea con precisión, se puede utilizar LineLabelPlacement con LineLabelAlignment.Curved:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
Si no deseas que los textos se superpongan con la línea, utiliza LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
Para escenarios más avanzados, es posible que desees ajustar el estilo de las etiquetas dinámicamente en función de los valores de los atributos de la entidad. Así es como puedes hacerlo:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
