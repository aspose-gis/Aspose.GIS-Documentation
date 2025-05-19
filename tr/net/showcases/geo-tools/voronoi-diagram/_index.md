---
title: "Voronoi Diyagramı"
type: docs
url: /tr/net/geo-tools/voronoi-diagram/
description: "Aspose.GIS kütüphanesini kullanarak Voronoi Diyagramı ile nasıl çalışacağınız"
weight: 70
---

# Voronoi Diyagramı

Bir Voronoi Diyagramı, düzlemin basit bir bölümlemesidir: verilen n nokta kümesi (genellikle siteler olarak adlandırılır) için her nokta için düzlemde n bölge oluşturmak istersiniz. Bu bölgeler öyle oluşur ki, her site için o bölgedeki herhangi bir nokta diğer hiçbir siteden daha çok o siteye yakındır.

GeoTools'un, bir nokta koleksiyonu için Voronoi diyagramı oluşturmak için "MakeVoronoiGraph" adlı bir yöntemi vardır. Üç veya daha fazla nokta ayarlamamız gerekir, ardından düzlemimizi kısıtlamak için (tüm noktalar için "x" ve "y" koordinatlarının minimum ve maksimum değerlerini hesaplayarak) bir dikdörtgen elde ederiz. Sonuç olarak, dikdörtgenimizle sınırlı Voronoi diyagramını oluşturan kenar koleksiyonu elde ederiz.

Daha sonra GeoTools'un, bir poligon için merkez hattını almak için "BuildCenterline" (Voronoi Diyagramına dayalı) adlı bir yöntemi vardır. İç halkaları olan bir poligon (veya nokta koleksiyonu) ayarlamamız gerekir. Burada sonuç olarak girdi poligonuyla sınırlı Voronoi diyagramını oluşturan kenar koleksiyonunu elde ederiz. Bu, "MakeVoronoiGraph" ve "BuildCenterline" yöntemleri arasındaki temel farktır. Ayrıca, bir nokta koleksiyonu ayarlayabiliriz; bu durumda bu noktalardan bir poligon oluştururuz. Bazı durumlarda, bir poligon farklı şekillerde oluşturabiliriz, bu nedenle daha fazla doğruluk için poligonun ayarlanması daha iyidir.

Ve sonra GeoTools'un merkez hat uzunluğunu almak için "GetCenterlineLength" adlı bir yöntemi vardır. Bu, tüm merkez hattı kenarlarının toplamıdır. İç halkaları olan bir poligon (veya nokta koleksiyonu) ayarlamamız gerekir.

## 3 nokta için Voronoi Grafiği Oluşturma

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![3 nokta için Voronoi Grafiği](rightTriangle.map.png)

## 6 nokta için Voronoi Grafiği Oluşturma

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![6 nokta için Voronoi Grafiği](test3.map.png)

## 2000 rastgele nokta için Voronoi Grafiği Oluşturma

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
![2000 nokta için Voronoi Grafiği](test8.map.png)

## Dik açılı üçgen poligonu için Merkez Hattı Oluşturma ve Merkez Hattı Uzunluğunu Alma

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
![Dik açılı üçgen poligonu](rightTriangle_p.map.png)

## İç halkalı kare poligon için Merkez Hattı Oluşturma

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
![Kare Poligon](square_p_2.map.png)

## 6 nokta için Merkez Hattı Oluşturma ve Merkez Hattı Uzunluğunu Alma

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
![6 nokta için Merkez Hattı](test3_c.map.png)
