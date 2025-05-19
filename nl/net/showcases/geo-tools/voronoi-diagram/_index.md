---
title: "Voronoi Diagram"
type: docs
url: /nl/net/geo-tools/voronoi-diagram/
description: "Hoe om te werken met Voronoi Diagram met behulp van de Aspose.GIS bibliotheek"
weight: 70
---

# Voronoi Diagram

Een Voronoi diagram is een eenvoudige verdeling van het vlak: gegeven een set van n punten (vaak aangeduid als sites) wilt u n regio's van het vlak creëren, één voor elk punt. Deze regio's worden gevormd zodat voor elke site elk punt binnen de regio dichter bij die site ligt dan bij enige andere site.

GeoTools heeft een methode genaamd "MakeVoronoiGraph" om een Voronoi diagram te bouwen voor een verzameling punten. We moeten drie of meer punten instellen, dan krijgen we een rechthoek (door het minimum en maximum van de "x" en "y" coördinaten voor alle punten te berekenen) om ons vlak te beperken. Als resultaat krijgen we een verzameling randen die het Voronoi diagram vormen, beperkt door onze rechthoek.

Vervolgens heeft GeoTools een methode genaamd "BuildCenterline" (die gebaseerd is op het Voronoi Diagram) om de middellijn voor een polygoon te krijgen. We moeten een polygoon (of een verzameling punten) instellen die binnenringen kan hebben. Hier, als resultaat, krijgen we een verzameling randen die het Voronoi diagram vormen, beperkt door de invoerpolygoon. Dit is het belangrijkste verschil tussen de methoden "MakeVoronoiGraph" en "BuildCenterline". We kunnen ook een verzameling punten instellen; in dit geval bouwen we een polygoon met deze punten. In sommige gevallen kunnen we een polygoon op verschillende manieren bouwen, dus voor meer nauwkeurigheid is het beter om de polygoon in te stellen.

En dan heeft GeoTools een methode genaamd "GetCenterlineLength" om de lengte van de middellijn te krijgen. Dit is de som van alle middellijnranden. Hier moeten we een polygoon (of een verzameling punten) instellen die binnenringen kan hebben.

## Make Voronoi Graph voor 3 punten

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Voronoi Graph voor 3 punten](rightTriangle.map.png)

## Make Voronoi Graph voor 6 punten

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Voronoi Graph voor 6 punten](test3.map.png)

## Make Voronoi Graph voor 2000 willekeurige punten

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
![Voronoi Graph voor 2000 punten](test8.map.png)

## Build Centerline en Get Centerline Length voor rechthoekige driehoek polygoon

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
![Rechthoekige driehoek polygoon](rightTriangle_p.map.png)

## Build Centerline voor vierkante polygoon met binnenring

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
![Vierkante Polygoon](square_p_2.map.png)

## Build Centerline en Get Centerline Length voor 6 punten

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
![Middellijn voor 6 punten](test3_c.map.png)
