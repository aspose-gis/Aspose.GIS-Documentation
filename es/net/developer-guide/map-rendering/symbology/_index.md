---
title: Simbología - API de GIS C#
linktitle: "Simbología"
type: docs
url: /es/symbology/
weight: 10
description: La biblioteca o API de C# GIS admite simbolizadores para dibujar la geometría de entidades como Marcador, Línea, Relleno y combinar simbolizadores para crear visualizaciones más complejas.
---

Un simbolizador es una forma de dibujar la geometría de una entidad en un mapa.

|** **|**Simbolizador**|**Clase API**|**Descripción**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**Marcador**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Dibuja una forma predefinida con relleno y contorno personalizables.|
|![todo:image_alt_text](symbology_2.png)|**Línea**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Dibuja una línea con un estilo personalizable.|
|![todo:image_alt_text](symbology_3.png)|**Relleno**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Rellena un polígono o área delimitada por una línea con relleno y trazo personalizables.|
Además de los simbolizadores que realizan el dibujo real, existe un número de otros simbolizadores que permiten combinar otros simbolizadores para crear visualizaciones más complejas.

|**Simbolizador**|**Clase API**|**Descripción**|
| :- | :- | :- |
|**Simbolizador en capas**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Dibuja una entidad con varios simbolizadores uno encima del otro|
|**Simbolizador de geometría mixta**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Dibuja entidades de capas que contienen geometrías de tipos mixtos con un simbolizador específico para cada tipo de geometría|
|**Simbolizador basado en reglas**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Selecciona un simbolizador que se aplicará a una entidad por reglas especificadas por el usuario.|
|**Simbolizador de clúster de marcadores**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|Dibuja agrupaciones de marcadores, agrupación de estos elementos.|
|**Simbolizador generador de geometría**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Permite sustituir la geometría de la entidad antes de renderizarla.|
|**Simbolizador nulo**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|No dibuja nada. Útil cuando se combina con otros simbolizadores, como el simbolizador basado en reglas.|
