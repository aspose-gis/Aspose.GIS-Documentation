---
title: "مولد المربعات"
type: docs
url: /ar/net/geo-tools/generator-of-tiles/
description: "كيفية إنشاء مربعات الخرائط"
weight: 70
---

# مولد المربعات

خريطة المربعات هي الطريقة الأكثر شيوعًا لعرض الخرائط والتنقل فيها. `GeneratorTiles` لديه طرق لتقديم المربعات للخرائط المبنية أو لأغراض عملية أخرى.
نحن بحاجة إلى تعيين الطبقة المدخلة (أو الطبقات) ودليل الإخراج ومعامل التكبير. إذا كان لدينا أكثر من طبقة واحدة، فلكل طبقة، فإننا نجمع الهندسة وننشئ طبقة مدمجة جديدة. يتم إنشاء جميع المربعات في دليل الإخراج المحدد ولديها الاسم `tile_zxy_{z}_{x}_{y}`، حيث `z` هو معامل التكبير، و `x` و `y` هما إحداثيات مدى الزاوية اليسرى للمربع. عند مستوى التكبير "0"، سيتم تقديم الطبقة بأكملها في مربع خريطة واحد. يتضاعف كل مستوى تكبير في كلا البعدين، لذلك يتم استبدال مربع واحد بـ 4 مربعات عند التكبير. يتم حفظ المربعات بامتداد "png".

## مثال مع طبقة InMemory

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // لرؤية المربع بأكمله
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // لرؤية 4 مربعات
```

## مثال عندما نحصل على طبقة من ملف GeoJson (أو غيره)

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // لرؤية المربع بأكمله
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // لرؤية 16 مربعًا

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // لرؤية المربع بأكمله
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // لرؤية 16 مربعًا
```

## مثال مع طبقات متعددة

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // لرؤية المربع بأكمله
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // لرؤية 4 مربعات
```
