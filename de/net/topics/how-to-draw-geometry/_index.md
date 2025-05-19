---
title: "So zeichnet man Geometrie auf einer Karte"
type: docs
url: /de/how-to-draw-geometry
weight: 70
---

Um geometrische Objekte auf einer Karte zu erstellen und anzuzeigen, müssen Sie zunächst **ein Geometrieobjekt erstellen**. Es gibt zwei Methoden, die Sie verwenden können:

- **Konstruktor für jeden Geometrietyp**
Diese Methode beinhaltet die Verwendung eines benutzerdefinierten Konstruktors für jeden Geometrietyp. Um beispielsweise einen Punkt zu erstellen, würden Sie den folgenden Code verwenden:

```
Point point = new Point(40.7128, -74.006);
```

Diese Methode kann jedoch herausfordernd und umständlich sein, wenn komplexe Objekte wie Polylinien oder Sammlungen erstellt werden. Infolgedessen muss der Entwickler möglicherweise viele Codezeilen hinzufügen, was die Lesbarkeit des Codes beeinträchtigt. Die Sicherstellung der Datenintegrität während der Initialisierung kann ebenfalls schwierig sein. Betrachten Sie beispielsweise das folgende Beispiel, das ein Polygon mit einem Loch im Inneren erstellt:

```
Polygon polygon = new Polygon();

LinearRing ring = new LinearRing();
ring.AddPoint(50.02, 36.22);
ring.AddPoint(49.99, 36.26);
ring.AddPoint(49.97, 36.23);
ring.AddPoint(49.98, 36.17);
ring.AddPoint(50.02, 36.22);

LinearRing hole = new LinearRing();
hole.AddPoint(50.00, 36.22);
hole.AddPoint(49.99, 36.20);
hole.AddPoint(49.98, 36.23);
hole.AddPoint(50.00, 36.24);
hole.AddPoint(50.00, 36.22);

polygon.ExteriorRing = ring;
polygon.AddInteriorRing(hole);
```

Ein weiterer Nachteil dieses Ansatzes ist der Mangel an Uniformität der Daten für die Initialisierung. Sie können kein Repository von Konstanten oder Dateien in Ihrem Projekt erstellen.

- **WKT (Well-Known Text)**
Diese Methode beinhaltet das Generieren von Geometrie aus WKT (Well-Known Text), was eine standardisierte Möglichkeit zur Erstellung von Geometrien bietet. Der folgende Code demonstriert, wie man einen Punkt und eine Linie erstellt:

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

Während dieser Ansatz die Leistung aufgrund der Notwendigkeit des Parsens der Zeichenkette leicht reduzieren kann, vereinfacht er die Erstellung komplexerer Objekte.

Weitere Details zu WKT finden Sie in folgendem Artikel: "Exportieren und Importieren von Daten aus/in WKT und WKB."

Anzeigen geometrischer Objekte auf der Karte
Sobald Sie ein Geometrieobjekt erstellt haben, besteht der nächste Schritt darin, es auf der Karte anzuzeigen. Während die Karte Layer anzeigen kann, die aus verschiedenen Quellen und Formaten geladen werden, ist der InMemoryLayer ein Layer, der keine Quelle benötigt.

**Um Ihr geometrisches Objekt anzuzeigen**, können Sie einen InMemoryLayer erstellen und das Objekt zu ihm hinzufügen:

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

Nun können Sie **diesen Layer auf der Karte anzeigen und eine Datei in einem der unterstützten Formate** wie SVG erstellen, mit folgendem Code:

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

Sobald Sie den Layer hinzugefügt und auf der Karte angezeigt haben, können Sie ihn in einem der unterstützten Formate speichern. In diesem Beispiel wird das SVG-Format gewählt, um potenzielle Probleme mit der Bitmap-Unterstützung zu vermeiden. Es ist wichtig anzumerken, dass Net 6.0 eine begrenzte Bitmap-Unterstützung hat, was zu Einschränkungen wie der Unfähigkeit führen kann, Bitmap-Bilder mithilfe von Blazor WebAsm auf der Client-Seite zu rendern. Daher ist bei der Auswahl eines Formats zum Speichern Ihrer Karte wichtig, die Einschränkungen der Zielplattform zu berücksichtigen und ein Format auszuwählen, das damit kompatibel ist.

Der Artikel erklärt, wie man geometrische Objekte mit einem Standard-, schlichten Stil auf einer Karte erstellt und anzeigt. Die Aspose-Bibliothek bietet jedoch eine breite Palette von Styling-Optionen, die an Ihre Bedürfnisse angepasst werden können. Um diese Optionen zu erkunden, empfehlen wir Ihnen, die [Aspose.MapRendering Dokumentation]( https://docs.aspose.com/gis/net/map-rendering/) zu konsultieren, die detaillierte Informationen darüber enthält, wie man verschiedene Styling-Techniken verwendet, um das visuelle Erscheinungsbild Ihrer Karte zu verbessern.

**Zusammenfassend lässt sich sagen**, dass Sie zur Erstellung geometrischer Objekte auf einer Karte entweder einen Konstruktor für jeden Geometrietyp verwenden oder Geometrie aus WKT generieren können. Um das Objekt anzuzeigen, platzieren Sie es auf einem Layer und zeigen den Layer mit Standard-Kartenstyling auf einer Karte an. Speichern Sie die Karte in einem unterstützten Format wie SVG und nutzen Sie unsere Bibliothek, um Styling-Optionen zu erkunden. Darüber hinaus bietet unsere Bibliothek die Möglichkeit, ein fertiges Beispiel zu sehen, indem Sie auf den [Link]( https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer) in der Dokumentation klicken, was Ihnen helfen kann, diese Techniken in Ihren eigenen Projekten zu implementieren.
