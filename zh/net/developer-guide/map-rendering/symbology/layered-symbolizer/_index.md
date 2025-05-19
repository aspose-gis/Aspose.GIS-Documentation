---
title: "分层符号化器"
type: docs
url: /zh/net/layered-symbolizer/
weight: 40
description: GIS C# Library API 中的分层符号化器使用基于要素或图层的渲染顺序模式，在彼此之上绘制具有多个符号化器的要素。
---

## **分层符号化器**
分层符号化器在彼此之上绘制具有多个符号化器的要素。您可以选择两种渲染顺序模式：

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - 使用添加到分层符号化器的所有符号化器绘制第一个要素，然后继续绘制下一个要素。
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - 使用第一个符号化器绘制所有要素，然后使用下一个符号化器绘制所有要素。

### **按要素渲染**

### **按图层渲染**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
