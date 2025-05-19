---
title: "ボロノイ図"
type: docs
url: /ja/net/geo-tools/voronoi-diagram/
description: "Aspose.GISライブラリを使用してボロノイ図を操作する方法"
weight: 70
---

# ボロノイ図

ボロノイ図は、平面の単純な分割です。一連のn個の点（しばしば「サイト」と呼ばれる）が与えられた場合、各点に対して平面のn個の領域を作成したいと考えています。これらの領域は、各サイトについて、その領域内の任意の点は他のどのサイトよりもそのサイトに最も近いように形成されます。

GeoToolsには、「MakeVoronoiGraph」というメソッドがあり、一連の点のボロノイ図を構築できます。3つ以上のポイントを設定する必要があります。次に、すべてのポイントの「x」および「y」座標の最小値と最大値を計算して長方形を取得し、平面を制限します。その結果、長方形によって制限されたボロノイ図を形成するエッジのコレクションが得られます。

次に、GeoToolsには、「BuildCenterline」（ボロノイ図に基づく）というメソッドがあり、ポリゴンの中心線を取得できます。内部リングを持つことができるポリゴン（またはポイントのコレクション）を設定する必要があります。ここで、結果として得られるのは、入力ポリゴンによって制限されたボロノイ図を形成するエッジのコレクションです。「MakeVoronoiGraph」と「BuildCenterline」メソッド間の主な違いはこれです。また、ポイントのコレクションを設定することもできます。この場合、これらのポイントでポリゴンを構築します。場合によっては、異なる方法でポリゴンを構築できるため、より正確にするためにポリゴンを設定する方が良いでしょう。

そして次に、GeoToolsには中心線の長さを取得するための「GetCenterlineLength」というメソッドがあります。これはすべての中心線エッジの合計です。内部リングを持つことができるポリゴン（またはポイントのコレクション）を設定する必要があります。

## 3つのポイントに対するボロノイグラフを作成する

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![3つのポイントに対するボロノイグラフ](rightTriangle.map.png)

## 6つのポイントに対するボロノイグラフを作成する

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![6つのポイントに対するボロノイグラフ](test3.map.png)

## 2000個のランダムなポイントに対するボロノイグラフを作成する

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
![2000個のポイントに対するボロノイグラフ](test8.map.png)

## 直角三角形ポリゴンの中心線を作成し、中心線の長さを取得する

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
![直角三角形ポリゴン](rightTriangle_p.map.png)

## 内部リングを持つ正方形ポリゴンの中心線を作成する

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
![正方形ポリゴン](square_p_2.map.png)

## 6つのポイントに対する中心線を作成し、中心線の長さを取得する

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
![6つのポイントに対する中心線](test3_c.map.png)
