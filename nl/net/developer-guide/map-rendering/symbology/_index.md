---
title: Symboliek - C# GIS API
linktitle: "Symboliek"
type: docs
url: /nl/symbology/
weight: 10
description: GIS C# Bibliotheek of API ondersteunt symbolizers om feature geometrie te tekenen zoals Marker, Lijn, Vulling en het combineren van symbolizers om meer complexe visualisaties te creëren.
---

Een symbolizer is een manier om een feature geometrie op een kaart te tekenen.

|** **|**Symbolizer**|**API Class**|**Beschrijving**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**Marker**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Tekent een vooraf gedefinieerde vorm met aanpasbare vulling en omtrek. |
|![todo:image_alt_text](symbology_2.png)|**Lijn**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Tekent een lijn met aanpasbare styling.|
|![todo:image_alt_text](symbology_3.png)|**Vulling**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Vult een polygoon of gebied begrensd door een lijn met aanpasbare vulling en rand.|
Naast de symbolizers die daadwerkelijk tekenen, is er een aantal andere symbolizers dat het mogelijk maakt om symbolizers te combineren om meer complexe visualisaties te creëren.

|**Symbolizer**|**API Class**|**Beschrijving**|
| :- | :- | :- |
|**Gelaagde Symbolizer**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Tekent een feature met meerdere symbolizers boven elkaar|
|**Gemengde Geometrie Symbolizer**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Tekent features uit lagen die geometrieën van gemengde types bevatten met een specifieke symbolizer voor elk geometrietype|
|**Op Regels Gebaseerde Symbolizer**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Selecteert een symbolizer om toe te passen op een feature door regels die door de gebruiker zijn gespecificeerd.|
|**Marker Cluster Symbolizer**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|Tekent clustering van markers, groepering van deze items.|
|**Geometrie Generator Symbolizer**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Maakt het mogelijk om de feature geometrie te vervangen voordat deze wordt weergegeven.|
|**Null Symbolizer**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|Tekent niets. Nuttig in combinatie met andere symbolizers, zoals de op regels gebaseerde symbolizer.|
