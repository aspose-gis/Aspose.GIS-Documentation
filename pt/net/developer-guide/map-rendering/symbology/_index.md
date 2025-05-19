---
title: Simbologia - API GIS C#
linktitle: "Simbologia"
type: docs
url: /pt/symbology/
weight: 10
description: Biblioteca ou API GIS C# suporta simbolizadores para desenhar a geometria de feições como Marcador, Linha, Preenchimento e combinar simbolizadores para criar visualizações mais complexas.
---

Um simbolizador é uma forma de desenhar a geometria de uma feição em um mapa.

|** **|**Simbolizador**|**Classe API**|**Descrição**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**Marcador**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Desenha uma forma predefinida com preenchimento e contorno personalizáveis. |
|![todo:image_alt_text](symbology_2.png)|**Linha**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Desenha uma linha com estilo personalizável.|
|![todo:image_alt_text](symbology_3.png)|**Preenchimento**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Preenche um polígono ou área delimitada por uma linha com preenchimento e traço personalizáveis.|
Além dos simbolizadores que realizam o desenho real, existe um número de outros simbolizadores que permitem combinar outros simbolizadores para criar visualizações mais complexas.

|**Simbolizador**|**Classe API**|**Descrição**|
| :- | :- | :- |
|**Simbolizador em Camadas**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Desenha uma feição com vários simbolizadores um sobre o outro|
|**Simbolizador de Geometria Mista**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Desenha feições de camadas que contêm geometrias de tipos mistos com um simbolizador específico para cada tipo de geometria|
|**Simbolizador Baseado em Regras**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Seleciona um simbolizador a ser aplicado a uma feição por regras especificadas pelo usuário.|
|**Simbolizador de Cluster de Marcadores**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|Desenha o agrupamento de marcadores, agrupamento desses itens.|
|**Simbolizador Gerador de Geometria**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Permite substituir a geometria da feição antes da renderização.|
|**Simbolizador Nulo**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|Não desenha nada. Útil quando combinado com outros simbolizadores, como o simbolizador baseado em regras.|
