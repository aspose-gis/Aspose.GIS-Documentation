---
title: "Generador de Mosaicos"
type: docs
url: /es/net/geo-tools/generator-of-tiles/
description: "Cómo generar mosaicos de mapas"
weight: 70
---

# Generador de mosaicos

El mapa de mosaicos es la forma más popular de mostrar y navegar por los mapas. `GeneratorTiles` tiene métodos para renderizar mosaicos para un mapa construido u otros fines prácticos.
Necesitamos establecer la capa (o capas) de entrada, el directorio de salida y el parámetro de zoom. Si tenemos más de una capa, entonces para cada capa, unimos las geometrías y creamos una nueva capa fusionada. Todos los mosaicos se crean en el directorio de salida configurado y tienen el nombre `tile_zxy_{z}_{x}_{y}`, donde `z` es el parámetro de zoom, `x` e `y` son las coordenadas de la extensión de la esquina superior izquierda del mosaico. En el nivel de zoom "0", toda la capa se renderizará en un solo mosaico de mapa. Cada nivel de zoom se duplica en ambas dimensiones, por lo que un solo mosaico es reemplazado por 4 mosaicos al hacer zoom. Los mosaicos se guardan con la extensión "png".

## Ejemplo con capa InMemory

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // para ver todo el mosaico
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // para ver 4 mosaicos
```

## Ejemplo cuando obtenemos la capa de un archivo GeoJson (u otro)

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // para ver todo el mosaico
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // para ver 16 mosaicos

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // para ver todo el mosaico
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // para ver 16 mosaicos
```

## Ejemplo con múltiples capas

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // para ver todo el mosaico
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // para ver 4 mosaicos
```
