---
title: "نمودار ورونوی"
type: docs
url: /fa/net/geo-tools/voronoi-diagram/
description: "نحوه کار با نمودار ورونوی با استفاده از کتابخانه Aspose.GIS"
weight: 70
---

# نمودار ورونوی

نمودار ورونوی یک تقسیم بندی ساده از صفحه است: با توجه به مجموعه ای از n نقطه (که اغلب به عنوان سایت ها شناخته می شوند) می خواهید n منطقه از صفحه ایجاد کنید، یکی برای هر نقطه. این مناطق به گونه ای تشکیل شده اند که برای هر سایت، هر نقطه داخل منطقه آن نزدیکتر به آن سایت نسبت به هر سایت دیگر باشد.

GeoTools روشی به نام "MakeVoronoiGraph" دارد تا یک نمودار ورونوی را برای مجموعه ای از نقاط ایجاد کند. ما باید سه یا بیشتر نقطه تنظیم کنیم، سپس یک مستطیل دریافت می کنیم (با محاسبه حداقل و حداکثر مقادیر "x" و "y" برای همه نقاط) تا صفحه خود را محدود کنیم. در نتیجه، مجموعه ای از لبه ها تشکیل دهنده نمودار ورونوی محدود شده توسط مستطیل ما به دست می آوریم.

سپس GeoTools روشی به نام "BuildCenterline" (که بر اساس نمودار ورونوی است) برای دریافت خط مرکزی یک چند ضلعی دارد. ما باید یک چند ضلعی (یا مجموعه ای از نقاط) را تنظیم کنیم که می تواند دارای حلقه های داخلی باشد. در اینجا، در نتیجه، مجموعه ای از لبه ها تشکیل دهنده نمودار ورونوی محدود شده توسط چند ضلعی ورودی به دست می آوریم. این تفاوت اصلی بین روش های "MakeVoronoiGraph" و "BuildCenterline" است. همچنین، ما می توانیم یک مجموعه از نقاط را تنظیم کنیم؛ در این حالت، یک چند ضلعی با استفاده از این نقاط ایجاد می کنیم. در برخی موارد، می توانیم یک چند ضلعی را به روش های مختلفی بسازیم، بنابراین برای دقت بیشتر، بهتر است چند ضلعی را تنظیم کنیم.

و سپس GeoTools روشی به نام "GetCenterlineLength" دارد تا طول خط مرکزی را دریافت کند. این مجموع تمام لبه های خط مرکزی است. در اینجا ما باید یک چند ضلعی (یا مجموعه ای از نقاط) را تنظیم کنیم که می تواند دارای حلقه های داخلی باشد.

## ایجاد نمودار ورونوی برای 3 نقطه

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![نمودار ورونوی برای 3 نقطه](rightTriangle.map.png)

## ایجاد نمودار ورونوی برای 6 نقطه

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![نمودار ورونوی برای 6 نقطه](test3.map.png)

## ایجاد نمودار ورونوی برای 2000 نقطه تصادفی

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
![نمودار ورونوی برای 2000 نقطه](test8.map.png)

## ساخت خط مرکزی و دریافت طول خط مرکزی برای چند ضلعی مثلث قائم الزاویه

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
![چند ضلعی مثلث قائم الزاویه](rightTriangle_p.map.png)

## ساخت خط مرکزی برای چند ضلعی مربع با حلقه داخلی

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
![چند ضلعی مربع](square_p_2.map.png)

## ساخت خط مرکزی و دریافت طول خط مرکزی برای 6 نقطه

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
![خط مرکزی برای 6 نقطه](test3_c.map.png)
