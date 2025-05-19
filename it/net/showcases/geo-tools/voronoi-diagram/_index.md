---
title: "Diagramma di Voronoi"
type: docs
url: /it/net/geo-tools/voronoi-diagram/
description: "Come lavorare con il Diagramma di Voronoi utilizzando la libreria Aspose.GIS"
weight: 70
---

# Diagramma di Voronoi

Un diagramma di Voronoi è una semplice partizione del piano: dato un insieme di n punti (spesso chiamati siti) si desidera creare n regioni del piano, una per ogni punto. Queste regioni sono formate in modo tale che per ogni sito, qualsiasi punto all'interno della sua regione sia più vicino a quel sito rispetto a qualsiasi altro sito.

GeoTools ha un metodo chiamato "MakeVoronoiGraph" per costruire un diagramma di Voronoi per una raccolta di punti. Dobbiamo impostare tre o più punti, quindi otteniamo un rettangolo (calcolando il minimo e il massimo delle coordinate "x" e "y" per tutti i punti) per limitare il nostro piano. Di conseguenza, otteniamo una raccolta di bordi che formano il diagramma di Voronoi limitato dal nostro rettangolo.

Quindi, GeoTools ha un metodo chiamato "BuildCenterline" (che si basa sul Diagramma di Voronoi) per ottenere la linea centrale per un poligono. Dobbiamo impostare un poligono (o una raccolta di punti) che può avere anelli interni. Qui, come risultato, otteniamo una raccolta di bordi che formano il diagramma di Voronoi limitato dal poligono di input. Questa è la differenza principale tra i metodi "MakeVoronoiGraph" e "BuildCenterline". Inoltre, possiamo impostare una raccolta di punti; in questo caso, costruiamo un poligono con questi punti. In alcuni casi, possiamo costruire un poligono in modi diversi, quindi per maggiore precisione, è meglio impostare il poligono.

E poi, GeoTools ha un metodo chiamato "GetCenterlineLength" per ottenere la lunghezza della linea centrale. Questa è la somma di tutti i bordi della linea centrale. Qui dobbiamo impostare un poligono (o una raccolta di punti) che può avere anelli interni.

## Crea il grafico di Voronoi per 3 punti

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Grafico di Voronoi per 3 punti](rightTriangle.map.png)

## Crea il grafico di Voronoi per 6 punti

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Grafico di Voronoi per 6 punti](test3.map.png)

## Crea il grafico di Voronoi per 2000 punti casuali

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
![Grafico di Voronoi per 2000 punti](test8.map.png)

## Costruisci la linea centrale e ottieni la lunghezza della linea centrale per il poligono del triangolo rettangolo

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
![Poligono del triangolo rettangolo](rightTriangle_p.map.png)

## Costruisci la linea centrale per il poligono quadrato con anello interno

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
![Poligono quadrato](square_p_2.map.png)

## Costruisci la linea centrale e ottieni la lunghezza della linea centrale per 6 punti

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
![Linea centrale per 6 punti](test3_c.map.png)
