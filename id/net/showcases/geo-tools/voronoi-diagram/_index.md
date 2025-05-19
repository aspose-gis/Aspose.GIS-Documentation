---
title: "Diagram Voronoi"
type: docs
url: /id/net/geo-tools/voronoi-diagram/
description: "Cara bekerja dengan Diagram Voronoi menggunakan library Aspose.GIS"
weight: 70
---

# Diagram Voronoi

Diagram Voronoi adalah partisi sederhana dari bidang: diberikan sekumpulan n titik (sering disebut sebagai situs) Anda ingin membuat n wilayah bidang, satu untuk setiap titik. Wilayah-wilayah tersebut terbentuk sedemikian rupa sehingga untuk setiap situs, setiap titik di dalam wilayahnya paling dekat dengan situs itu daripada situs lainnya.

GeoTools memiliki metode bernama "MakeVoronoiGraph" untuk membangun diagram Voronoi untuk kumpulan titik. Kita perlu mengatur tiga atau lebih titik, lalu kita mendapatkan persegi panjang (menghitung minimum dan maksimum dari koordinat "x" dan "y" untuk semua titik) untuk membatasi bidang kita. Sebagai hasilnya, kita mendapatkan koleksi tepi yang membentuk diagram Voronoi dibatasi oleh persegi panjang kita.

Kemudian, GeoTools memiliki metode bernama "BuildCenterline" (yang didasarkan pada Diagram Voronoi) untuk mendapatkan garis tengah untuk poligon. Kita perlu mengatur poligon (atau kumpulan titik) yang dapat dengan cincin interior. Di sini, sebagai hasilnya, kita mendapatkan koleksi tepi yang membentuk diagram Voronoi dibatasi oleh poligon input. Ini adalah perbedaan utama antara metode "MakeVoronoiGraph" dan "BuildCenterline". Selain itu, kita dapat mengatur kumpulan titik; dalam kasus ini, kita membangun poligon dengan titik-titik ini. Dalam beberapa kasus, kita dapat membangun poligon dengan cara yang berbeda, jadi untuk akurasi lebih tinggi, sebaiknya atur poligon tersebut.

Dan kemudian, GeoTools memiliki metode bernama "GetCenterlineLength" untuk mendapatkan panjang garis tengah. Ini adalah jumlah dari semua tepi garis tengah. Di sini kita perlu mengatur poligon (atau kumpulan titik) yang dapat dengan cincin interior.

## Buat Grafik Voronoi untuk 3 titik

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Grafik Voronoi untuk 3 titik](rightTriangle.map.png)

## Buat Grafik Voronoi untuk 6 titik

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Grafik Voronoi untuk 6 titik](test3.map.png)

## Buat Grafik Voronoi untuk 2000 titik acak

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
![Grafik Voronoi untuk 2000 titik](test8.map.png)

## Bangun Garis Tengah dan Dapatkan Panjang Garis Tengah untuk poligon segitiga siku-siku

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
![Poligon segitiga siku-siku](rightTriangle_p.map.png)

## Bangun Garis Tengah untuk poligon persegi dengan cincin interior

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
![Poligon Persegi](square_p_2.map.png)

## Bangun Garis Tengah dan Dapatkan Panjang Garis Tengah untuk 6 titik

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
![Garis tengah untuk 6 titik](test3_c.map.png)
