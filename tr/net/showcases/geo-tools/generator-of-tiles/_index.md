---
title: "Döşeme Üreticisi"
type: docs
url: /tr/net/geo-tools/generator-of-tiles/
description: "Harita döşemeleri nasıl oluşturulur"
weight: 70
---

# Döşeme Üreticisi

Döşeme haritası, haritaları görüntülemenin ve bunlarda gezinmenin en popüler yoludur. `GeneratorTiles`, yerleşik harita veya diğer pratik amaçlar için döşemeler oluşturmak için yöntemlere sahiptir.
Giriş katmanını (veya katmanlarını), çıktı dizinini ve yakınlaştırma parametresini ayarlamamız gerekir. Birden fazla katmanımız varsa, her katman için geometrileri birleştirir ve yeni bir birleşik katman oluşturur. Tüm döşemeler ayarlanmış çıktı dizinine `tile_zxy_{z}_{x}_{y}` adıyla kaydedilir; burada `z` yakınlaştırma parametresidir, `x` ve `y` ise sol üst köşenin kapsamının koordinatlarıdır. "0" yakınlaştırma seviyesinde tüm katman tek bir harita döşemesine işlenir. Her yakınlaştırma seviyesi her iki boyutta da ikiye katlanır; bu nedenle, yakınlaştırıldığında tek bir döşeme 4 döşemeyle değiştirilir. Döşemeler "png" uzantısıyla kaydedilir.

## Bellekte Katman Örneği

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // tüm döşemeyi görmek için
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // 4 döşeme görmek için
```

## Katmanı GeoJson (veya diğer) dosyasından aldığımızda Örnek

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // tüm döşemeyi görmek için
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // 16 döşeme görmek için

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // tüm döşemeyi görmek için
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // 16 döşeme görmek için
```

## Çoklu katmanlı örnek

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // tüm döşemeyi görmek için
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // 4 döşeme görmek için
```
