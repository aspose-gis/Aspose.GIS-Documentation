---
title: "تولیدکننده کاشی‌ها"
type: docs
url: /fa/net/geo-tools/generator-of-tiles/
description: "نحوه تولید کاشی‌های نقشه"
weight: 70
---

# تولیدکننده کاشی‌ها

نقشه کاشی‌ای محبوب‌ترین راه برای نمایش و پیمایش نقشه‌ها است. `GeneratorTiles` دارای متدهایی برای رندر کردن کاشی‌ها برای نقشه ساخته شده یا اهداف عملی دیگر است.
ما باید لایه ورودی (یا لایه‌ها)، دایرکتوری خروجی و پارامتر بزرگنمایی را تنظیم کنیم. اگر بیش از یک لایه داشته باشیم، سپس برای هر لایه، هندسه‌ها را ادغام می‌کنیم و یک لایه جدید ادغام شده ایجاد می‌کنیم. همه کاشی‌ها در دایرکتوری خروجی تعیین‌شده ایجاد می‌شوند و نام `tile_zxy_{z}_{x}_{y}` را دارند، که در آن `z` پارامتر بزرگنمایی، `x` و `y` مختصات گسترش گوشه سمت چپ کاشی هستند. در سطح بزرگنمایی "0"، کل لایه در یک کاشی نقشه واحد رندر می‌شود. هر سطح بزرگنمایی در هر دو بعد دو برابر می‌شود، بنابراین یک کاشی واحد هنگام بزرگنمایی با 4 کاشی جایگزین می‌شود. کاشی‌ها با پسوند "png" ذخیره می‌شوند.

## مثال با لایه InMemory
```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // برای دیدن کل کاشی
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // برای دیدن 4 کاشی
```

## مثال زمانی که لایه را از فایل GeoJson (یا دیگر) دریافت می‌کنیم

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // برای دیدن کل کاشی
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // برای دیدن 16 کاشی

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // برای دیدن کل کاشی
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // برای دیدن 16 کاشی
```

## مثال با لایه‌های چندگانه

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // برای دیدن کل کاشی
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // برای دیدن 4 کاشی
```
