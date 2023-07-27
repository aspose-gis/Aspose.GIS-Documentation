---
title: "How to Draw Geometry on a Map"
type: docs
url: /net/how-to-draw-geometry
weight: 70
---

# How to Draw Geometry on a Map

To create and display geometric objects on a map, you need to start by **creating a geometry object**. There are two methods you can use:

- **Constructor for Each Geometry Feature Type**
This method involves using a custom constructor for each geometry feature type. For example, to create a point, you would use the following code:

```
Point point = new Point(40.7128, -74.006);
```

However, this method can become challenging and cumbersome to manage when creating complex objects like polylines or collections. As a result, the developer may need to add many lines of code, causing the readability of the code to drop. Ensuring data integrity during initialization can also be difficult. For instance, consider the following example that creates a polygon with a hole inside:

```
Polygon polygon = new Polygon();

LinearRing ring = new LinearRing();
ring.AddPoint(50.02, 36.22);
ring.AddPoint(49.99, 36.26);
ring.AddPoint(49.97, 36.23);
ring.AddPoint(49.98, 36.17);
ring.AddPoint(50.02, 36.22);

LinearRing hole = new LinearRing();
hole.AddPoint(50.00, 36.22);
hole.AddPoint(49.99, 36.20);
hole.AddPoint(49.98, 36.23);
hole.AddPoint(50.00, 36.24);
hole.AddPoint(50.00, 36.22);

polygon.ExteriorRing = ring;
polygon.AddInteriorRing(hole);
```

Another disadvantage of this approach is the lack of uniformity of the data for initialization. You cannot create a repository of constants or files within your project.

- **WKT (Well-Known Text)**
This method involves generating geometry from WKT (Well-Known Text), which offers a standardized way to create geometries. The following code demonstrates how to create a point and a line:

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

While this approach may slightly reduce performance due to the need to parse the string, it simplifies the creation of more complex objects.

You can find more details about WKT in the following article: "Exporting and Importing Data from/to WKT and WKB."

Displaying Geometric Objects on the Map
Once you have created a geometric object, the next step is to display it on the map. While the map can display layers loaded from various sources and formats, the InMemoryLayer is a layer that doesn't require a source.

**To display your geometric object**, you can create an InMemoryLayer and add the object to it:

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

Now you can **display this layer on the map and create a file in one of the supported formats**, such as SVG, with the following code:

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

Once you have added the layer and displayed it on the map, you can save it in any of the supported formats. In this example, the SVG format is chosen to avoid potential issues with Bitmap support. It's important to note that Net 6.0 has limited Bitmap support, which can result in restrictions like the inability to render Bitmap images using Blazor WebAsm on the client-side. Therefore, when choosing a format to save your map, it's important to consider the limitations of the target platform and select a format that is compatible with it.

The article explains how to create and display geometric objects on a map with a default, plain style. However, the Aspose library offers a wide range of styling options that can be customized to fit your needs. To explore these options, we recommend consulting the [Aspose.MapRendering documentation]( https://docs.aspose.com/gis/net/map-rendering/), which provides detailed information on how to use different styling techniques to enhance the visual appeal of your map.

**In summary**, to create geometric objects on a map, you can use either a constructor for each geometry feature type or generate geometry from WKT. To display the object, place it on a layer and display the layer on a map in default map styling. Save the map in a supported format, such as SVG, and use our library to explore styling options. Additionally, our library provides an opportunity to see a finished example by clicking on the [link]( https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer) provided in the documentation, which can help you to understand how to implement these techniques in your own projects.
