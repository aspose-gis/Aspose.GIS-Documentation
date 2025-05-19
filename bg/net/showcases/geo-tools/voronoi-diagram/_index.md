---
title: "Диаграма на Вороной"
type: docs
url: /bg/net/geo-tools/voronoi-diagram/
description: "Как да работите с Диаграма на Вороной, използвайки библиотеката Aspose.GIS"
weight: 70
---

# Диаграма на Вороной

Диаграмата на Вороной е просто разделяне на равнината: като се има предвид набор от n точки (често наричани сайтове), искате да създадете n области на равнината, по една за всяка точка. Тези области са формирани така, че за всеки сайт всяка точка вътре в неговата област е по-близо до този сайт, отколкото до който и да е друг сайт.

GeoTools има метод, наречен "MakeVoronoiGraph", за изграждане на диаграма на Вороной за колекция от точки. Трябва да зададем три или повече точки, след което получаваме правоъгълник (изчислявайки минимума и максимума на координатите "x" и "y" за всички точки), за да ограничим равнината си. В резултат получаваме колекция от ръбове, образуващи диаграмата на Вороной, ограничена от нашия правоъгълник.

След това GeoTools има метод, наречен "BuildCenterline" (който се основава на Диаграмата на Вороной), за да получи средната линия за многоъгълник. Трябва да зададем многоъгълник (или колекция от точки), който може да бъде с вътрешни пръстени. Тук, в резултат, получаваме колекция от ръбове, образуващи диаграмата на Вороной, ограничена от входния многоъгълник. Това е основната разлика между методите "MakeVoronoiGraph" и "BuildCenterline". Освен това можем да зададем колекция от точки; в този случай изграждаме многоъгълник по тези точки. В някои случаи можем да изградим многоъгълник по различни начини, така че за по-голяма точност е по-добре да зададем многоъгълника.

И след това GeoTools има метод, наречен "GetCenterlineLength", за да получи дължината на средната линия. Това е сумата от всички ръбове на средната линия. Тук трябва да зададем многоъгълник (или колекция от точки), който може да бъде с вътрешни пръстени.

## Създаване на Voronoi Graph за 3 точки

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Voronoi Graph за 3 точки](rightTriangle.map.png)

## Създаване на Voronoi Graph за 6 точки

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Voronoi Graph за 6 точки](test3.map.png)

## Създаване на Voronoi Graph за 2000 случайни точки

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
![Voronoi Graph за 2000 точки](test8.map.png)

## Изграждане на средна линия и получаване на дължината на средната линия за правоъгълен триъгълник многоъгълник

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
![Правоъгълен триъгълник многоъгълник](rightTriangle_p.map.png)

## Изграждане на средна линия за квадратен многоъгълник с вътрешен пръстен

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
![Квадратен многоъгълник](square_p_2.map.png)

## Изграждане на средна линия и получаване на дължината на средната линия за 6 точки

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
![Средна линия за 6 точки](test3_c.map.png)
