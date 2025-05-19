---
title: "Linien-Symbolisierer"
type: docs
url: /de/net/line-symbolizer/
weight: 20
description: GIS C#-Bibliothek oder API unterstützt einen einfachen Linien-Symbolisierer für eindimensionale Geometrien, Linien und kann auf Geometrien jeglichen Typs wie Punkt, Linie, Fläche angewendet werden.
---

## **Linien-Symbolisierer**
Der einfache Linien-Symbolisierer zeichnet eine Linie mit anpassbarem Stil. Dies ist der Standardsymbolisierer für eindimensionale Geometrien (Linien). 

Unterstützte Styling-Optionen:

|**Eigenschaft**|**Beschreibung**|
| :- | :- |
|[Farbe](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|Gibt die Farbe und Transparenz der Linie an.|
|[Breite](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|Gibt die Breite der Linie an|
|[Linienverbindung](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|Bestimmt, wie Linien an den Schnittpunkten von Liniensegmenten gerendert werden.|
|[Stil](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|Gibt an, wie die Symbollinien gezeichnet werden sollen.|
|[Strichmuster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|Gibt ein Array von Abständen an, das die Längen abwechselnder Striche und Leerstellen in gestrichelten Linien angibt.|
|[Strichversatz](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|Gibt den Abstand vom Beginn einer Linie zum Beginn eines Strichmusters an.|
|[Kappenstil](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>Gibt an, wie Linien an ihren Enden gerendert werden.</p><p>- Stumpf - scharfe quadratische Kante</p><p>- Rund - abgerundete Kante</p><p>- Quadratisch - leicht verlängerte quadratische Kante</p>|
|[Versatz](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|Gibt einen Versatz von der ursprünglichen Linie an. Für eine positive Distanz befindet sich der Versatz auf der linken Seite der Eingabelinie (bezogen auf die Linienrichtung). Bei einer negativen Distanz befindet er sich auf der rechten Seite.|

### **Geometrietypen**
` `Der Symbolisierer kann auf Geometrien jeglichen Typs angewendet werden.

|**Geometriedimension**|**Geometrietypen**|**Rendering-Verhalten**|
| :-: | :-: | :-: |
|**Punkt**|Punkt, MultiPoint|Zeichnet eine Linie von geringer Länge mit horizontaler Ausrichtung zentriert auf dem Punkt mit zwei Endkappen.|
|**Linie**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Zeichnet die Linie.|
|**Fläche**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Die geschlossene Umrandung der Geometrie wird als Linienstring verwendet (ohne Endkappen)|

Für GeometryCollections wird das Rendering-Verhalten für jede Geometrie innerhalb der Collection separat bestimmt. Layer mit gemischten Geometrietypen folgen der Logik für GeometryCollections.

Verwenden Sie MixedGeometrySymbolizer, um einen Symbolisierer auf bestimmte Geometrietypen zu beschränken.

### **Beispiele**
Standardmäßig zeichnet der Linien-Symbolisierer schwarze Linien:



Hier erfahren Sie, wie Sie die Linienfarbe auf Blau ändern:




|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

Für fortgeschrittenere Szenarien möchten Sie den Linienstil möglicherweise dynamisch basierend auf Feature-Attributwerten anpassen. So geht's:




|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |




Sie möchten möglicherweise auch Beschriftungen zu Ihren Linien hinzufügen. Besuchen Sie [Beispiele für die Beschriftung von Linien](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) für Beispiele.
