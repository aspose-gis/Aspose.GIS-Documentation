---
title: "Warstwowy Symbolizator"
type: docs
url: /pl/net/layered-symbolizer/
weight: 40
description: Warstwowy symbolizator w bibliotece GIS C# API rysuje obiekt z kilkoma symbolizatorami na sobie, z trybami kolejności renderowania opartymi na obiektach lub warstwach.
---

## **Warstwowy Symbolizator**
Warstwowy symbolizator rysuje obiekt za pomocą kilku symbolizatorów na sobie. Możesz wybrać spośród dwóch trybów kolejności renderowania:

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - rysuj pierwszy obiekt wszystkimi symbolizatorami dodanymi do warstwowego symbolizatora, a następnie przejdź do rysowania następnego obiektu.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - rysuj wszystkie obiekty z pierwszym symbolem, a następnie rysuj wszystkie obiekty z następnym symbolem.

### **Renderowanie według Obiektów**

### **Renderowanie według Warstw**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
