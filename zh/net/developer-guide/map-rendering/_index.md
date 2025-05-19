---
title: 使用 GIS C# 库将地图渲染为图像 SVG、PNG、JPG
linktitle: "地图渲染"
type: docs
url: /zh/net/map-rendering/
weight: 50
description: 通过 GIS C# API，您可以从 Shapefile、FileGDB、GeoJSON、KML 格式渲染地图，执行高级样式设置并从栅格格式绘制地图。
---

## **地图渲染概述**
使用 Aspose.GIS for .NET C# API，您可以将来自 Shapefile、FileGDB、GeoJSON、KML 或其他 [支持的文件格式](/gis/net/supported-file-formats/) 的地图渲染为 SVG、PNG、JPEG 或 BMP。

以下是说明如何使用默认设置从 shapefile 渲染地图的 C# 代码：

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}

这是结果：

![地图渲染](map_rendering.png)

让我们更详细地了解代码。

首先，我们实例化一个 [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map) 对象。它代表可以渲染的来自各种来源的图层集合。 Map 具有其打算显示的尺寸。在这里，我们将地图设置为宽度为 800 像素、高度为 400 像素。

请注意，Map 包含在 using 语句中。这是必要的，因为 map 会跟踪添加到其中的所有资源，并在完成渲染且 Map 对象被释放时释放它们。

接下来，我们将来自文件的图层添加到地图中。每个图层都渲染在之前的图层之上，按照其添加到地图中的顺序进行渲染。有关如何打开矢量图层的更多详细信息，请参阅 [此处](/gis/net/working-with-vector-layers/)。

最后，我们调用 [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) 将地图渲染到文件。我们指定保存结果文件的路径和要使用的渲染器。类 [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) 包含 Aspose.GIS 中包含的所有渲染器的引用。例如，您可以指定 Renderers.Png 而不是上述示例中的 Renderers.Svg 将地图渲染为 PNG 文件

## **高级样式设置**
使用 Aspose.GIS API，您可以自定义渲染和特征样式以实现所需的外观。

![高级样式](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}

## **在地图中绘制栅格**
使用 Aspose.GIS for .NET，您可以从栅格格式渲染地图。
### **使用默认设置渲染**
以下是如何使用默认设置将 GeoTIFF 渲染为 SVG 的方法：

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![默认栅格](default_raster.png)
### **渲染倾斜栅格**
使用 Aspose.GIS，您可以渲染具有倾斜栅格单元的栅格。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![倾斜栅格](skew_raster.png)
### **在极坐标空间参考中渲染**
Aspose.GIS 允许您在地图渲染过程中使用极坐标空间参考。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![等角投影国家](gnomonic_countries.png)
