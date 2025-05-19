---
title: "Biểu đồ Voronoi"
type: docs
url: /vi/net/geo-tools/voronoi-diagram/
description: "Cách làm việc với Biểu đồ Voronoi bằng thư viện Aspose.GIS"
weight: 70
---

# Biểu đồ Voronoi

Một Biểu đồ Voronoi là một phân vùng đơn giản của mặt phẳng: cho một tập hợp n điểm (thường được gọi là các trang web), bạn muốn tạo ra n vùng của mặt phẳng, mỗi vùng tương ứng với một điểm. Các vùng này được hình thành sao cho đối với mỗi trang web, bất kỳ điểm nào bên trong vùng của nó đều gần trang web đó hơn bất kỳ trang web nào khác.

GeoTools có một phương thức gọi là "MakeVoronoiGraph" để xây dựng một biểu đồ Voronoi cho một tập hợp các điểm. Chúng ta cần đặt ba hoặc nhiều điểm, sau đó chúng ta nhận được một hình chữ nhật (tính toán giá trị tối thiểu và tối đa của tọa độ "x" và "y" cho tất cả các điểm) để giới hạn mặt phẳng của chúng ta. Kết quả là, chúng ta nhận được một tập hợp các cạnh tạo thành biểu đồ Voronoi bị giới hạn bởi hình chữ nhật của chúng ta.

Sau đó, GeoTools có một phương thức gọi là "BuildCenterline" (dựa trên Biểu đồ Voronoi) để lấy đường trung tâm cho một đa giác. Chúng ta cần đặt một đa giác (hoặc một tập hợp các điểm) có thể có các vòng bên trong. Tại đây, kết quả là chúng ta nhận được một tập hợp các cạnh tạo thành biểu đồ Voronoi bị giới hạn bởi đa giác đầu vào. Đây là sự khác biệt chính giữa các phương thức "MakeVoronoiGraph" và "BuildCenterline". Ngoài ra, chúng ta có thể đặt một tập hợp các điểm; trong trường hợp này, chúng ta xây dựng một đa giác bằng các điểm này. Trong một số trường hợp, chúng ta có thể xây dựng một đa giác theo những cách khác nhau, vì vậy để có độ chính xác cao hơn, tốt hơn là đặt đa giác.

Và sau đó, GeoTools có một phương thức gọi là "GetCenterlineLength" để lấy chiều dài đường trung tâm. Đây là tổng của tất cả các cạnh đường trung tâm. Tại đây chúng ta cần đặt một đa giác (hoặc một tập hợp các điểm) có thể có các vòng bên trong.

## Tạo Biểu đồ Voronoi cho 3 điểm

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Biểu đồ Voronoi cho 3 điểm](rightTriangle.map.png)

## Tạo Biểu đồ Voronoi cho 6 điểm

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Biểu đồ Voronoi cho 6 điểm](test3.map.png)

## Tạo Biểu đồ Voronoi cho 2000 điểm ngẫu nhiên

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
![Biểu đồ Voronoi cho 2000 điểm](test8.map.png)

## Xây dựng Đường trung tâm và Lấy Chiều dài Đường trung tâm cho đa giác tam giác vuông

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
![Đa giác tam giác vuông](rightTriangle_p.map.png)

## Xây dựng Đường trung tâm cho đa giác hình vuông có vòng bên trong

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
![Đa giác hình vuông](square_p_2.map.png)

## Xây dựng Đường trung tâm và Lấy Chiều dài Đường trung tâm cho 6 điểm

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
![Đường trung tâm cho 6 điểm](test3_c.map.png)
