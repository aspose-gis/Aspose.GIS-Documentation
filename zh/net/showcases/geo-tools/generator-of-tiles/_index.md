---
title: "瓦片生成器"
type: docs
url: /zh/net/geo-tools/generator-of-tiles/
description: "如何生成地图瓦片"
weight: 70
---

# 瓦片生成器

切片地图是最流行的显示和导航地图的方式。`GeneratorTiles` 有方法来渲染构建的地图或其他实际用途的瓦片。
我们需要设置输入图层（或图层）、输出目录和缩放参数。如果有多于一个图层，那么对于每个图层，我们都将连接几何体并创建一个新的合并图层。所有瓦片都在设置的输出目录中创建，名称为 `tile_zxy_{z}_{x}_{y}`，其中 `z` 是缩放参数，`x` 和 `y` 是左上角瓦片范围的坐标。在缩放级别“0”处，整个图层将渲染成单个地图瓦片。每个缩放级别在两个维度上都加倍，因此当放大时，单个瓦片会被 4 个瓦片取代。瓦片以 "png" 扩展名保存。

## 使用 InMemory 图层的示例

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // 查看整个瓦片
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // 查看 4 个瓦片
```

## 当我们从 GeoJson（或其他）文件获取图层时的示例

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // 查看整个瓦片
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // 查看 16 个瓦片

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // 查看整个瓦片
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // 查看 16 个瓦片
```

## 多层图层的示例

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // 查看整个瓦片
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // 查看 4 个瓦片
```
