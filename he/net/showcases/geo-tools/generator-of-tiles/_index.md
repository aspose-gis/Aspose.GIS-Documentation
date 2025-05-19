---
title: "מחולל אריחים"
type: docs
url: /he/net/geo-tools/generator-of-tiles/
description: "כיצד ליצור אריחי מפה"
weight: 70
---

# מחולל אריחים

מפת אריחים היא הדרך הפופולרית ביותר להציג ולנווט במפות. ל`GeneratorTiles` יש שיטות לעיבוד אריחים עבור מפה בנויה או למטרצים מעשיים אחרים. 
עלינו להגדיר את שכבת הקלט (או השכבות), ספריית הפלט ופרמטר הזום. אם יש לנו יותר משכבה אחת, אז עבור כל שכבה, אנחנו מצטרפים לצורות גיאומטריות ויוצרים שכבה מיזוג חדשה. כל האריחים נוצרים בספריית הפלט המוגדרת ויש להם את השם `tile_zxy_{z}_{x}_{y}`, כאשר `z` הוא פרמטר הזום, `x` ו-`y` הם הקואורדינטות של היקף הפינה השמאלית העליונה של האריח. ברמת זום "0", כל השכבה תעובד באריח מפה אחד. בכל רמת זום מכפילים את המימדים פי שניים, כך שאריח בודד מוחלף ב-4 אריחים בעת הגדלת הזום. האריחים נשמרים עם סיומת "png".

## דוגמה עם שכבת InMemory
```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // כדי לראות את האריח כולו
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // כדי לראות 4 אריחים 
```

## דוגמה כאשר אנחנו מקבלים שכבה מקובץ GeoJson (או אחר)
```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // כדי לראות את האריח כולו
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // כדי לראות 16 אריחים 

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // כדי לראות את האריח כולו
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // כדי לראות 16 אריחים 
```

## דוגמה עם שכבות מרובות
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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // כדי לראות את האריח כולו
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // כדי לראות 4 אריחים 
```
