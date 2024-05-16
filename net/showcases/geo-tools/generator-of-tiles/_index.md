---
title: "Tiles Generator"
type: docs
url: /net/geo-tools/generator-of-tiles/
description: "How to generate map tiles"
weight: 70
---

# Generator of tiles

Tile map is the most popular way to display and navigate maps. `GeneratorTiles` have methods to render tiles for built map or other practical purposes. 
We need to set the input layer (or layers), output directory, and zoom parameter. If we have more than one layer, then for each layer, we join geometries and create a new merged layer. All tiles are created in the setting output directory and have the name `tile_zxy_{z}_{x}_{y}`, where `z` is the zoom parameter, `x` and `y` are the coordinates of the left corner tile's extent. At zoom level "0," the entire layer will be rendered in a single map tile. Each zoom level doubles in both dimensions, so a single tile is replaced by 4 tiles when zooming in. The tiles are saved with the "png" extension.

## Example with InMemory layer

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // to see entire tile
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // to see 4 tiles 
```

## Example when we get layer from GeoJson (or other) file

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // to see entire tile
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // to see 16 tiles 

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // to see entire tile
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // to see 16 tiles 
```

## Example with multi layers

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // to see entire tile
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // to see 4 tiles 
```