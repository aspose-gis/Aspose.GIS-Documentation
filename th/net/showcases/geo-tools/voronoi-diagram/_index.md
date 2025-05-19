---
title: "แผนภาพ Voronoi"
type: docs
url: /th/net/geo-tools/voronoi-diagram/
description: "วิธีการทำงานกับแผนภาพ Voronoi โดยใช้ไลบรารี Aspose.GIS"
weight: 70
---

# แผนภาพ Voronoi

แผนภาพ Voronoi คือการแบ่งระนาบอย่างง่ายๆ: กำหนดชุดของจุด n จุด (มักเรียกว่าไซต์) คุณต้องการสร้างภูมิภาค n ภูมิภาคของระนาบ โดยแต่ละภูมิภาคเป็นของแต่ละจุด ภูมิภาคเหล่านี้ถูกสร้างขึ้นเพื่อให้สำหรับแต่ละไซต์ จุดใดๆ ภายในภูมิภาคของมันจะอยู่ใกล้กับไซต์นั้นมากกว่าไซต์อื่นๆ

GeoTools มีวิธีการที่เรียกว่า "MakeVoronoiGraph" เพื่อสร้างแผนภาพ Voronoi สำหรับชุดของจุด เราต้องตั้งค่าสามหรือมากกว่าจุด จากนั้นเราจะได้สี่เหลี่ยมผืนผ้า (คำนวณค่าต่ำสุดและสูงสุดของพิกัด "x" และ "y" สำหรับทุกจุด) เพื่อจำกัดระนาบของเรา เป็นผลให้เราได้ชุดของเส้นที่สร้างแผนภาพ Voronoi ที่ถูกจำกัดโดยสี่เหลี่ยมผืนผ้าของเรา

จากนั้น GeoTools มีวิธีการที่เรียกว่า "BuildCenterline" (ซึ่งอิงตามแผนภาพ Voronoi) เพื่อรับเส้นกลางสำหรับรูปหลายเหลี่ยม เราต้องตั้งค่ารูปหลายเหลี่ยม (หรือชุดของจุด) ซึ่งสามารถมีวงแหวนภายในได้ ที่นี่เป็นผลให้เราได้รับชุดของเส้นที่สร้างแผนภาพ Voronoi ที่ถูกจำกัดโดยรูปหลายเหลี่ยมอินพุต นี่คือความแตกต่างหลักระหว่างวิธีการ "MakeVoronoiGraph" และ "BuildCenterline" นอกจากนี้ เรายังสามารถตั้งค่าชุดของจุด ในกรณีนี้ เราสร้างรูปหลายเหลี่ยมด้วยจุดเหล่านี้ ในบางกรณี เราสามารถสร้างรูปหลายเหลี่ยมในรูปแบบต่างๆ ดังนั้นเพื่อให้มีความแม่นยำมากขึ้น จึงเป็นการดีกว่าที่จะตั้งค่ารูปหลายเหลี่ยม

และจากนั้น GeoTools มีวิธีการที่เรียกว่า "GetCenterlineLength" เพื่อรับความยาวของเส้นกลาง นี่คือผลรวมของเส้นขอบทั้งหมดของเส้นกลาง ที่นี่เราต้องตั้งค่ารูปหลายเหลี่ยม (หรือชุดของจุด) ซึ่งสามารถมีวงแหวนภายในได้

## สร้างกราฟ Voronoi สำหรับ 3 จุด

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![กราฟ Voronoi สำหรับ 3 จุด](rightTriangle.map.png)

## สร้างกราฟ Voronoi สำหรับ 6 จุด

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![กราฟ Voronoi สำหรับ 6 จุด](test3.map.png)

## สร้างกราฟ Voronoi สำหรับจุดสุ่ม 2000 จุด

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
![กราฟ Voronoi สำหรับจุด 2000 จุด](test8.map.png)

## สร้างเส้นกลางและรับความยาวของเส้นกลางสำหรับรูปสามเหลี่ยมมุมฉาก

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
![รูปสามเหลี่ยมมุมฉาก](rightTriangle_p.map.png)

## สร้างเส้นกลางสำหรับรูปหลายเหลี่ยมสี่เหลี่ยมจัตุรัสที่มีวงแหวนภายใน

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
![รูปหลายเหลี่ยมสี่เหลี่ยมจัตุรัส](square_p_2.map.png)

## สร้างเส้นกลางและรับความยาวของเส้นกลางสำหรับ 6 จุด

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
![เส้นกลางสำหรับ 6 จุด](test3_c.map.png)
