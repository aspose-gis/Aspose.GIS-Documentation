---
title: "Диаграмма Вороного"
type: docs
url: /ru/net/geo-tools/voronoi-diagram/
description: "Как работать с диаграммой Вороного, используя библиотеку Aspose.GIS"
weight: 70
---

# Диаграмма Вороного

Диаграмма Вороного — это простое разделение плоскости: задан набор из n точек (часто называемых сайтами), и вы хотите создать n областей на плоскости, по одной для каждой точки. Эти области формируются таким образом, что для каждого сайта любая точка внутри его области ближе к этому сайту, чем к любому другому сайту.

GeoTools имеет метод под названием "MakeVoronoiGraph" для построения диаграммы Вороного для коллекции точек. Нам нужно установить три или более точек, затем мы получаем прямоугольник (вычисляя минимум и максимум координат "x" и "y" для всех точек), чтобы ограничить нашу плоскость. В результате мы получаем коллекцию ребер, образующих диаграмму Вороного, ограниченную нашим прямоугольником.

Затем GeoTools имеет метод под названием "BuildCenterline" (который основан на диаграмме Вороного) для получения центральной линии полигона. Нам нужно установить полигон (или коллекцию точек), который может иметь внутренние кольца. Здесь в результате мы получаем коллекцию ребер, образующих диаграмму Вороного, ограниченную входным полигоном. Это основное различие между методами "MakeVoronoiGraph" и "BuildCenterline". Также мы можем установить коллекцию точек; в этом случае мы строим полигон по этим точкам. В некоторых случаях мы можем построить полигон разными способами, поэтому для большей точности лучше указать полигон.

И затем GeoTools имеет метод под названием "GetCenterlineLength" для получения длины центральной линии. Это сумма всех ребер центральной линии. Здесь нам нужно установить полигон (или коллекцию точек), который может иметь внутренние кольца.

## Создание графа Вороного для 3 точек

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Граф Вороного для 3 точек](rightTriangle.map.png)

## Создание графа Вороного для 6 точек

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Граф Вороного для 6 точек](test3.map.png)

## Создание графа Вороного для 2000 случайных точек

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
![Граф Вороного для 2000 точек](test8.map.png)

## Построение центральной линии и получение длины центральной линии для полигона прямоугольного треугольника

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
![Полигон прямоугольного треугольника](rightTriangle_p.map.png)

## Построение центральной линии для квадратного полигона с внутренним кольцом

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
![Квадратный полигон](square_p_2.map.png)

## Построение центральной линии и получение длины центральной линии для 6 точек

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
![Центральная линия для 6 точек](test3_c.map.png)
