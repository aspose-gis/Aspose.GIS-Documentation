---
title: Symbology - C# GIS API
linktitle: "Symbology"
type: docs
url: /net/symbology/
weight: 10
description: GIS C# Library or API supports symbolizers to draw feature geometry like Marker, Line, Fill and combining symbolizers to create more complex visualizations.
---

A symbolizer is a way to draw a feature geometry on a map. 

|** |**Symbolizer**|**API Class**|**Description**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**Marker**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Draws a predefined shape with customizable fill and outline. |
|![todo:image_alt_text](symbology_2.png)|**Line**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Draws a line with customizable styling.|
|![todo:image_alt_text](symbology_3.png)|**Fill**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Fills a polygon or area bounded by a line with customizable fill and stroke.|
In addition to the symbolizers that do actual drawing, there is a number of other symbolizers that allow combining other symbolizers to create more complex visualizations.

|**Symbolizer**|**API Class**|**Description**|
| :- | :- | :- |
|**Layered Symbolizer**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Draws a feature with several symbolizers on top of each other|
|**Mixed Geometry Symbolizer**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Draws features from layers that contain geometries of mixed types with a specific symbolizer for each geometry type|
|**Rule-Based Symbolizer**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Selects a symbolizer to apply to a feature by rules specified by the user.|
|**Marker Cluster Symbolizer**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|Draws clustering of markers, grouping of these items.|
|**Geometry Generator Symbolizer**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Allow to substitute the feature geometry before rendering.|
|**Null Symbolizer**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|Doesn't draw anything. Useful when combined with other symbolizers, such as the rule-based symbolizer.|

