---
title: "Simbolizador de Marcador"
type: docs
url: /pt/net/marker-symbolizer/
weight: 10
description: Biblioteca ou API GIS C# suporta o simbolizador de Marcador Simples que desenha uma forma predefinida com preenchimento e contorno personalizáveis em geometrias de qualquer tipo como Ponto, Linha, Superfície.
---

## **Simbolizador de Marcador**
O simbolizador de Marcador Simples desenha uma forma predefinida com preenchimento e contorno personalizáveis. Este é o simbolizador padrão para geometrias 0-dimensionais (pontos). 

As formas suportadas são:

|![todo:image_alt_text](marker-symbolizer_1.png)|Círculo| |![todo:image_alt_text](marker-symbolizer_2.png)|Estrela|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Quadrado| |![todo:image_alt_text](marker-symbolizer_4.png)|Cruz|
|![todo:image_alt_text](marker-symbolizer_5.png)|Triângulo| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

Opções de estilo suportadas:

|**Propriedade**|**Descrição**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|Especifica a forma do marcador.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|Especifica o tamanho da forma do marcador|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|Especifica a cor e a transparência dadas ao preenchimento|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|Especifica a cor e a transparência dadas à linha|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|Especifica a largura da linha|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|Determina como as linhas são renderizadas em interseções de segmentos de linha.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|Especifica como o trabalho de linha do símbolo deve ser desenhado.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|Especifica uma matriz de distâncias que especifica os comprimentos de traços e espaços alternados em linhas tracejadas.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|Especifica a distância do início de uma linha para o início de um padrão de traço.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|Especifica a rotação do símbolo em torno de seu ponto central, em graus decimais. Valores positivos indicam rotação no sentido horário, valores negativos indicam rotação anti-horária. O padrão é 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|Especifica o deslocamento horizontal de um local do ponto para o ponto de ancoragem da forma.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|Especifica o deslocamento vertical de um local do ponto para o ponto de ancoragem da forma.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|Especifica qual lado de uma forma de marcador será alinhado horizontalmente com a localização do ponto.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|Especifica qual lado de uma forma de marcador será alinhado verticalmente com a localização do ponto.|

### **Tipos de Geometria**
` `O simbolizador pode ser aplicado a geometrias de qualquer tipo.

|**Dimensão da Geometria**|**Tipos de Geometria**|**Comportamento de Renderização**|
| :-: | :-: | :-: |
|**Ponto**|Ponto, MultiPoint|Desenha a forma centrada na coordenada do ponto.|
|**Linha**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>Desenha a forma centrada no centróide da geometria</p><p> </p>|
|**Superfície**|Polígono, CurvePolygon, MultiPolygon, MultiSurface||

Para GeometryCollections, o comportamento de renderização é determinado separadamente para cada geometria dentro da coleção. Camadas com tipo de geometria Misto seguem a lógica para GeometryCollections.

Use MixedGeometrySymbolizer para limitar um simbolizador a tipos de geometria específicos.

### **Exemplos**
Por padrão, o simbolizador de marcador desenha círculos pretos:



Aqui está como alterar a cor de preenchimento para vermelho:



|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

Outro exemplo de estilo com uma forma predefinida (triângulo):



|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----
Para cenários mais avançados, você pode querer ajustar o estilo do marcador dinamicamente com base nos valores dos atributos de recurso. Veja como fazer isso:



|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
Você também pode querer adicionar rótulos aos seus marcadores. Visite [Exemplos de Rotulagem de Pontos](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) para exemplos.
