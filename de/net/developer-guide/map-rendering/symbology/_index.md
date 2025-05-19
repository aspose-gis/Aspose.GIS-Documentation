---
title: Symbolik - C# GIS API
linktitle: "Symbolik"
type: docs
url: /de/symbology/
weight: 10
description: GIS C#-Bibliothek oder API unterstützt Symbolisierer zum Zeichnen von Feature-Geometrien wie Marker, Linie, Füllung und zur Kombination von Symbolisierern, um komplexere Visualisierungen zu erstellen.
---

Ein Symbolisierer ist eine Möglichkeit, eine Feature-Geometrie auf einer Karte zu zeichnen.

|** **|**Symbolisierer**|**API Klasse**|**Beschreibung**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**Marker**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Zeichnet eine vordefinierte Form mit anpassbarer Füllung und Umrandung.|
|![todo:image_alt_text](symbology_2.png)|**Linie**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Zeichnet eine Linie mit anpassbarer Formatierung.|
|![todo:image_alt_text](symbology_3.png)|**Füllung**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Füllt ein Polygon oder einen Bereich, der von einer Linie begrenzt wird, mit anpassbarer Füllung und Strich.|
Zusätzlich zu den Symbolisierern, die eigentliches Zeichnen durchführen, gibt es eine Reihe anderer Symbolisierer, die das Kombinieren anderer Symbolisierer ermöglichen, um komplexere Visualisierungen zu erstellen.

|**Symbolisierer**|**API Klasse**|**Beschreibung**|
| :- | :- | :- |
|**Layered Symbolizer**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Zeichnet ein Feature mit mehreren Symbolisierern übereinander.|
|**Mixed Geometry Symbolizer**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Zeichnet Features aus Layern, die Geometrien gemischter Typen enthalten, mit einem bestimmten Symbolisierer für jeden Geometrietyp.|
|**Rule-Based Symbolizer**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Wählt einen Symbolisierer aus, der auf ein Feature angewendet werden soll, anhand von Regeln, die vom Benutzer festgelegt wurden.|
|**Marker Cluster Symbolizer**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|Zeichnet Clustering von Markern, Gruppierung dieser Elemente.|
|**Geometry Generator Symbolizer**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Ermöglicht das Ersetzen der Feature-Geometrie vor dem Rendern.|
|**Null Symbolizer**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|Zeichnet nichts. Nützlich in Kombination mit anderen Symbolisierern, wie z. B. dem regelbasierten Symbolisierer.|
