---
title: "Diagramme de Voronoï"
type: docs
url: /fr/net/geo-tools/voronoi-diagram/
description: "Comment travailler avec le Diagramme de Voronoï en utilisant la bibliothèque Aspose.GIS"
weight: 70
---

# Diagramme de Voronoï

Un diagramme de Voronoï est un simple partitionnement du plan : étant donné un ensemble de n points (souvent appelés sites), vous souhaitez créer n régions du plan, une pour chaque point. Ces régions sont formées de telle sorte que pour chaque site, tout point à l'intérieur de sa région soit plus proche de ce site que de tout autre site.

GeoTools dispose d'une méthode appelée "MakeVoronoiGraph" pour construire un diagramme de Voronoï pour une collection de points. Nous devons définir trois points ou plus, puis nous obtenons un rectangle (calculant le minimum et le maximum des coordonnées "x" et "y" pour tous les points) afin de restreindre notre plan. En conséquence, nous obtenons une collection d'arêtes formant le diagramme de Voronoï limité par notre rectangle.

Ensuite, GeoTools dispose d'une méthode appelée "BuildCenterline" (qui est basée sur le diagramme de Voronoï) pour obtenir la ligne médiane d'un polygone. Nous devons définir un polygone (ou une collection de points) qui peut avoir des anneaux intérieurs. Ici, en conséquence, nous obtenons une collection d'arêtes formant le diagramme de Voronoï limité par le polygone d'entrée. C'est la principale différence entre les méthodes "MakeVoronoiGraph" et "BuildCenterline". De plus, nous pouvons définir une collection de points ; dans ce cas, nous construisons un polygone avec ces points. Dans certains cas, nous pouvons construire un polygone de différentes manières, donc pour plus de précision, il est préférable de définir le polygone.

Et puis, GeoTools dispose d'une méthode appelée "GetCenterlineLength" pour obtenir la longueur de la ligne médiane. Il s'agit de la somme de toutes les arêtes de la ligne médiane. Ici, nous devons définir un polygone (ou une collection de points) qui peut avoir des anneaux intérieurs.

## Créer un graphe de Voronoï pour 3 points

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Diagramme de Voronoï pour 3 points](rightTriangle.map.png)

## Créer un graphe de Voronoï pour 6 points

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Diagramme de Voronoï pour 6 points](test3.map.png)

## Créer un graphe de Voronoï pour 2000 points aléatoires

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
![Diagramme de Voronoï pour 2000 points](test8.map.png)

## Construire la ligne médiane et obtenir la longueur de la ligne médiane pour un polygone triangle rectangle

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
![Polygone triangle rectangle](rightTriangle_p.map.png)

## Construire la ligne médiane pour un polygone carré avec anneau intérieur

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
![Polygone carré](square_p_2.map.png)

## Construire la ligne médiane et obtenir la longueur de la ligne médiane pour 6 points

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
![Ligne médiane pour 6 points](test3_c.map.png)
