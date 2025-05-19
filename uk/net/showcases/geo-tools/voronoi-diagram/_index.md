---
title: "Діаграма Вороного"
type: docs
url: /uk/net/geo-tools/voronoi-diagram/
description: "Як працювати з Діаграмою Вороного, використовуючи бібліотеку Aspose.GIS"
weight: 70
---

# Діаграма Вороного

Діаграма Вороного - це просте розділення площини: задано набір n точок (часто їх називають сайтами), ви хочете створити n регіонів площини, один для кожної точки. Ці регіони утворюються таким чином, щоб для кожного сайту будь-яка точка всередині його регіону була ближчою до цього сайту, ніж будь-який інший сайт.

GeoTools має метод під назвою "MakeVoronoiGraph" для побудови діаграми Вороного для набору точок. Нам потрібно задати три або більше точок, а потім ми отримаємо прямокутник (обчислюючи мінімум і максимум координат "x" та "y" для всіх точок), щоб обмежити нашу площину. В результаті ми отримуємо колекцію ребер, що утворюють діаграму Вороного, обмежену нашим прямокутником.

Потім GeoTools має метод під назвою "BuildCenterline" (який базується на Діаграмі Вороного), щоб отримати центральну лінію для полігону. Нам потрібно задати полігон (або колекцію точок), який може мати внутрішні кільця. Тут, в результаті, ми отримуємо колекцію ребер, що утворюють діаграму Вороного, обмежену вхідним полігоном. Це основна відмінність між методами "MakeVoronoiGraph" та "BuildCenterline". Також ми можемо задати колекцію точок; у цьому випадку ми будуємо полігон за цими точками. У деяких випадках ми можемо побудувати полігон різними способами, тому для більшої точності краще задати полігон.

І потім GeoTools має метод під назвою "GetCenterlineLength" для отримання довжини центральної лінії. Це сума всіх ребер центральної лінії. Тут нам потрібно задати полігон (або колекцію точок), який може мати внутрішні кільця.

## Побудова діаграми Вороного для 3 точок

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Діаграма Вороного для 3 точок](rightTriangle.map.png)

## Побудова діаграми Вороного для 6 точок

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Діаграма Вороного для 6 точок](test3.map.png)

## Побудова діаграми Вороного для 2000 випадкових точок

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
![Діаграма Вороного для 2000 точок](test8.map.png)

## Побудова центральної лінії та отримання довжини центральної лінії для полігону прямокутного трикутника

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
![Полігон прямокутного трикутника](rightTriangle_p.map.png)

## Побудова центральної лінії для квадратного полігону з внутрішнім кільцем

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
![Квадратний полігон](square_p_2.map.png)

## Побудова центральної лінії та отримання довжини центральної лінії для 6 точок

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
![Центральна лінія для 6 точок](test3_c.map.png)
