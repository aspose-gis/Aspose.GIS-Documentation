---
title: "דיאגרמת Voronoi"
type: docs
url: /he/net/geo-tools/voronoi-diagram/
description: "כיצד לעבוד עם דיאגרמת Voronoi באמצעות ספריית Aspose.GIS"
weight: 70
---

# דיאגרמת Voronoi

דיאגרמת Voronoi היא חלוקה פשוטה של המישור: בהינתן קבוצה של n נקודות (המכונות לעתים קרובות אתרים) ברצונך ליצור n אזורים של המישור, אחד לכל נקודה. האזורים הללו נוצרים כך שלכל אתר, כל נקודה בתוך האזור שלה קרובה יותר לאתר הזה מכל אתר אחר.

ל-GeoTools יש שיטה בשם "MakeVoronoiGraph" לבניית דיאגרמת Voronoi עבור אוסף של נקודות. עלינו להגדיר שלושה נקודות לפחות, ואז אנו מקבלים מלבן (חישוב המינימום והמקסימום של קואורדינטות "x" ו-"y" לכל הנקודות) כדי להגביל את המישור שלנו. כתוצאה מכך, אנו מקבלים אוסף של צלעות היוצרות את דיאגרמת Voronoi המוגבלת על ידי המלבן שלנו.

לאחר מכן, ל-GeoTools יש שיטה בשם "BuildCenterline" (המבוססת על דיאגרמת Voronoi) כדי לקבל את קו האמצע עבור מצולע. עלינו להגדיר מצולע (או אוסף של נקודות) שיכול להיות עם טבעות פנימיות. כאן, כתוצאה מכך, אנו מקבלים אוסף של צלעות היוצרות את דיאגרמת Voronoi המוגבלת על ידי המצולע הקלט. זהו ההבדל העיקרי בין השיטות "MakeVoronoiGraph" ו-"BuildCenterline". כמו כן, אנו יכולים להגדיר אוסף של נקודות; במקרה זה, אנו בונים מצולע על ידי הנקודות הללו. במקרים מסוימים, אנו יכולים לבנות מצולע בדרכים שונות, ולכן לדיוק רב יותר, עדיף להגדיר את המצולע.

ואז ל-GeoTools יש שיטה בשם "GetCenterlineLength" כדי לקבל את אורך קו האמצע. זהו סכום כל צלעות קו האמצע. כאן עלינו להגדיר מצולע (או אוסף של נקודות) שיכול להיות עם טבעות פנימיות.

## בניית גרף Voronoi עבור 3 נקודות

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![דיאגרמת Voronoi עבור 3 נקודות](rightTriangle.map.png)

## בניית גרף Voronoi עבור 6 נקודות

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![דיאגרמת Voronoi עבור 6 נקודות](test3.map.png)

## בניית גרף Voronoi עבור 2000 נקודות אקראיות

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
![דיאגרמת Voronoi עבור 2000 נקודות](test8.map.png)

## בניית קו אמצע וקבלת אורך קו האמצע למצולע משולש ימני

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
![מצולע משולש ימני](rightTriangle_p.map.png)

## בניית קו אמצע למצולע ריבוע עם טבעת פנימית

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
![מצולע ריבוע](square_p_2.map.png)

## בניית קו אמצע וקבלת אורך קו האמצע עבור 6 נקודות

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
![קו אמצע עבור 6 נקודות](test3_c.map.png)
