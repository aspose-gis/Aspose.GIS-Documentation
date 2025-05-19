---
title: "Bộ tạo ô"
type: docs
url: /vi/net/geo-tools/generator-of-tiles/
description: "Cách tạo các ô bản đồ"
weight: 70
---

# Bộ tạo ô

Bản đồ ô là cách phổ biến nhất để hiển thị và điều hướng bản đồ. `GeneratorTiles` có các phương thức để kết xuất các ô cho bản đồ được xây dựng hoặc các mục đích thực tế khác.
Chúng ta cần đặt lớp đầu vào (hoặc các lớp), thư mục đầu ra và tham số thu phóng. Nếu chúng ta có nhiều hơn một lớp, thì đối với mỗi lớp, chúng ta sẽ hợp nhất các hình học và tạo một lớp hợp nhất mới. Tất cả các ô được tạo trong thư mục đầu ra đã cài đặt và có tên `tile_zxy_{z}_{x}_{y}`, trong đó `z` là tham số thu phóng, `x` và `y` là tọa độ của phạm vi góc trái trên của ô. Ở mức thu phóng "0", toàn bộ lớp sẽ được kết xuất trong một ô bản đồ duy nhất. Mỗi cấp độ thu phóng tăng gấp đôi theo cả hai chiều, vì vậy một ô duy nhất được thay thế bằng 4 ô khi thu phóng. Các ô được lưu với phần mở rộng "png".

## Ví dụ với lớp InMemory

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // để xem toàn bộ ô
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // để xem 4 ô
```

## Ví dụ khi chúng ta lấy lớp từ tệp GeoJson (hoặc các tệp khác)

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // để xem toàn bộ ô
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // để xem 16 ô

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // để xem toàn bộ ô
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // để xem 16 ô
```

## Ví dụ với nhiều lớp

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // để xem toàn bộ ô
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // để xem 4 ô
```
