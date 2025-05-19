---
title: "Багатошаровий Символізатор"
type: docs
url: /uk/net/layered-symbolizer/
weight: 40
description: Багатошаровий символізатор у GIS C# Library API малює об'єкт з кількома символізаторами один на одного з режимами порядку рендерингу на основі об'єктів або шарів.
---

## **Багатошаровий Символізатор**
Багатошаровий символізатор малює об'єкт з кількома символізаторами один на одного. Ви можете вибрати між двома режимами порядку рендерингу:

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - малює перший об'єкт з усіма символізаторами, доданими до багатошарового символізатора, а потім переходить до малювання наступного об'єкта.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - малює всі об'єкти з першим символізатором, а потім малює всі об'єкти з наступним символізатором.
### **Рендеринг за Об'єктами**

### **Рендеринг за Шарами**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
