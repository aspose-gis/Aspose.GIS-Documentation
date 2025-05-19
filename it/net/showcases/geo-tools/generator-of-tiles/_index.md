---
title: "Generatore di Tiles"
type: docs
url: /it/net/geo-tools/generator-of-tiles/
description: "Come generare le tile delle mappe"
weight: 70
---

# Generatore di tiles

La mappa a tile è il modo più popolare per visualizzare e navigare nelle mappe. `GeneratorTiles` ha metodi per renderizzare le tile per una mappa costruita o per altri scopi pratici.
Dobbiamo impostare il layer (o i layer) di input, la directory di output e il parametro zoom. Se abbiamo più di un layer, allora per ogni layer uniamo le geometrie e creiamo un nuovo layer unito. Tutte le tile vengono create nella directory di output impostata e hanno il nome `tile_zxy_{z}_{x}_{y}`, dove `z` è il parametro zoom, `x` e `y` sono le coordinate dell'estensione dell'angolo superiore sinistro della tile. Al livello di zoom "0", l'intero layer verrà renderizzato in una singola tile della mappa. Ogni livello di zoom raddoppia in entrambe le dimensioni, quindi una singola tile viene sostituita da 4 tile quando si esegue lo zoom. Le tile vengono salvate con estensione "png".

## Esempio con layer InMemory

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // per vedere l'intera tile
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // per vedere 4 tile
```

## Esempio quando otteniamo il layer da un file GeoJson (o altro)

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // per vedere l'intera tile
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // per vedere 16 tile

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // per vedere l'intera tile
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // per vedere 16 tile
```

## Esempio con più layer

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // per vedere l'intera tile
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // per vedere 4 tile
```
