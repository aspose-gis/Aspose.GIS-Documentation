---
title: "Layered Symbolizer"
type: docs
url: /de/net/layered-symbolizer/
weight: 40
description: Der Layered Symbolizer in der GIS C# Library API zeichnet ein Feature mit mehreren Symbolizern übereinander, wobei die Rendering-Reihenfolgenmodi auf Features oder Layern basieren.
---

## **Layered Symbolizer**
Der Layered Symbolizer zeichnet ein Feature mit mehreren Symbolizern übereinander. Sie können zwischen zwei Rendering-Reihenfolgenmodi wählen:

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - Zeichnen Sie das erste Feature mit allen Symbolizern, die dem Layered Symbolizer hinzugefügt wurden, und gehen Sie dann zum Zeichnen des nächsten Features über.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - Zeichnen Sie alle Features mit dem ersten Symbolizer, zeichnen Sie dann alle Features mit dem nächsten Symbolizer.

### **Rendering nach Features**

### **Rendering nach Layern**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
