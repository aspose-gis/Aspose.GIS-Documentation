---
title: "Kachelgenerator"
type: docs
url: /de/net/geo-tools/generator-of-tiles/
description: "So generieren Sie Kartenkacheln"
weight: 70
---

# Kachelgnerator

Eine Tile-Karte ist die beliebteste Methode, um Karten anzuzeigen und zu navigieren. `GeneratorTiles` verfügt über Methoden zum Rendern von Kacheln für erstellte Karten oder andere praktische Zwecke.
Wir müssen die Eingabeschicht (oder Schichten), das Ausgabeverzeichnis und den Zoomparameter festlegen. Wenn wir mehr als eine Schicht haben, dann verbinden wir für jede Schicht Geometrien und erstellen eine neue zusammengeführte Schicht. Alle Kacheln werden im festgelegten Ausgabeverzeichnis erstellt und heißen `tile_zxy_{z}_{x}_{y}`, wobei `z` der Zoomparameter ist, `x` und `y` die Koordinaten des linken oberen Eckpunkts des Kachelbereichs sind. Auf Zoomstufe "0" wird die gesamte Schicht in einer einzigen Kartenkachel gerendert. Jede Zoomstufe verdoppelt sich in beiden Dimensionen, sodass eine einzelne Kachel beim Zoomen in 4 Kacheln ersetzt wird. Die Kacheln werden mit der Erweiterung "png" gespeichert.

## Beispiel mit InMemory-Schicht

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // um die gesamte Kachel zu sehen
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // um 4 Kacheln zu sehen
```

## Beispiel, wenn wir eine Schicht aus einer GeoJson- (oder anderen) Datei erhalten

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // um die gesamte Kachel zu sehen
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // um 16 Kacheln zu sehen

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // um die gesamte Kachel zu sehen
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // um 16 Kacheln zu sehen
```

## Beispiel mit mehreren Schichten

```csharp
var layer1 = Drivers.InMemory.CreateLayer();
var layer2 = Drivers.InMemory.CreateLayer();
var layer3 = Drivers.InMemory.CreateLayer();

Feature feature1 = layer1.ConstructFeature();
feature1.Geometry = Geometry.FromText("LINESTRING(-250 100, 0 0)");
layer1.Add(feature1);

Feature feature2 = layer1.ConstructFeature();
feature2.Geometry = Geometry.FromText("LINESTRING(0 100, 250 200)");
layer2.Add(feature2);

Feature feature3 = layer1.ConstructFeature();
feature3.Geometry = Geometry.FromText("LINESTRING(-250 200, 250 0)");
layer3.Add(feature3);

List<VectorLayer> listLayers = new List<VectorLayer>();
listLayers.Add(layer1);
listLayers.Add(layer2);
listLayers.Add(layer3);

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // um die gesamte Kachel zu sehen
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // um 4 Kacheln zu sehen
```
