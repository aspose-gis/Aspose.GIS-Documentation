---
title: "Diagrama de Voronoi"
type: docs
url: /pt/net/geo-tools/voronoi-diagram/
description: "Como trabalhar com o Diagrama de Voronoi usando a biblioteca Aspose.GIS"
weight: 70
---

# Diagrama de Voronoi

Um Diagrama de Voronoi é uma partição simples do plano: dado um conjunto de n pontos (frequentemente referidos como sítios) você quer criar n regiões do plano, uma para cada ponto. Essas regiões são formadas de tal forma que para cada sítio, qualquer ponto dentro de sua região seja mais próximo desse sítio do que qualquer outro sítio.

GeoTools tem um método chamado "MakeVoronoiGraph" para construir um diagrama de Voronoi para uma coleção de pontos. Precisamos definir três ou mais pontos, então obtemos um retângulo (calculando o mínimo e o máximo das coordenadas "x" e "y" para todos os pontos) para restringir nosso plano. Como resultado, obtemos uma coleção de arestas formando o diagrama de Voronoi restrito pelo nosso retângulo.

Então, GeoTools tem um método chamado "BuildCenterline" (que é baseado no Diagrama de Voronoi) para obter a linha central para um polígono. Precisamos definir um polígono (ou uma coleção de pontos) que pode ter anéis internos. Aqui, como resultado, obtemos uma coleção de arestas formando o diagrama de Voronoi restrito pelo polígono de entrada. Esta é a principal diferença entre os métodos "MakeVoronoiGraph" e "BuildCenterline". Além disso, podemos definir uma coleção de pontos; neste caso, construímos um polígono por esses pontos. Em alguns casos, podemos construir um polígono de maneiras diferentes, então para mais precisão, é melhor definir o polígono.

E então, GeoTools tem um método chamado "GetCenterlineLength" para obter o comprimento da linha central. Este é a soma de todas as arestas da linha central. Aqui precisamos definir um polígono (ou uma coleção de pontos) que pode ter anéis internos.

## Criar Gráfico de Voronoi para 3 pontos

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Gráfico de Voronoi para 3 pontos](rightTriangle.map.png)

## Criar Gráfico de Voronoi para 6 pontos

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Gráfico de Voronoi para 6 pontos](test3.map.png)

## Criar Gráfico de Voronoi para 2000 pontos aleatórios

```csharp
List<Point> sites = new List<Point>();
var extent = new Extent(0, 0, 4000, 4000);
var points = GeoGenerator.ProducePoints(extent, new PointGeneratorOptions{ Count = 2000, Seed = 1 });
foreach (Point point in points)
{ 
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Gráfico de Voronoi para 2000 pontos](test8.map.png)

## Construir Linha Central e Obter Comprimento da Linha Central para um polígono de triângulo retângulo

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};
Polygon polygon = new Polygon(new LinearRing(sites));
polygon = Gis.GeoTools.GeometryOperations.CloseLinearRing(polygon) as Polygon;

var edges = Gis.GeoTools.GeometryOperations.BuildCenterline(polygon);

var length = Gis.GeoTools.GeometryOperations.GetCenterlineLength(polygon);
```
![Polígono de triângulo retângulo](rightTriangle_p.map.png)

## Construir Linha Central para um polígono quadrado com anel interno

```csharp
List<Point> exteriorSites = new List<Point>
{
    new Point(0, 300),
    new Point(300, 300),
    new Point(300, 0),
    new Point(0, 0)
};
Polygon polygon = new Polygon(new LinearRing(exteriorSites));
List<Point> interiorSites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 100),
    new Point(200, 200),
    new Point(100, 200)
};
polygon.AddInteriorRing(new LinearRing(interiorSites));
polygon = Gis.GeoTools.GeometryOperations.CloseLinearRing(polygon) as Polygon;

var edges = Gis.GeoTools.GeometryOperations.BuildCenterline(polygon);
```
![Polígono Quadrado](square_p_2.map.png)

## Construir Linha Central e Obter Comprimento da Linha Central para 6 pontos

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
     sites.Add(point);
}

var edges = Gis.GeoTools.GeometryOperations.BuildCenterline(sites);
var length = Gis.GeoTools.GeometryOperations.GetCenterlineLength(sites);
```
![Linha Central para 6 pontos](test3_c.map.png)
