---
title: "Simbolizzatore a livelli"
type: docs
url: /it/net/layered-symbolizer/
weight: 40
description: Il simbolizzatore a livelli nella libreria API GIS C# disegna una entità con diversi simbolizzatori uno sopra l'altro con modalità di ordine di rendering basate su entità o livelli.
---

## **Simbolizzatore a livelli**
Il simbolizzatore a livelli disegna un elemento geografico con diversi simbolizzatori sovrapposti. Puoi scegliere tra due modalità di ordine di rendering:

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - disegna la prima entità con tutti i simbolizzatori aggiunti al simbolizzatore a livelli, quindi procedi con il disegno dell'entità successiva.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - disegna tutte le entità con il primo simbolizzatore, quindi disegna tutte le entità con il simbolo successivo.

### **Rendering per Entità**

### **Rendering per Livelli**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
