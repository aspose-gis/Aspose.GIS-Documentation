---
title: "Optimaler Pfadfinder"
type: docs
url: /de/net/optimaler-pfadfinder
weight: 70
---

## Zusammenfassung

Die Suche nach dem kürzesten Weg in einem Straßennetz ist ein Analyseprozess, der darauf abzielt, den effizientesten Weg zwischen Punkten auf einer Karte zu bestimmen. Dieses Tool kann nützlich sein, um optimale Routen mit mehreren Stopps zu erstellen oder die Entfernung und Reisezeit zwischen verschiedenen Orten zu messen. Mit jedem Aufruf kann unsere Technologie optimale Routen für ein oder mehrere Fahrzeuge finden. Beispielsweise kann sie Fahrern helfen, die optimalen Routen für die Lieferung von Waren zu finden oder die optimale Pendelstrecke von zu Hause zur Arbeit für verschiedene Passagiere zu bestimmen.

## Algorithmusfähigkeiten

Unsere Bibliothek bietet die Möglichkeit, die **optimalste Route zwischen zwei Punkten** auf einer Karte zu erstellen. Sie verfügt über folgende Hauptfunktionen:

1. Suche nach dem optimalen Pfad auf der Karte unter Berücksichtigung von Wegen und Hindernissen: Wir berücksichtigen nicht nur Straßen, sondern auch Geländewege wie Wanderwege, Fußgängerwege und Hindernisse, die die Wahl des optimalen Pfades beeinflussen können.

2. Suche nach dem optimalen Pfad nur auf Straßen: Wenn Sie eine Route ausschließlich auf Straßen finden müssen, bieten wir diese Möglichkeit. Dies ist beispielsweise nützlich für Fahrzeuge, die sich nur auf Straßen bewegen dürfen.

3. Festlegen unterschiedlicher Geschwindigkeiten für Straßen: Wir haben die Fähigkeit, verschiedenen Straßen unterschiedliche Geschwindigkeiten zuzuweisen. Beispielsweise können höhere Geschwindigkeiten für Autobahnen und niedrigere Geschwindigkeiten für schmale Fahrspuren festgelegt werden.

4. Festlegen rechteckiger Hindernisse: Sie können rechteckige Hindernisse auf der Karte definieren, die beim Erstellen des optimalen Pfades berücksichtigt werden müssen. Dies ist nützlich, wenn es bekannte Hindernisse wie Gebäude oder Seen (deren Annäherung) gibt.

5. Begrenzung des Suchradius für Straßen: Sie können den Suchradius für Straßen einschränken, um die Suchzeit zu verkürzen und sich nur auf einen bestimmten Bereich zu konzentrieren.

6. Steuerung von Leistung und Genauigkeit: Wir bieten die Möglichkeit, die Leistung und Genauigkeit des Algorithmus zu steuern. Sie können ihn feinabstimmen, um das gewünschte Gleichgewicht zwischen Suchgeschwindigkeit und Routenkonstruktionsgenauigkeit zu erreichen.

Als Nächstes werden wir eine detailliertere Beschreibung jeder dieser Funktionen geben und Beispiele für ihre Anwendungen untersuchen.

## Ansatz zur Lösung

Obwohl die Pfadfindung eine nicht triviale Aufgabe ist, gibt es mehrere gute und zuverlässige Algorithmen, die in der Entwicklungsgemeinschaft anerkannt sind.

In unserer Implementierung haben wir einen modifizierten Lee-Algorithmus verwendet. Wir haben ein Gitter von Zellen auf der Ebene. Vom Startpunkt ausgehend breitet sich eine Welle in 8 Richtungen (einschließlich Diagonalen) zu benachbarten Zellen aus und berechnet die Zeit, die benötigt wird, um jede einzelne davon zu erreichen. Eine benachbarte Zelle kann ein Hindernis oder eine Straße enthalten. Straßen können unterschiedliche Geschwindigkeitskoeffizienten haben. So "markieren" wir unser Gitter mit der Zeit, die benötigt wird, um jede Zelle vom Startpunkt innerhalb eines bestimmten Radius oder bis zum Erreichen des Zielpunkts zu erreichen. Wenn wir den Zielpunkt erreichen, bauen wir einen umgekehrten Pfad unter Verwendung unseres Gitters.

