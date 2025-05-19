---
title: "Simbolizador em Camadas"
type: docs
url: /pt/net/layered-symbolizer/
weight: 40
description: O simbolizador em camadas na API da biblioteca GIS C# desenha um elemento com vários simbolizadores um sobre o outro, com modos de ordem de renderização baseados em elementos ou camadas.
---

## **Simbolizador em Camadas**
O simbolizador em camadas desenha um elemento com vários simbolizadores um sobre o outro. Você pode selecionar dois modos de ordem de renderização:

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - desenhe o primeiro elemento com todos os simbolizadores adicionados ao simbolizador em camadas, então prossiga com o desenho do próximo elemento.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - desenhe todos os elementos com o primeiro simbolizador, então desenhe todos os elementos com o próximo simbolizador.

### **Renderização por Elementos**

### **Renderização por Camadas**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
