---
title: "Simbolizador de Linha"
type: docs
url: /pt/net/line-symbolizer/
weight: 20
description: Biblioteca ou API GIS C# suporta o simbolizador de linha simples para geometrias unidimensionais linhas e pode ser aplicado em geometrias de qualquer tipo como Ponto, Linha, Superfície.
---

## **Simbolizador de Linha**
O simbolizador de linha simples desenha uma linha com estilo personalizável. Este é o simbolizador padrão para geometrias unidimensionais (linhas). 

Opções de estilo suportadas:

|**Propriedade**|**Descrição**|
| :- | :- |
|[Color](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|Especifica a cor e a transparência dadas à linha.|
|[Width](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|Especifica a largura da linha|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|Determina como as linhas são renderizadas em interseções de segmentos de linha.|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|Especifica como o trabalho de linha do símbolo deve ser desenhado.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|Especifica uma matriz de distâncias que especifica os comprimentos de traços e espaços alternados em linhas tracejadas.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|Especifica a distância do início de uma linha para o início de um padrão de traço.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>Especifica como as linhas são renderizadas em suas extremidades.</p><p>- Butt - borda quadrada nítida</p><p>- Round - borda arredondada</p><p>- Square - borda quadrada ligeiramente alongada</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|Especifica o deslocamento da linha original. Para distância positiva, o deslocamento estará no lado esquerdo da linha de entrada (em relação à direção da linha). Para uma distância negativa, estará no lado direito.|

### **Tipos de Geometria**
` `O simbolizador pode ser aplicado a geometrias de qualquer tipo.

|**Dimensão da Geometria**|**Tipos de Geometria**|**Comportamento de Renderização**|
| :-: | :-: | :-: |
|**Ponto**|Ponto, MultiPoint|Desenha uma linha de pequeno comprimento com orientação horizontal centrada no ponto, com duas tampas finais.|
|**Linha**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Desenha a linha.|
|**Superfície**|Polígono, CurvePolygon, MultiPolygon, MultiSurface|O contorno fechado da geometria é usado como a string de linha (sem tampas finais)|

Para GeometryCollections, o comportamento de renderização é determinado separadamente para cada geometria dentro da coleção. Camadas com tipo de geometria Misto seguem a lógica para GeometryCollections.

Use MixedGeometrySymbolizer para limitar um simbolizador a tipos de geometria específicos.

### **Exemplos**
Por padrão, o simbolizador de linha desenha linhas pretas:




Aqui está como alterar a cor da linha para azul:



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

Para cenários mais avançados, você pode querer ajustar o estilo da linha dinamicamente com base nos valores dos atributos do recurso. Veja como fazer isso:



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |



Você também pode querer adicionar rótulos às suas linhas. Visite [Exemplos de Rotulagem de Linhas](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) para exemplos.
