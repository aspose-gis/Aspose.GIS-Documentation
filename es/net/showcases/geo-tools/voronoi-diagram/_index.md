---
title: "Diagrama de Voronoi"
type: docs
url: /es/net/geo-tools/voronoi-diagram/
description: "Cómo trabajar con el Diagrama de Voronoi utilizando la biblioteca Aspose.GIS"
weight: 70
---

# Diagrama de Voronoi

Un diagrama de Voronoi es una partición simple del plano: dado un conjunto de n puntos (a menudo denominados sitios) desea crear n regiones del plano, una para cada punto. Esas regiones se forman de tal manera que para cada sitio, cualquier punto dentro de su región esté más cerca de ese sitio que de cualquier otro sitio.

GeoTools tiene un método llamado "MakeVoronoiGraph" para construir un diagrama de Voronoi para una colección de puntos. Necesitamos establecer tres o más puntos, luego obtenemos un rectángulo (calculando el mínimo y el máximo de las coordenadas "x" e "y" para todos los puntos) para restringir nuestro plano. Como resultado, obtenemos una colección de aristas que forman el diagrama de Voronoi restringido por nuestro rectángulo.

Luego, GeoTools tiene un método llamado "BuildCenterline" (que se basa en el Diagrama de Voronoi) para obtener la línea central de un polígono. Necesitamos establecer un polígono (o una colección de puntos) que puede tener anillos interiores. Aquí, como resultado, obtenemos una colección de aristas que forman el diagrama de Voronoi restringido por el polígono de entrada. Esta es la principal diferencia entre los métodos "MakeVoronoiGraph" y "BuildCenterline". Además, podemos establecer una colección de puntos; en este caso, construimos un polígono con estos puntos. En algunos casos, podemos construir un polígono de diferentes maneras, por lo que para mayor precisión, es mejor establecer el polígono.

Y luego, GeoTools tiene un método llamado "GetCenterlineLength" para obtener la longitud de la línea central. Esta es la suma de todas las aristas de la línea central. Aquí necesitamos establecer un polígono (o una colección de puntos) que puede tener anillos interiores.

## Crear Gráfico de Voronoi para 3 puntos

```csharp
List<Point> sites = new List<Point>
{
    new Point(100, 100),
    new Point(200, 200),
    new Point(200, 100)
};

var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Gráfico de Voronoi para 3 puntos](rightTriangle.map.png)

## Crear Gráfico de Voronoi para 6 puntos

```csharp
List<Point> sites = new List<Point>();
MultiPoint geometryFromText = (MultiPoint)Geometry.FromText("MULTIPOINT ((320 170), (366 246), (530 230), (530 300), (455 277), (490 160))");
foreach (Point point in geometryFromText)
{
    sites.Add(point);
}
var edges = Gis.GeoTools.GeometryOperations.MakeVoronoiGraph(sites);
```
![Gráfico de Voronoi para 6 puntos](test3.map.png)

## Crear Gráfico de Voronoi para 2000 puntos aleatorios

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
![Gráfico de Voronoi para 2000 puntos](test8.map.png)

## Construir Línea Central y Obtener Longitud de la Línea Central para un polígono de triángulo rectángulo

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
![Polígono de triángulo rectángulo](rightTriangle_p.map.png)

## Construir Línea Central para un polígono cuadrado con anillo interior

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
![Polígono Cuadrado](square_p_2.map.png)

## Construir Línea Central y Obtener Longitud de la Línea Central para 6 puntos

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
![Línea Central para 6 puntos](test3_c.map.png)
