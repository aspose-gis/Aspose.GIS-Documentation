---
title: "타일 생성기"
type: docs
url: /ko/net/geo-tools/generator-of-tiles/
description: "맵 타일을 생성하는 방법"
weight: 70
---

# 타일 생성기

타일 맵은 맵을 표시하고 탐색하는 가장 일반적인 방법입니다. `GeneratorTiles`는 빌드된 맵 또는 기타 실용적인 목적으로 타일을 렌더링하기 위한 메서드를 가지고 있습니다. 입력 레이어(또는 레이어), 출력 디렉토리 및 확대/축소 매개변수를 설정해야 합니다. 둘 이상의 레이어가 있는 경우 각 레이어에 대해 지오메트리를 결합하고 새 병합된 레이어를 만듭니다. 모든 타일은 설정된 출력 디렉토리에 생성되며 이름은 `tile_zxy_{z}_{x}_{y}`이며, 여기서 `z`는 확대/축소 매개변수이고, `x`와 `y`는 타일 범위의 왼쪽 모서리 좌표입니다. 확대/축소 레벨 "0"에서 전체 레이어가 단일 맵 타일로 렌더링됩니다. 각 확대/축소 레벨은 양쪽 차원에서 두 배가 되므로 확대할 때 단일 타일이 4개의 타일로 대체됩니다. 타일은 "png" 확장자로 저장됩니다.

## InMemory 레이어를 사용한 예제

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // 전체 타일 확인
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // 4개의 타일 확인
```

## GeoJson (또는 기타) 파일에서 레이어를 가져오는 경우의 예제

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // 전체 타일 확인
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // 16개의 타일 확인

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // 전체 타일 확인
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // 16개의 타일 확인
```

## 다중 레이어를 사용한 예제

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // 전체 타일 확인
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // 4개의 타일 확인
```
