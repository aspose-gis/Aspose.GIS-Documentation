---
title: "보로노이 다이어그램"
type: docs
url: /ko/net/geo-tools/voronoi-diagram/
description: "Aspose.GIS 라이브러리를 사용하여 보로노이 다이어그램을 작업하는 방법"
weight: 70
---

# 보로노이 다이어그램

보로노이 다이어그램은 평면의 간단한 분할입니다. 주어진 n개의 점(종종 사이트라고 함)에 대해 각 점에 대해 n개의 영역을 만들고 싶습니다. 이러한 영역은 다음과 같이 형성됩니다. 각 사이트에 대해 해당 영역 내의 모든 점은 다른 사이트보다 해당 사이트에 더 가깝습니다.

GeoTools에는 포인트 컬렉션에 대한 보로노이 다이어그램을 구축하는 "MakeVoronoiGraph"라는 메서드가 있습니다. 세 개 이상의 포인트를 설정해야 하면 "x" 및 "y" 좌표의 최소값과 최대값을 계산하여 모든 포인트에 대해 평면을 제한하는 사각형을 얻습니다. 결과적으로 사각형으로 제한된 보로노이 다이어그램을 형성하는 일련의 에지가 생성됩니다.

그런 다음 GeoTools에는 보로노이 다이어그램을 기반으로 폴리곤의 중심선을 가져오는 "BuildCenterline"이라는 메서드가 있습니다. 내부 링이 있는 폴리곤(또는 포인트 컬렉션)을 설정해야 합니다. 여기서 결과적으로 입력 폴리곤으로 제한된 보로노이 다이어그램을 형성하는 일련의 에지가 생성됩니다. 이것은 "MakeVoronoiGraph"와 "BuildCenterline" 메서드 간의 주요 차이점입니다. 또한 포인트 컬렉션을 설정할 수도 있습니다. 이 경우 이러한 포인트를 사용하여 폴리곤을 구축합니다. 어떤 경우에는 다른 방식으로 폴리곤을 구축 할 수 있으므로 더 정확하게하려면 폴리곤을 설정하는 것이 좋습니다.

그리고 GeoTools에는 중심선 길이를 가져오는 "GetCenterlineLength"라는 메서드가 있습니다. 이것은 모든 중심선 에지의 합입니다. 여기에서 내부 링이 있는 폴리곤(또는 포인트 컬렉션)을 설정해야 합니다.

## 3개의 점에 대한 보로노이 그래프 만들기

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![3개의 점에 대한 보로노이 그래프](rightTriangle.map.png)

## 6개의 점에 대한 보로노이 그래프 만들기

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![6개의 점에 대한 보로노이 그래프](test3.map.png)

## 2000개의 랜덤 포인트에 대한 보로노이 그래프 만들기

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
![2000개의 점에 대한 보로노이 그래프](test8.map.png)

## 직각 삼각형 폴리곤의 중심선 구축 및 중심선 길이 가져오기

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
![직각 삼각형 폴리곤](rightTriangle_p.map.png)

## 내부 링이 있는 정사각형 폴리곤의 중심선 구축

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
![정사각형 폴리곤](square_p_2.map.png)

## 6개의 점에 대한 중심선 구축 및 중심선 길이 가져오기

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
![6개의 점에 대한 중심선](test3_c.map.png)
