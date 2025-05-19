---
title: "タイルジェネレーター"
type: docs
url: /ja/net/geo-tools/generator-of-tiles/
description: "地図タイルの生成方法"
weight: 70
---

# タイルジェネレーター

タイルマップは、地図を表示およびナビゲートする最も一般的な方法です。`GeneratorTiles` には、構築された地図またはその他の実用的な目的のためにタイルをレンダリングするためのメソッドがあります。
入力レイヤー（またはレイヤー）、出力ディレクトリ、およびズームパラメーターを設定する必要があります。 1 つ以上のレイヤーがある場合、各レイヤーに対してジオメトリを結合し、新しいマージされたレイヤーを作成します。 すべてのタイルは設定された出力ディレクトリに作成され、名前は `tile_zxy_{z}_{x}_{y}` であり、ここで `z` はズームパラメーター、`x` と `y` はタイルの左上隅の範囲の座標です。 ズームレベル「0」では、レイヤー全体が単一の地図タイルにレンダリングされます。 各ズームレベルは両方の次元で倍増するため、ズームインすると単一のタイルが4つのタイルに置き換えられます。 タイルは "png" 拡張子で保存されます。

## InMemory レイヤーを使用した例

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // タイル全体を見るため
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // 4つのタイルを見るため
```

## GeoJson（またはその他）ファイルからレイヤーを取得する例

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // タイル全体を見るため
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // 16タイルを見るため

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // タイル全体を見るため
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // 16タイルを見るため
```

## マルチレイヤーを使用した例

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // タイル全体を見るため
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // 4つのタイルを見るため
```
