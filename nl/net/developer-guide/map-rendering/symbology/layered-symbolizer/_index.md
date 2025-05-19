---
title: "Gelaagde Symbolizer"
type: docs
url: /nl/net/layered-symbolizer/
weight: 40
description: Gelaagde symbolizer in GIS C# Library API tekent een feature met meerdere symbolizers boven elkaar met rendering ordermodi op basis van features of lagen.
---

## **Gelaagde Symbolizer**
De gelaagde symbolizer tekent een feature met meerdere symbolizers boven elkaar. U kunt kiezen uit twee rendering ordermodi:

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - teken de eerste feature met alle symbolizers toegevoegd aan de gelaagde symbolizer, ga dan verder met het tekenen van de volgende feature.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - teken alle features met de eerste symbolizer, teken vervolgens alle features met de volgende symbolizer.

### **Rendering per Features**

### **Rendering per Lagen**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
