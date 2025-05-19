---
title: "Simbolizador de Preenchimento"
type: docs
url: /pt/net/fill-symbolizer/
weight: 30
description: A biblioteca GIS C# API suporta o simbolizador de preenchimento simples para preencher estilo e traço para geometrias bidimensionais polígonos de qualquer tipo, como Ponto, Linha, Superfície.
---

## **Simbolizador de Preenchimento**
O simbolizador de preenchimento simples preenche uma área com um estilo de preenchimento e traço personalizáveis. Este é o simbolizador padrão para geometrias bidimensionais (polígonos). 

Se um polígono tem “buracos”, eles não são preenchidos, mas as bordas ao redor dos buracos são tracejadas da maneira usual. “Ilhas” dentro de buracos são preenchidas e tracejadas, e assim por diante.

Opções de estilo suportadas:

|**Propriedade**|**Descrição**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Especifica a cor e a transparência dadas ao preenchimento.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Sólido - Preenchimento sólido</p><p>- Nenhum - Não preencher o polígono</p><p>- Hachura Horizontal - Um padrão de linhas horizontais.</p><p>- Hachura Vertical - Um padrão de linhas verticais.</p><p>- Hachura Cruzada - Especifica linhas horizontais e verticais que se cruzam.</p><p>- Hachura Diagonal para Frente - Um padrão de linhas em uma diagonal da esquerda superior para a direita inferior.</p><p>- Hachura Diagonal para Trás - Um padrão de linhas em uma diagonal da direita superior para a esquerda inferior.</p><p>- Hachura Cruzada Diagonal - Um padrão de linhas diagonais cruzadas.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Especifica a cor e a transparência dadas à linha do traço.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Especifica como o trabalho de linha do símbolo deve ser desenhado.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Especifica a largura da linha do traço.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Especifica uma matriz de distâncias que especifica os comprimentos de traços e espaços alternados em linhas tracejadas.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Especifica a distância do início de uma linha para o início de um padrão de traço.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Determina como as linhas são renderizadas em interseções de segmentos de linha.</p><p>- Miter - canto afiado</p><p>- Round - canto arredondado</p><p>- Bevel - canto diagonal</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Especifica o deslocamento horizontal de um ponto de localização para o ponto de âncora da forma.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Especifica o deslocamento vertical de um ponto de localização para o ponto de âncora da forma.|

### **Tipos de Geometria**
` `O simbolizador pode ser aplicado a geometrias de qualquer tipo.

|**Dimensão da Geometria**|**Tipos de Geometria**|**Comportamento de Renderização**|
| :-: | :-: | :-: |
|**Ponto**|Ponto, MultiPoint|Desenha um pequeno quadrado ortogonal polígono.|
|**Linha**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|A linha é fechada para preenchimento conectando seu ponto final ao seu ponto inicial. Apenas a linha original é tracejada.|
|**Superfície**|Polígono, CurvePolygon, MultiPolygon, MultiSurface|Desenha o polígono.|

Para GeometryCollections, o comportamento de renderização é determinado separadamente para cada geometria dentro da coleção. Camadas com tipo de geometria Misto seguem a lógica para GeometryCollections.

Use MixedGeometrySymbolizer para limitar um simbolizador a tipos de geometria específicos.

### **Exemplos**
Por padrão, o Simple Fill symbolizer desenha uma linha de traço preta e preenchimento branco sólido:



Aqui está como alterar o estilo:



|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

Você também pode querer adicionar rótulos aos seus polígonos. Visite [Exemplos de Rotulagem de Linhas](/gis/pt/simple-labeling/#simplelabeling-lineslabelingexamples) para exemplos de como rotular a borda do polígono ou [Exemplos de Rotulagem de Pontos](/gis/pt/simple-labeling/#simplelabeling-pointslabelingexamples) sobre exmaplos de como rotular os centros dos polígonos.
