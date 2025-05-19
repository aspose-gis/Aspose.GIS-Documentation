---
title: "Generator Płytki"
type: docs
url: /pl/net/geo-tools/generator-of-tiles/
description: "Jak generować płytki mapy"
weight: 70
---

# Generator Płytki

Mapa w postaci płytek to najpopularniejszy sposób wyświetlania i nawigacji po mapach. `GeneratorTiles` posiada metody do renderowania płytek dla zbudowanej mapy lub innych praktycznych celów.
Musimy ustawić warstwę wejściową (lub warstwy), katalog wyjściowy oraz parametr zoomu. Jeśli mamy więcej niż jedną warstwę, to dla każdej warstwy łączymy geometrie i tworzymy nową scaloną warstwę. Wszystkie płytki są tworzone w ustawionym katalogu wyjściowym i mają nazwę `tile_zxy_{z}_{x}_{y}`, gdzie `z` jest parametrem zoomu, a `x` i `y` to współrzędne lewego górnego rogu zasięgu płytki. Przy poziomie zoomu "0" cała warstwa zostanie wyrenderowana w jednej płytce mapy. Każdy poziom zoomu podwaja się w obu wymiarach, więc pojedyncza płytka jest zastępowana przez 4 płytki podczas powiększania. Płytki są zapisywane z rozszerzeniem "png".

## Przykład z warstwą InMemory
```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // aby zobaczyć całą płytkę
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // aby zobaczyć 4 płytki
```

## Przykład gdy pobieramy warstwę z pliku GeoJson (lub innego)
```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // aby zobaczyć całą płytkę
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // aby zobaczyć 16 płytek

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // aby zobaczyć całą płytkę
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // aby zobaczyć 16 płytek
```

## Przykład z wieloma warstwami
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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // aby zobaczyć całą płytkę
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // aby zobaczyć 4 płytki
```
