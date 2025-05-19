---
title: "เครื่องสร้างไทล์"
type: docs
url: /th/net/geo-tools/generator-of-tiles/
description: "วิธีการสร้างไทล์แผนที่"
weight: 70
---

# เครื่องสร้างไทล์

แผนที่ไทล์เป็นวิธีที่เป็นที่นิยมมากที่สุดในการแสดงและนำทางแผนที่ `GeneratorTiles` มีเมธอดสำหรับการเรนเดอร์ไทล์สำหรับแผนที่ที่สร้างขึ้น หรือเพื่อวัตถุประสงค์อื่นๆ เราต้องตั้งค่าเลเยอร์อินพุต (หรือหลายเลเยอร์) ไดเรกทอรีเอาต์พุต และพารามิเตอร์ซูม หากเรามีมากกว่าหนึ่งเลเยอร์ สำหรับแต่ละเลเยอร์ เราจะรวมรูปทรงเรขาคณิตและสร้างเลเยอร์ที่ผสานกันใหม่ ไทล์ทั้งหมดจะถูกสร้างในไดเรกทอรีเอาต์พุตที่ตั้งค่าไว้ และมีชื่อว่า `tile_zxy_{z}_{x}_{y}` โดยที่ `z` คือพารามิเตอร์ซูม, `x` และ `y` คือพิกัดของขอบเขตมุมบนซ้ายของไทล์ ที่ระดับการซูม "0" เลเยอร์ทั้งหมดจะถูกเรนเดอร์ในไทล์แผนที่เดียว แต่ละระดับการซูมจะเพิ่มขึ้นเป็นสองเท่าในทั้งสองมิติ ดังนั้นไทล์เดียวจะถูกแทนที่ด้วย 4 ไทล์เมื่อทำการซูมเข้า ไทล์จะถูกบันทึกด้วยนามสกุล "png"

## ตัวอย่างกับเลเยอร์ InMemory

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // เพื่อดูไทล์ทั้งหมด
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // เพื่อดู 4 ไทล์
```

## ตัวอย่างเมื่อเราได้รับเลเยอร์จากไฟล์ GeoJson (หรืออื่นๆ)

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // เพื่อดูไทล์ทั้งหมด
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // เพื่อดู 16 ไทล์

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // เพื่อดูไทล์ทั้งหมด
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // เพื่อดู 16 ไทล์
```

## ตัวอย่างกับหลายเลเยอร์

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // เพื่อดูไทล์ทั้งหมด
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // เพื่อดู 4 ไทล์
```
