---
title: "Tegelgenerator"
type: docs
url: /nl/net/geo-tools/generator-of-tiles/
description: "Hoe tegels voor kaarten te genereren"
weight: 70
---

# Tegelgenerator

Een tegelkaart is de meest populaire manier om kaarten weer te geven en te navigeren. `GeneratorTiles` heeft methoden om tegels te renderen voor een gebouwde kaart of andere praktische doeleinden.
We moeten de invoerlaag (of lagen), uitvoermap en zoomparameter instellen. Als we meer dan één laag hebben, voegen we voor elke laag geometrieën samen en maken we een nieuwe samengevoegde laag. Alle tegels worden gemaakt in de ingestelde uitvoermap en hebben de naam `tile_zxy_{z}_{x}_{y}`, waarbij `z` de zoomparameter is, `x` en `y` de coördinaten zijn van de omvang van de linkerhoektegel. Op zoomniveau "0" wordt de hele laag weergegeven in één kaarttegel. Elk zoomniveau verdubbelt in beide dimensies, dus één tegel wordt vervangen door 4 tegels bij het zoomen. De tegels worden opgeslagen met de extensie "png".

## Voorbeeld met InMemory-laag

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // om de hele tegel te zien
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // om 4 tegels te zien
```

## Voorbeeld wanneer we een laag krijgen uit een GeoJson (of ander) bestand

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // om de hele tegel te zien
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // om 16 tegels te zien

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // om de hele tegel te zien
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // om 16 tegels te zien
```

## Voorbeeld met meerdere lagen

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // om de hele tegel te zien
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // om 4 tegels te zien
```
