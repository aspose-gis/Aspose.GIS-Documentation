---
title: "Map Rendering"
type: docs
url: /net/map-rendering/
weight: 50
description: With GIS C# API, you can render map from Shapefile, FileGDB, GeoJSON, KML formats, perform advance styling and draw map from raster formats. 
---

## **Map Rendering Overview**
With Aspose.GIS for .NET C# API you can render a map from a Shapefile, FileGDB, GeoJSON, KML or other [supported file formats](/gis/net/supported-file-formats/) to SVG, PNG, JPEG, or BMP.

Here is C# code illustrating how to render a map from a shapefile to SVG using default settings:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



Here’s the result:



![map rendering](map_rendering.png)

Let’s take a closer look at the code.

First, we instantiate a [Map ](https://apireference.aspose.com/gis/net/aspose.gis.rendering/map)object. It represents a collection of layers from various sources that can be rendered. A Map has a size it’s intended to be displayed at. Here we set the map to be 800 pixels wide and 400 pixels tall.

Notice that the Map is enclosed into the using statement. This is necessary because the map keeps track of all resources added to it, and disposes them when we’re done with rendering and Map object is disposed.

Next, we add a layer from a file to the map. Each layer is rendered on top of the previous layer, in the order in which they were added to the map. See more details about how to open vector layers [here](/gis/net/working-with-vector-layers/).

Finally, we call [Map.Render](https://apireference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) to render the map into a file. We specify a path to where to save the result file and a renderer to use. Class [Renderers ](https://apireference.aspose.com/gis/net/aspose.gis.rendering/renderers)contains references to all renderers included with Aspose.GIS. For example, you can specify Renderers.Png instead of Renderers.Svg in the example above to render the map into a PNG file
## **Advanced Styling**
With Aspose.GIS API, you can customize rendering and feature styles in order to achieve the look you want. 

![advanced styling](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **Draw raster in map**
With Aspose.GIS for .NET you can render a map from raster formats.
### **Render with default settings**
Here’s how to render a map from a GeoTIFF to SVG using default settings:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![default raster](default_raster.png)
### **Render skew rasters**
With Aspose.GIS you can render a raster with skew raster cells.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![skew raster](skew_raster.png)
### **Render in polar spatial reference**
Aspose.GIS lets you using polar spatial references on a map rendering process.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![gnomonic countries](gnomonic_countries.png)


