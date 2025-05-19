---
title: "Генератор плиток"
type: docs
url: /uk/net/geo-tools/generator-of-tiles/
description: "Як генерувати плитки карти"
weight: 70
---

# Генератор плиток

Плитка карти є найпопулярнішим способом відображення та навігації картами. `GeneratorTiles` має методи для рендерингу плиток для створеної карти або інших практичних цілей.
Нам потрібно задати вхідний шар (або шари), вихідну директорію та параметр масштабування. Якщо у нас більше одного шару, то для кожного шару ми об'єднуємо геометрії та створюємо новий злитий шар. Усі плитки створюються у заданій вихідній директорії і мають назву `tile_zxy_{z}_{x}_{y}`, де `z` - параметр масштабування, `x` і `y` - координати лівого кута екстенту плитки. На рівні масштабування "0" весь шар буде відрендерений в одній плитці карти. Кожен рівень масштабування подвоюється в обох вимірах, тому одна плитка замінюється 4 плитками при збільшенні масштабу. Плитки зберігаються з розширенням "png".

## Приклад з шаром InMemory
```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // щоб побачити всю плитку
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // щоб побачити 4 плитки
```

## Приклад коли ми отримуємо шар з GeoJson (або іншого) файлу
```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // щоб побачити всю плитку
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // щоб побачити 16 плиток

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // щоб побачити всю плитку
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // щоб побачити 16 плиток
```

## Приклад з багатошаровим шаром
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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // щоб побачити всю плитку
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // щоб побачити 4 плитки
```
