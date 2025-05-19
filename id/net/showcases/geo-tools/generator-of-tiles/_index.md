---
title: "Pembuat Ubin"
type: docs
url: /id/net/geo-tools/generator-of-tiles/
description: "Cara membuat ubin peta"
weight: 70
---

# Pembuat Ubin

Peta ubin adalah cara paling populer untuk menampilkan dan menavigasi peta. `GeneratorTiles` memiliki metode untuk merender ubin untuk peta yang dibangun atau tujuan praktis lainnya.
Kita perlu mengatur lapisan input (atau lapisan), direktori output, dan parameter zoom. Jika kita memiliki lebih dari satu lapisan, maka untuk setiap lapisan, kita menggabungkan geometri dan membuat lapisan gabungan baru. Semua ubin dibuat di direktori output yang ditentukan dan memiliki nama `tile_zxy_{z}_{x}_{y}`, di mana `z` adalah parameter zoom, `x` dan `y` adalah koordinat dari luas sudut kiri atas ubin. Pada level zoom "0", seluruh lapisan akan dirender dalam satu ubin peta. Setiap level zoom berlipat ganda dalam kedua dimensi, sehingga satu ubin diganti oleh 4 ubin saat memperbesar. Ubin disimpan dengan ekstensi "png".

## Contoh dengan lapisan InMemory

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // untuk melihat seluruh ubin
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // untuk melihat 4 ubin
```

## Contoh saat kita mendapatkan lapisan dari file GeoJson (atau lainnya)

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // untuk melihat seluruh ubin
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // untuk melihat 16 ubin

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // untuk melihat seluruh ubin
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // untuk melihat 16 ubin
```

## Contoh dengan multi lapisan

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // untuk melihat seluruh ubin
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // untuk melihat 4 ubin
```
