---
title: "Layered Symbolizer"
type: docs
url: /net/layered-symbolizer/
weight: 40
description: Layered symbolizer in GIS C# Library API draws a feature with several symbolizers on top of each other with rendering order modes based on features or layers.
---

## **Layered Symbolizer**
The Layered symbolizer draws a feature with several symbolizers on top of each other. You can select from two rendering order modes:

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - draw the first feature with all symbolizers added to the layered symbolizer, then proceed with drawing the next feature.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - draw all features with the first symbolizer, then draw all features with the next symbolizer.
### **Rendering by Features**

### **Rendering by Layers**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |

