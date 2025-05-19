---
title: "Vrstvený Symbolizér"
type: docs
url: /cs/net/layered-symbolizer/
weight: 40
description: Vrstvený symbolizér v GIS C# Library API vykresluje entitu s několika symbolizéry nad sebou s režimy pořadí vykreslování založenými na entitách nebo vrstvách.
---

## **Vrstvený Symbolizér**
Vrstvený symbolizér vykresluje entitu s několika symbolizéry nad sebou. Můžete si vybrat ze dvou režimů pořadí vykreslování:

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - nakreslete první entitu se všemi symbolizéry přidanými do vrstveného symbolizéru, poté pokračujte s kreslením další entity.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - nakreslete všechny entity s prvním symbolizérem, poté nakreslete všechny entity s dalším symbolizérem.

### **Vykreslování podle Entit**

### **Vykreslování podle Vrstev**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