Um die optimale Route im Straßennetz zu bestimmen, sind mehrere Schritte erforderlich. Zuerst müssen Sie die Straßen definieren und die Geschwindigkeit der Bewegung auf jeder einzelnen angeben. Sie sollten auch das Vorhandensein künstlicher und natürlicher Hindernisse berücksichtigen, die den Pfad beeinflussen können. Danach müssen Sie die Start- und Zielpunkte der Suche festlegen. Sobald diese vorbereitenden Schritte erledigt sind, können Sie mit der eigentlichen Pfadfindung beginnen. Das Ergebnis ist ein Pfad, der beispielsweise als Liste von Punktkoordinaten dargestellt wird.

Es ist wichtig zu beachten, dass der optimale Pfad vom gewählten Transportmittel abhängen kann, da sich die Geschwindigkeit und das Hindernis-Set unterscheiden können. Daher sollten für jeden Verkehrstyp unterschiedliche Straßen- und Hindernissätze verwendet werden, wenn nach dem optimalen Pfad gesucht wird.

## Demoprojekt auf GitHub

Um die Funktionalität unserer Bibliothek besser zu verstehen, betrachten wir [ein Beispiel für ihre Verwendung](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths). Dieser Code veranschaulicht, wie man Straßen und Hindernisse im Pfadfindungsalgorithmus einrichtet und die optimale Route findet.

Das Beispiel besteht aus den folgenden Schritten:

1. Erstellen einer Liste von Straßeninformationen (RoadInfo), die Informationen über das Straßensegment (Segment) und die Geschwindigkeit der Bewegung (Velocity) enthält.
2. Hinzufügen schneller Straßen zur Liste.
3. Hinzufügen langsamer Ringstraßen zur Liste.
4. Erstellen eines Wegschichtgenerators (WayLayerGenerator) und Hinzufügen von Straßen zum Generator.
5. Suchen mehrerer Pfade vom Startpunkt (startPoint) zu den Zielpunkten (goalPoint01, goalPoint02, goalPoint03) unter Verwendung des angegebenen Radius (radius).
6. Vorbereiten einer Straßenschicht (roadsLayer) zur Anzeige auf der Karte und Hinzufügen von Straßenobjekten.
7. Vorbereiten einer Wegschicht (wayLayer) zur Anzeige auf der Karte und Erstellen geometrischer Objekte für jeden gefundenen Pfad.
8. [Anzeigen der Karte](https://docs.aspose.com/gis/net/how-to-draw-geometry/) mit der Funktion ShowMap, Speichern der Karte am angegebenen Pfad.

Dieser Code erstellt und zeigt Straßenpfade auf der Karte für angegebene Punkte unter Verwendung von Straßeninformationen und dem Wegschichtgenerator an.

## Suchoptionen

Die Pfadfindung wird mithilfe der Klasse **WayLayerGenerator** durchgeführt, die sich im Namespace Aspose.Gis.GeoTools.WayAnalyzer befindet.

Die WayLayerGenerator-Klasse verfügt über die Methode **FindTheWay**, um den Pfad vom Startpunkt zum Ziel zu finden. Um eine Instanz der WayLayerGenerator-Klasse zu erstellen, geben wir die WayOptions als Parameter an (alle Parameter sind optional):

- StartPoint: Der Startpunkt

- GoalPoint: Der Zielpunkt

- Radius: Der Suchradius

- Scale: Die Skala des Gitters

- IsMoveOnlyRoad: Ob nur auf Straßen gesucht werden soll

Das bemerkenswerte Merkmal ist hier der Parameter Scale. Wenn er im Konstruktor angegeben wird, fixieren wir eine konstante Skala für nachfolgende Suchen. Wenn der Parameter Scale nicht gesetzt ist, aber StartPoint und GoalPoint gesetzt sind, berechnen wir die Skala als die Entfernung zwischen dem Start- und Zielpunkt geteilt durch 100. In allen anderen Fällen beträgt der Standardwert von Scale 1. Für erfahrene Benutzer ist es besser, Scale festzulegen oder StartPoint und GoalPoint direkt zu setzen, um Straßen und Hindernisse am effizientesten auf dem Gitter darzustellen (insbesondere wenn es viele davon gibt).

Um die Methode FindTheWay zu verwenden, müssen wir die Start- und Zielpunkte angeben. Wir können auch den Suchradius festlegen (die Entfernung, bis zu der sich die Welle ausbreitet). Standardmäßig wird der Radius als die Entfernung zwischen dem Start- und Zielpunkt multipliziert mit 3 berechnet. Die Start- und Zielpunkte können nahe beieinander oder sehr weit voneinander entfernt sein, daher berechnen wir basierend auf der Entfernung zwischen ihnen die Skala unseres Gitters. Wenn sich die aktuelle Skala nicht mit der vorherigen übereinstimmt, berechnen wir das Gitter neu. Die Skala kann mithilfe des Parameters Scale fixiert werden. In diesem Fall wird sie nicht berechnet und das Gitter wird nicht neu berechnet.

Bevor wir mit der Suche beginnen, müssen wir die Straßen- und Hinderniskarte mithilfe der entsprechenden Methoden AddRoad und AddBlock der WayLayerGenerator-Klasse definieren.

Für die Methode **AddRoad** müssen wir angeben:

- startPoint: Der Startpunkt der Straße

- endPoint: Der Endpunkt der Straße

- velocity: Die Geschwindigkeit der Bewegung auf der Straße

Für die Methode **AddBlock** müssen wir angeben:

- x: Die x-Koordinate der oberen linken Ecke des Blocks

- y: Die y-Koordinate der oberen linken Ecke des Blocks

- sizeX: Die Größe in der x-Achse

- sizeY: Die Größe in der y-Achse

Diese Methoden ermöglichen es uns, die Straßen- und Hinderniskarte zu definieren, bevor wir mit der Pfadfindung beginnen.

## Codebeispiele

Hier sind einige Codebeispiele, die veranschaulichen, wie man Straßen und Hindernisse im Pfadfindungsalgorithmus einrichtet und die optimale Route findet.

Beispiel 1: Finden eines Pfades zwischen Start- und Zielpunkten.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Beispiel 2**: Festlegen des Skalenparameters und Vorhandensein negativer Koordinaten für den Punkt.

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Beispiel 3**: Festlegen des Parameters IsMoveOnlyRoad und Suchradius.

```
WayOptions mapGeneratorOptions = new WayOptions();
mapGeneratorOptions.IsMoveOnlyRoad = true;
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddRoad(new Point(100, 100), new Point(140, 150), 10);
generator.AddRoad(new Point(140, 150), new Point(190, 100), 10);
Point startPoint = new Point(100, 100);
Point goalPoint = new Point(190, 100);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 100);
```

**Beispiel 4**: Festlegen des Skalenparameters für eine schnellere Suche.

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**Beispiel 5**: Mehrfaches Suchbeispiel.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddBlock(200, 1700, 1500, 100, 0);
generator.AddBlock(1700, 200, 100, 1600, 0);
generator.AddBlock(200, 200, 1500, 100, 0);
generator.AddRoad(new Point(1000, 1150), new Point(200, 600), 10);
generator.AddRoad(new Point(50, 450), new Point(150, 1850), 10);

Point startPoint = new Point(1000, 1000);
Point goalPoint = new Point(1900, 1000);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 3500);

