---
title: "Diagram Voronoi"
type: docs
url: /pl/net/geo-tools/voronoi-diagram/
description: "Jak pracować z Diagramem Voronoi używając biblioteki Aspose.GIS"
weight: 70
---

# Diagram Voronoi

Diagram Voronoi to proste podział płaszczyzny: mając zestaw n punktów (często nazywanych witrynami), chcesz utworzyć n regionów na płaszczyźnie, jeden dla każdego punktu. Te regiony są tworzone tak, że dla każdej witryny dowolny punkt w jej regionie jest bliższy tej witrynie niż jakiejkolwiek innej witrynie.

GeoTools ma metodę o nazwie "MakeVoronoiGraph" do zbudowania diagramu Voronoi dla zbioru punktów. Musimy ustawić trzy lub więcej punktów, a następnie otrzymujemy prostokąt (obliczając minimum i maksimum współrzędnych „x” i „y” dla wszystkich punktów), aby ograniczyć naszą płaszczyznę. W rezultacie otrzymujemy zbiór krawędzi tworzących diagram Voronoi ograniczony naszym prostokątem.

Następnie GeoTools ma metodę o nazwie "BuildCenterline" (która jest oparta na Diagramie Voronoi), aby uzyskać linię środkową dla wielokąta. Musimy ustawić wielokąt (lub zbiór punktów), który może mieć wewnętrzne pierścienie. Tutaj, w wyniku, otrzymujemy zbiór krawędzi tworzących diagram Voronoi ograniczony przez wprowadzony wielokąt. To jest główna różnica między metodami "MakeVoronoiGraph" i "BuildCenterline". Możemy również ustawić zbiór punktów; w tym przypadku budujemy wielokąt za pomocą tych punktów. W niektórych przypadkach możemy zbudować wielokąt na różne sposoby, więc dla większej dokładności lepiej jest ustawić wielokąt.

A następnie GeoTools ma metodę o nazwie "GetCenterlineLength" do uzyskania długości linii środkowej. Jest to suma wszystkich krawędzi linii środkowej. Tutaj musimy ustawić wielokąt (lub zbiór punktów), który może mieć wewnętrzne pierścienie.

## Utwórz Diagram Voronoi dla 3 punktów

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Diagram Voronoi dla 3 punktów](rightTriangle.map.png)

## Utwórz Diagram Voronoi dla 6 punktów

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Diagram Voronoi dla 6 punktów](test3.map.png)

## Utwórz Diagram Voronoi dla 2000 losowych punktów

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
![Diagram Voronoi dla 2000 punktów](test8.map.png)

## Zbuduj Linię Środkową i Oblicz Długość Linii Środkowej dla wielokąta trójkąta prostego

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
![Wielokąt trójkąta prostego](rightTriangle_p.map.png)

## Zbuduj Linię Środkową dla wielokąta kwadratu z pierścieniem wewnętrznym

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
![Wielokąt kwadratu](square_p_2.map.png)

## Zbuduj Linię Środkową i Oblicz Długość Linii Środkowej dla 6 punktów

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
![Linia środkowa dla 6 punktów](test3_c.map.png)
