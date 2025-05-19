---
title: "Symboliseur en couches"
type: docs
url: /fr/net/layered-symbolizer/
weight: 40
description: Le symboliseur en couches dans l'API de la bibliothèque C# GIS dessine un élément avec plusieurs symboliseurs superposés avec des modes d'ordre de rendu basés sur les éléments ou les couches.
---

## **Symboliseur en couches**
Le symboliseur en couches dessine un élément avec plusieurs symboliseurs superposés. Vous pouvez choisir parmi deux modes d'ordre de rendu :

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - dessiner le premier élément avec tous les symboliseurs ajoutés au symboliseur en couches, puis passer au dessin de l'élément suivant.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - dessiner tous les éléments avec le premier symboliseur, puis dessiner tous les éléments avec le symboliseur suivant.

### **Rendu par éléments**

### **Rendu par couches**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
