---
title: "Генератор на плочки"
type: docs
url: /bg/net/geo-tools/generator-of-tiles/
description: "Как да генерираме картографски плочки"
weight: 70
---

# Генератор на плочки

Картографска плочка е най-популярният начин за показване и навигиране в карти. `GeneratorTiles` има методи за рендиране на плочки за създадена карта или други практически цели.
Трябва да зададем входния слой (или слоеве), изходната директория и параметъра за увеличение. Ако имаме повече от един слой, тогава за всеки слой обединяваме геометриите и създаваме нов обединен слой. Всички плочки се създават в зададената изходна директория и имат име `tile_zxy_{z}_{x}_{y}`, където `z` е параметърът за увеличение, а `x` и `y` са координатите на обхвата на горния ляв ъгъл на плочката. На ниво на увеличение "0" целият слой ще бъде рендиран в една картографска плочка. Всяко ниво на увеличение се удвоява в двете измерения, така че една плочка се заменя от 4 плочки при приближаване. Плочките се запазват с разширение "png".

## Пример със слой InMemory
```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // за да видим цялата плочка
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // за да видим 4 плочки
```

## Пример, когато получаваме слой от GeoJson (или друг) файл
```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // за да видим цялата плочка
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // за да видим 16 плочки

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // за да видим цялата плочка
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // за да видим 16 плочки
```

## Пример с много слоеве
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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // за да видим цялата плочка
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // за да видим 4 плочки
```
