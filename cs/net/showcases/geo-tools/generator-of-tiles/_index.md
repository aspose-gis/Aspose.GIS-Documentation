---
title: "Generátor dlaždic"
type: docs
url: /cs/net/geo-tools/generator-of-tiles/
description: "Jak generovat mapové dlaždice"
weight: 70
---

# Generátor dlaždic

Dlaždicová mapa je nejpopulárnější způsob zobrazování a navigace v mapách. `GeneratorTiles` má metody pro vykreslování dlaždic pro sestavenou mapu nebo jiné praktické účely.
Musíme nastavit vstupní vrstvu (nebo vrstvy), výstupní adresář a parametr zoomu. Pokud máme více než jednu vrstvu, pak pro každou vrstvu spojíme geometrie a vytvoříme novou sloučenou vrstvu. Všechny dlaždice jsou vytvářeny v nastaveném výstupním adresáři a mají název `tile_zxy_{z}_{x}_{y}`, kde `z` je parametr zoomu, `x` a `y` jsou souřadnice levého horního rohu rozsahu dlaždice. Při úrovni zoomu "0" bude celá vrstva vykreslena v jedné mapové dlaždici. Každá úroveň zoomu se zdvojnásobí v obou rozměrech, takže jedna dlaždice je nahrazena 4 dlaždicemi při přiblížení. Dlaždice jsou uloženy s příponou "png".

## Příklad s vrstvou InMemory

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // pro zobrazení celé dlaždice
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // pro zobrazení 4 dlaždic
```

## Příklad, když získáváme vrstvu ze souboru GeoJson (nebo jiného)

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // pro zobrazení celé dlaždice
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // pro zobrazení 16 dlaždic

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // pro zobrazení celé dlaždice
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // pro zobrazení 16 dlaždic
```

## Příklad s více vrstvami

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // pro zobrazení celé dlaždice
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // pro zobrazení 4 dlaždic
```
