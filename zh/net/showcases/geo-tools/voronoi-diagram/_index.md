---
title: "Voronoi Diagram"
type: docs
url: /zh/net/geo-tools/voronoi-diagram/
description: "如何使用 Aspose.GIS 库处理 Voronoi 图"
weight: 70
---

# Voronoi Diagram

Voronoi 图是平面的简单划分：给定一组 n 个点（通常称为站点），您希望为每个点创建 n 个区域。这些区域的形成方式如下：对于每个站点，其区域内的任何点都比其他任何站点更接近该站点。

GeoTools 具有一种名为“MakeVoronoiGraph”的方法来构建一系列点的 Voronoi 图。我们需要设置三个或更多点，然后获得一个矩形（通过计算所有点的“x”和“y”坐标的最小值和最大值）来限制我们的平面。结果是，我们得到一组形成 Voronoi 图的边，该图受到我们的矩形的限制。

然后，GeoTools 具有一种名为“BuildCenterline”（基于 Voronoi 图）的方法来获取多边形的中心线。我们需要设置一个多边形（或一系列点），它可以包含内部环。在这里，结果是形成 Voronoi 图的边的集合，该图受到输入多边形的限制。这是“MakeVoronoiGraph”和“BuildCenterline”方法之间的主要区别。此外，我们可以设置一系列点；在这种情况下，我们通过这些点构建一个多边形。在某些情况下，我们可以以不同的方式构建多边形，因此为了更高的精度，最好设置多边形。

然后，GeoTools 具有一种名为“GetCenterlineLength”的方法来获取中心线长度。这是所有中心线边的总和。在这里，我们需要设置一个多边形（或一系列点），它可以包含内部环。

## 为 3 个点构建 Voronoi 图

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![为 3 个点构建 Voronoi 图](rightTriangle.map.png)

## 为 6 个点构建 Voronoi 图

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![为 6 个点构建 Voronoi 图](test3.map.png)

## 为 2000 个随机点构建 Voronoi 图

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
![为 2000 个点构建 Voronoi 图](test8.map.png)

## 为直角三角形多边形构建中心线并获取中心线长度

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
![直角三角形多边形](rightTriangle_p.map.png)

## 为具有内部环的方形多边形构建中心线

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
![方形多边形](square_p_2.map.png)

## 为 6 个点构建中心线并获取中心线长度

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
![6 个点的中心线](test3_c.map.png)
