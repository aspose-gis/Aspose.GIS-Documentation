---
title: "Générateur de tuiles"
type: docs
url: /fr/net/geo-tools/generator-of-tiles/
description: "Comment générer des tuiles cartographiques"
weight: 70
---

# Générateur de tuiles

La carte en mosaïque est la manière la plus populaire d'afficher et de naviguer sur les cartes. `GeneratorTiles` dispose de méthodes pour rendre des tuiles pour une carte construite ou à d'autres fins pratiques. 
Nous devons définir la couche (ou les couches) d'entrée, le répertoire de sortie et le paramètre de zoom. Si nous avons plus d'une couche, alors pour chaque couche, nous joignons les géométries et créons une nouvelle couche fusionnée. Toutes les tuiles sont créées dans le répertoire de sortie défini et ont le nom `tile_zxy_{z}_{x}_{y}`, où `z` est le paramètre de zoom, `x` et `y` sont les coordonnées de l'étendue du coin supérieur gauche de la tuile. Au niveau de zoom "0", toute la couche sera rendue dans une seule tuile cartographique. Chaque niveau de zoom double dans les deux dimensions, donc une seule tuile est remplacée par 4 tuiles lors d'un zoom avant. Les tuiles sont enregistrées avec l'extension "png".

## Exemple avec une couche InMemory
```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // pour voir toute la tuile
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // pour voir 4 tuiles 
```

## Exemple lorsque nous obtenons une couche à partir d'un fichier GeoJson (ou autre)
```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // pour voir toute la tuile
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // pour voir 16 tuiles 

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // pour voir toute la tuile
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // pour voir 16 tuiles 
```

## Exemple avec plusieurs couches
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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // pour voir toute la tuile
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // pour voir 4 tuiles 
```
