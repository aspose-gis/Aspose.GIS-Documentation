---
title: Symbolisation - API GIS C#
linktitle: "Symbolisation"
type: docs
url: /fr/symbology/
weight: 10
description: La bibliothèque ou l'API GIS C# prend en charge les symboliseurs pour dessiner la géométrie des entités telles que Marqueur, Ligne, Remplissage et combiner les symboliseurs pour créer des visualisations plus complexes.
---

Un symboliseur est une manière de dessiner la géométrie d’une entité sur une carte.

|** **|**Symboliseur**|**Classe API**|**Description**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**Marqueur**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Dessine une forme prédéfinie avec un remplissage et un contour personnalisables.|
|![todo:image_alt_text](symbology_2.png)|**Ligne**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Dessine une ligne avec un style personnalisable.|
|![todo:image_alt_text](symbology_3.png)|**Remplissage**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Remplit un polygone ou une zone délimitée par une ligne avec un remplissage et un contour personnalisables.|
En plus des symboliseurs qui effectuent le dessin réel, il existe un certain nombre d'autres symboliseurs qui permettent de combiner d'autres symboliseurs pour créer des visualisations plus complexes.

|**Symboliseur**|**Classe API**|**Description**|
| :- | :- | :- |
|**Symboliseur en couches**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Dessine une entité avec plusieurs symboliseurs superposés|
|**Symboliseur de géométrie mixte**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Dessine des entités à partir de couches qui contiennent des géométries de types mixtes avec un symboliseur spécifique pour chaque type de géométrie|
|**Symboliseur basé sur des règles**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Sélectionne un symboliseur à appliquer à une entité par des règles spécifiées par l'utilisateur.|
|**Symboliseur de cluster de marqueurs**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|Dessine le regroupement de marqueurs, le groupement de ces éléments.|
|**Symboliseur de générateur de géométrie**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Permet de substituer la géométrie de l'entité avant le rendu.|
|**Symboliseur nul**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|Ne dessine rien. Utile lorsqu'il est combiné à d'autres symboliseurs, tels que le symboliseur basé sur des règles.|
