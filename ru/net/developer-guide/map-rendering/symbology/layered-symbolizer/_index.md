---
title: "Слоистый Символизатор"
type: docs
url: /ru/net/layered-symbolizer/
weight: 40
description: Слоистый символизатор в GIS C# Library API рисует объект с несколькими символизаторами друг на друге с режимами порядка рендеринга, основанными на объектах или слоях.
---

## **Слоистый Символизатор**
Слоистый символизатор рисует объект с несколькими символизаторами друг на друге. Вы можете выбрать один из двух режимов порядка рендеринга:

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - рисует первый объект со всеми символизаторами, добавленными в слоистый символизатор, затем переходит к рисованию следующего объекта.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - рисует все объекты с первым символизатором, затем рисует все объекты со следующим символизатором.

### **Рендеринг по Объектам**

### **Рендеринг по Слоям**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
