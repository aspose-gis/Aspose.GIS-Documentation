---
title: "Simbolizador en capas"
type: docs
url: /es/net/layered-symbolizer/
weight: 40
description: El simbolizador en capas en la API de la biblioteca GIS C# dibuja una entidad con varios simbolizadores uno encima del otro con modos de orden de renderizado basados en entidades o capas.
---

## **Simbolizador en capas**
El simbolizador en capas dibuja una entidad con varios simbolizadores uno encima del otro. Puede seleccionar entre dos modos de orden de renderizado:

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - dibuje la primera entidad con todos los simbolizadores agregados al simbolizador en capas, luego continúe dibujando la siguiente entidad.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - dibuje todas las entidades con el primer simbolizador, luego dibuje todas las entidades con el siguiente simbolizador.

### **Renderizado por entidades**

### **Renderizado por capas**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