Point startPoint = new Point(50, 50);
Point goalPoint = new Point(70, 70);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

Diese Codebeispiele erstellen und zeigen Straßenpfade auf der Karte für angegebene Punkte unter Verwendung von Straßeninformationen und dem Wegschichtgenerator an.

**Zusammenfassend** ist der optimale Pfadfinder ein leistungsstarkes Werkzeug zur Analyse von Straßennetzen und zur Bestimmung der effizientesten Routen zwischen Punkten auf einer Karte. Er berücksichtigt verschiedene Faktoren wie Straßentypen, Hindernisse und unterschiedliche Geschwindigkeiten, um den optimalen Pfad zu berechnen. Mit der Möglichkeit, sowohl auf Straßen als auch abseits davon zu suchen, sowie die Steuerung des Suchradius und die Anpassung von Leistung und Genauigkeit bietet dieser Algorithmus eine vielseitige Lösung für die Routenoptimierung. Durch die Berücksichtigung verschiedener Transportmittel und die Anpassung von Straßen- und Hindernissätzen entsprechend kann er in verschiedenen Szenarien eingesetzt werden, z. B. bei der Lieferplanung oder der Pendeloptimierung. Die bereitgestellten Codebeispiele und Erklärungen demonstrieren die Fähigkeiten des Algorithmus und die Schritte, die zu seiner Nutzung erforderlich sind. Letztendlich bietet der optimale Pfadfinder eine robuste Möglichkeit, die effizientesten Routen zu finden und die Navigation in einem Straßennetz zu verbessern.