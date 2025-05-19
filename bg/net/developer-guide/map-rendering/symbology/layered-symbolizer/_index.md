---
title: "Слоевиден Символизатор"
type: docs
url: /bg/net/layered-symbolizer/
weight: 40
description: Слоевият символизатор в GIS C# Library API рисува елемент с няколко символизатора един върху друг с режими на подредба при рендиране, базирани на елементи или слоеве.
---

## **Слоевиден Символизатор**
Слоевият символизатор рисува елемент с няколко символизатора един върху друг. Можете да избирате между два режима на подредба при рендиране:

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - рисува първия елемент с всички символизатори, добавени към слоевия символизатор, след което продължава с рисуването на следващия елемент.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - рисува всички елементи с първия символизатор, след това рисува всички елементи със следващия символизатор.

### **Рендиране по Елементи**

### **Рендиране по Слоеве**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
