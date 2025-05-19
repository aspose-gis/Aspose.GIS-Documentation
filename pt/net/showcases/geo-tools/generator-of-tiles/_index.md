---
title: "Gerador de Tiles"
type: docs
url: /pt/net/geo-tools/generator-of-tiles/
description: "Como gerar tiles de mapa"
weight: 70
---

# Gerador de tiles

O mapa de tile é a maneira mais popular de exibir e navegar em mapas. `GeneratorTiles` tem métodos para renderizar tiles para um mapa construído ou outros fins práticos.
Precisamos definir a camada (ou camadas) de entrada, o diretório de saída e o parâmetro de zoom. Se tivermos mais de uma camada, então para cada camada, juntamos as geometrias e criamos uma nova camada mesclada. Todos os tiles são criados no diretório de saída definido e têm o nome `tile_zxy_{z}_{x}_{y}`, onde `z` é o parâmetro de zoom, `x` e `y` são as coordenadas da extensão do canto superior esquerdo do tile. No nível de zoom "0", toda a camada será renderizada em um único tile de mapa. Cada nível de zoom dobra em ambas as dimensões, então um único tile é substituído por 4 tiles quando o zoom aumenta. Os tiles são salvos com a extensão "png".

## Exemplo com camada InMemory

```csharp
var layer = Drivers.InMemory.CreateLayer();

Feature feature_1 = layer.ConstructFeature();
feature_1.Geometry = Geometry.FromText("LINESTRING(0 0, 500 300)");
layer.Add(feature_1);

Feature feature_2 = layer.ConstructFeature();
feature_2.Geometry = Geometry.FromText("LINESTRING(0 300, 500 0)");
layer.Add(feature_2);

GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 0); // para ver o tile inteiro
GeneratorTiles.GenerateTiles(layer, OutDirectory, zoom: 1); // para ver 4 tiles
```

## Exemplo quando obtemos a camada de um arquivo GeoJson (ou outro)

```csharp
var layer_GeoJson = VectorLayer.Open(sourcePath, Drivers.GeoJson);
var layer_OsmXml = VectorLayer.Open(sourcePath, Drivers.OsmXml);

GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 0); // para ver o tile inteiro
GeneratorTiles.GenerateTiles(layer_GeoJson, OutDirectory, zoom: 2); // para ver 16 tiles

GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 0); // para ver o tile inteiro
GeneratorTiles.GenerateTiles(layer_OsmXml, OutDirectory, zoom: 2); // para ver 16 tiles
```

## Exemplo com múltiplas camadas

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

GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 0); // para ver o tile inteiro
GeneratorTiles.GenerateTiles(listLayers, OutDirectory, zoom: 1); // para ver 4 tiles
```
