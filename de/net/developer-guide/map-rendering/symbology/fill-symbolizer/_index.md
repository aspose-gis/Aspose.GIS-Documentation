---
title: "Fill Symbolizer"
type: docs
url: /de/fill-symbolizer/
weight: 30
description: GIS C# Library API unterstützt Simple Fill Symbolizer zum Füllen von Stil und Strich für 2-dimensionale Geometrien, Polygonen aller Art wie Punkt, Linie, Oberfläche.
---

## **Fill Symbolizer**
Der Simple Fill Symbolizer füllt einen Bereich mit einem anpassbaren Füllstil und Strich. Dies ist der Standardsymbolisierer für 2-dimensionale Geometrien (Polygone). 

Wenn ein Polygon „Löcher“ hat, werden diese nicht gefüllt, aber die Ränder um die Löcher auf die übliche Weise gestrichen. „Inseln“ innerhalb von Löchern werden gefüllt und gestrichen usw.

Unterstützte Styling-Optionen:

|**Eigenschaft**|**Beschreibung**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Gibt die Farbe und Transparenz für die Füllung an.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - Volltonfüllung</p><p>- None - Polygon nicht füllen</p><p>- Horizontal Hatch - Ein Muster aus horizontalen Linien.</p><p>- Vertical Hatch - Ein Muster aus vertikalen Linien.</p><p>- Cross Hatch - Gibt horizontale und vertikale Linien an, die sich kreuzen.</p><p>- Forward Diagonal Hatch - Ein Muster aus Linien auf einer Diagonale von oben links nach unten rechts.</p><p>- Backward Diagonal Hatch - Ein Muster aus Linien auf einer Diagonale von oben rechts nach unten links.</p><p>- Diagonal Cross Hatch - Ein Muster aus sich kreuzenden diagonalen Linien.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Gibt die Farbe und Transparenz für die Strichlinie an.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Gibt an, wie das Symbol Linienwerk gezeichnet werden soll.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Gibt die Breite der Strichlinie an.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Gibt ein Array von Abständen an, das die Längen abwechselnder Striche und Leerstellen in gestrichelten Linien angibt.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Gibt den Abstand vom Beginn einer Linie zum Beginn eines Strichmusters an.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Bestimmt, wie Linien an Schnittpunkten von Liniensegmenten gerendert werden.</p><p>- Miter - scharfe Ecke</p><p>- Round - abgerundete Ecke</p><p>- Bevel - diagonale Ecke</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Gibt einen horizontalen Versatz von einem Punkt zum Formankerpunkt an.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Gibt einen vertikalen Versatz von einem Punkt zum Formankerpunkt an.|

### **Geometrie Typen**
` `Der Symbolisierer kann auf Geometrien aller Art angewendet werden.

|**Geometrie Dimension**|**Geometrie Typen**|**Rendering Verhalten**|
| :-: | :-: | :-: |
|**Punkt**|Punkt, MultiPoint|Zeichnet ein kleines quadratisches orthogonales Polygon.|
|**Linie**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Die Linie wird geschlossen, indem ihr Endpunkt mit ihrem Startpunkt verbunden wird. Nur die ursprüngliche Linie wird gestrichen.|
|**Oberfläche**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Zeichnet das Polygon.|

Für GeometryCollections wird das Rendering-Verhalten für jede Geometrie innerhalb der Collection separat bestimmt. Layer mit gemischtem Geometrietyp folgen der Logik für GeometryCollections.

Verwenden Sie MixedGeometrySymbolizer, um einen Symbolisierer auf bestimmte Geometrietypen zu beschränken.

### **Beispiele**
Standardmäßig zeichnet der Simple Fill Symbolizer eine schwarze Strichlinie und eine solide weiße Füllung:



Hier erfahren Sie, wie Sie das Styling ändern:




|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

Sie möchten möglicherweise auch Beschriftungen zu Ihren Polygonen hinzufügen. Besuchen Sie [Lines Labeling Examples](/gis/de/simple-labeling/#simplelabeling-lineslabelingexamples) für Beispiele, wie Sie Polygongrenzen beschriften oder [Points Labeling Examples](/gis/de/simple-labeling/#simplelabeling-pointslabelingexamples) auf exmaples, wie Sie Polygonzentren beschriften.
