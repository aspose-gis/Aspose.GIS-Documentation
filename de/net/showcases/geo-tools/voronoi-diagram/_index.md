---
title: "Voronoi-Diagramm"
type: docs
url: /de/net/geo-tools/voronoi-diagram/
description: "So arbeiten Sie mit Voronoi-Diagrammen unter Verwendung der Aspose.GIS-Bibliothek"
weight: 70
---

# Voronoi-Diagramm

Ein Voronoi-Diagramm ist eine einfache Aufteilung der Ebene: Gegeben sei eine Menge von n Punkten (oft als Stellen bezeichnet), Sie möchten n Regionen der Ebene erstellen, jeweils für einen Punkt. Diese Regionen werden so gebildet, dass für jede Stelle jeder Punkt innerhalb seiner Region näher an dieser Stelle liegt als an einer anderen Stelle.

GeoTools verfügt über eine Methode namens "MakeVoronoiGraph", um ein Voronoi-Diagramm für eine Sammlung von Punkten zu erstellen. Wir müssen drei oder mehr Punkte festlegen, dann erhalten wir ein Rechteck (Berechnung des Minimums und Maximums der "x"- und "y"-Koordinaten für alle Punkte), um unsere Ebene einzuschränken. Als Ergebnis erhalten wir eine Sammlung von Kanten, die das Voronoi-Diagramm bilden, das durch unser Rechteck eingeschränkt wird.

Dann verfügt GeoTools über eine Methode namens "BuildCenterline" (die auf dem Voronoi-Diagramm basiert), um die Mittellinie für ein Polygon zu erhalten. Wir müssen ein Polygon (oder eine Sammlung von Punkten) festlegen, das Innenringe haben kann. Hier erhalten wir als Ergebnis eine Sammlung von Kanten, die das Voronoi-Diagramm bilden, das durch das Eingabepolygon eingeschränkt wird. Dies ist der Hauptunterschied zwischen den Methoden "MakeVoronoiGraph" und "BuildCenterline". Außerdem können wir eine Sammlung von Punkten festlegen; in diesem Fall erstellen wir ein Polygon anhand dieser Punkte. In einigen Fällen können wir ein Polygon auf verschiedene Weise erstellen, daher ist es für mehr Genauigkeit besser, das Polygon festzulegen.

Und dann verfügt GeoTools über eine Methode namens "GetCenterlineLength", um die Länge der Mittellinie zu erhalten. Dies ist die Summe aller Kanten der Mittellinie. Hier müssen wir ein Polygon (oder eine Sammlung von Punkten) festlegen, das Innenringe haben kann.

## Voronoi-Graph für 3 Punkte erstellen

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Voronoi-Graph für 3 Punkte](rightTriangle.map.png)

## Voronoi-Graph für 6 Punkte erstellen

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Voronoi-Graph für 6 Punkte](test3.map.png)

## Voronoi-Graph für 2000 Zufallspunkte erstellen

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
![Voronoi-Graph für 2000 Punkte](test8.map.png)

## Mittellinie erstellen und Mittellinienlänge für ein rechtwinkliges Dreieckspolygon erhalten

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
![Rechtwinkliges Dreieckspolygon](rightTriangle_p.map.png)

## Mittellinie für ein quadratisches Polygon mit Innenring erstellen

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
![Quadratisches Polygon](square_p_2.map.png)

## Mittellinie erstellen und Mittellinienlänge für 6 Punkte erhalten

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
![Mittellinie für 6 Punkte](test3_c.map.png)
