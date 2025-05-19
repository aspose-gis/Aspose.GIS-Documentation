---
title: "Voronoiův diagram"
type: docs
url: /cs/net/geo-tools/voronoi-diagram/
description: "Jak pracovat s Voronoiovým diagramem pomocí knihovny Aspose.GIS"
weight: 70
---

# Voronoiův diagram

Voronoiův diagram je jednoduché rozdělení roviny: máte sadu n bodů (často označovaných jako lokality) a chcete vytvořit n oblastí roviny, jednu pro každý bod. Tyto oblasti jsou tvořeny tak, že pro každou lokalitu je jakýkoli bod uvnitř její oblasti bližší této lokalitě než kterékoli jiné lokalitě.

GeoTools mají metodu s názvem "MakeVoronoiGraph" pro vytvoření Voronoiova diagramu pro kolekci bodů. Musíme nastavit tři nebo více bodů, pak získáme obdélník (vypočítáním minima a maxima „x“ a „y“ souřadnic pro všechny body) k omezení naší roviny. Výsledkem je kolekce hran tvořících Voronoiův diagram omezený naším obdélníkem.

Potom GeoTools mají metodu s názvem "BuildCenterline" (která je založena na Voronoiově diagramu) pro získání středové čáry polygonu. Musíme nastavit polygon (nebo kolekci bodů), který může mít vnitřní prsteny. Zde jako výsledek získáme kolekci hran tvořících Voronoiův diagram omezený vstupním polygonem. To je hlavní rozdíl mezi metodami "MakeVoronoiGraph" a "BuildCenterline". Také můžeme nastavit kolekci bodů; v tomto případě vytvoříme polygon pomocí těchto bodů. V některých případech můžeme polygon sestavit různými způsoby, takže pro větší přesnost je lepší nastavit polygon.

A pak GeoTools mají metodu s názvem "GetCenterlineLength" pro získání délky středové čáry. To je součet všech hran středové čáry. Zde musíme nastavit polygon (nebo kolekci bodů), který může mít vnitřní prsteny.

## Vytvoření Voronoiova grafu pro 3 body

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Voronoiův graf pro 3 body](rightTriangle.map.png)

## Vytvoření Voronoiova grafu pro 6 bodů

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Voronoiův graf pro 6 bodů](test3.map.png)

## Vytvoření Voronoiova grafu pro 2000 náhodných bodů

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
![Voronoiův graf pro 2000 bodů](test8.map.png)

## Vytvoření středové čáry a získání délky středové čáry pro pravoúhlý trojúhelníkový polygon

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
![Pravoúhlý trojúhelníkový polygon](rightTriangle_p.map.png)

## Vytvoření středové čáry pro čtvercový polygon s vnitřním prstencem

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
![Čtvercový polygon](square_p_2.map.png)

## Vytvoření středové čáry a získání délky středové čáry pro 6 bodů

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
![Středová čára pro 6 bodů](test3_c.map.png)
