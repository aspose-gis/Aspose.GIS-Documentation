---
title: "Генератор тайлов"
type: docs
url: /ru/net/geo-tools/generator-of-tiles/
description: "Как генерировать тайлы карты"
weight: 70
---

# Генератор тайлов

Карта тайлов - самый популярный способ отображения и навигации по картам. `GeneratorTiles` имеет методы для рендеринга тайлов для построенной карты или других практических целей.
Нам нужно установить входной слой (или слои), выходной каталог и параметр масштабирования. Если у нас более одного слоя, то для каждого слоя мы объединяем геометрии и создаем новый объединенный слой. Все тайлы создаются в указанном выходном каталоге и имеют имя `tile_zxy_{z}_{x}_{y}`, где `z` - параметр масштабирования, `x` и `y` - координаты левого верхнего угла области тайла. На уровне масштабирования "0" весь слой будет отображен в одном тайле карты. Каждый уровень масштабирования удваивается в обоих измерениях, поэтому один тайл заменяется 4 тайлами при увеличении масштаба. Тайлы сохраняются с расширением "png".

## Пример со слоем InMemory

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // чтобы увидеть весь тайл
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // чтобы увидеть 4 тайла
```

## Пример, когда мы получаем слой из файла GeoJson (или другого)

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // чтобы увидеть весь тайл
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // чтобы увидеть 16 тайлов

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // чтобы увидеть весь тайл
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // чтобы увидеть 16 тайлов
```

## Пример с многослойным слоем

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // чтобы увидеть весь тайл
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // чтобы увидеть 4 тайла
```
