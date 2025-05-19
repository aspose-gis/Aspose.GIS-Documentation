---
title: "Marker Symbolizer"
type: docs
url: /de/net/marker-symbolizer/
weight: 10
description: GIS C# Bibliothek oder API unterstützt Simple Marker Symbolizer, der eine vordefinierte Form mit anpassbarer Füllung und Umrandung auf Geometrien jeglichen Typs wie Punkt, Linie, Fläche zeichnet.
---

## **Marker Symbolizer**
Der Simple Marker Symbolizer zeichnet eine vordefinierte Form mit anpassbarer Füllung und Umrandung. Dies ist der Standardsymbolisierer für 0-dimensionale Geometrien (Punkte). 

Unterstützte Formen sind:

|![todo:image_alt_text](marker-symbolizer_1.png)|Kreis| |![todo:image_alt_text](marker-symbolizer_2.png)|Stern|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Quadrat| |![todo:image_alt_text](marker-symbolizer_4.png)|Kreuz|
|![todo:image_alt_text](marker-symbolizer_5.png)|Dreieck| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

Unterstützte Styling-Optionen:

|**Eigenschaft**|**Beschreibung**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|Gibt die Form des Markers an.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|Gibt die Größe der Markerform an|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|Gibt die Farbe und Transparenz für die Füllung an|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|Gibt die Farbe und Transparenz für die Linie an|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|Gibt die Breite der Linie an|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|Bestimmt, wie Linien an Schnittpunkten von Liniensegmenten gerendert werden.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|Gibt an, wie die Symbollinien gezeichnet werden sollen.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|Gibt ein Array von Abständen an, das die Längen abwechselnder Striche und Leerstellen in gestrichelten Linien angibt.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|Gibt den Abstand vom Beginn einer Linie zum Beginn eines Strichmusters an.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|Gibt die Drehung des Symbols um seinen Mittelpunkt in Dezimalgraden an. Positive Werte geben eine Drehung im Uhrzeigersinn an, negative Werte eine Drehung gegen den Uhrzeigersinn. Standardmäßig ist 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|Gibt einen horizontalen Versatz von einem Punkt zum Formankerpunkt an.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|Gibt einen vertikalen Versatz von einem Punkt zum Formankerpunkt an.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|Gibt an, welche Seite einer Markerform horizontal mit dem Punkt übereinstimmt.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|Gibt an, welche Seite einer Markerform vertikal mit dem Punkt übereinstimmt.|

### **Geometrie Typen**
` `Der Symbolisierer kann auf Geometrien jeglichen Typs angewendet werden.

|**Geometrie Dimension**|**Geometrie Typen**|**Rendering Verhalten**|
| :-: | :-: | :-: |
|**Punkt**|Punkt, MultiPoint|Zeichnet die Form zentriert an der Punktkoordinate.|
|**Linie**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>Zeichnet die Form zentriert am Schwerpunkt der Geometrie</p><p> </p>|
|**Fläche**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

Für GeometryCollections wird das Rendering-Verhalten separat für jede Geometrie innerhalb der Collection bestimmt. Layer mit gemischtem Geometrietyp folgen der Logik für GeometryCollections.

Verwenden Sie MixedGeometrySymbolizer, um einen Symbolisierer auf bestimmte Geometrietypen zu beschränken.

### **Beispiele**
Standardmäßig zeichnet der Marker-Symbolisierer schwarze Kreise:



Hier erfahren Sie, wie Sie die Füllfarbe auf Rot ändern:




|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

Ein weiteres Beispiel für das Styling mit einer vordefinierten Form (Dreieck):




|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----
Für fortgeschrittenere Szenarien möchten Sie den Markerstil möglicherweise dynamisch basierend auf Feature-Attributwerten anpassen. So geht's:




|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
Möglicherweise möchten Sie auch Beschriftungen zu Ihren Markern hinzufügen. Besuchen Sie [Beispiele für die Kennzeichnung von Punkten](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) für Beispiele.
