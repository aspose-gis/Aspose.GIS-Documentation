---
title: "階層シンボライザー"
type: docs
url: /ja/net/layered-symbolizer/
weight: 40
description: GIS C# Library API の階層シンボライザーは、フィーチャを複数のシンボライザーを重ねて描画し、フィーチャまたはレイヤーに基づいてレンダリング順序モードを使用します。
---

## **階層シンボライザー**
階層シンボライザーは、複数のシンボライザーを重ねてフィーチャを描画します。次の 2 つのレンダリング順序モードから選択できます。

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - レイヤーシンボライザーに追加されたすべてのシンボライザーで最初のフィーチャを描画し、次に次のフィーチャの描画に進みます。
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - 最初のシンボライザーですべてのフィーチャを描画してから、次のシンボライザーですべてのフィーチャを描画します。

### **フィーチャによるレンダリング**

### **レイヤーによるレンダリング**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
