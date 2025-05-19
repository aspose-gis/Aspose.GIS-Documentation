---
title: Renderizado de Mapas a Imagen SVG, PNG, JPG usando la Biblioteca GIS C#
linktitle: "Renderizado de Mapas"
type: docs
url: /es/net/map-rendering/
weight: 50
description: Con la API GIS C# , puede renderizar un mapa desde Shapefile, FileGDB, GeoJSON, formatos KML, realizar estilos avanzados y dibujar mapas desde formatos ráster.
---

## **Descripción general del renderizado de mapas**
Con la API Aspose.GIS para .NET C#, puede renderizar un mapa desde un Shapefile, FileGDB, GeoJSON, KML u otros [formatos de archivo compatibles](/gis/net/supported-file-formats/) a SVG, PNG, JPEG o BMP.

Aquí hay código C# que ilustra cómo renderizar un mapa desde un shapefile a SVG usando la configuración predeterminada:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



Aquí está el resultado:



![renderizado de mapa](map_rendering.png)

Echemos un vistazo más de cerca al código.

Primero, instanciamos un objeto [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map). Representa una colección de capas de diversas fuentes que se pueden renderizar. Un mapa tiene un tamaño en el que pretende mostrarse. Aquí configuramos el mapa para que tenga 800 píxeles de ancho y 400 píxeles de alto.

Tenga en cuenta que el Mapa está encerrado en la instrucción using. Esto es necesario porque el mapa realiza un seguimiento de todos los recursos agregados a él y los elimina cuando terminamos con el renderizado y se elimina el objeto Map.

A continuación, agregamos una capa desde un archivo al mapa. Cada capa se renderiza sobre la capa anterior, en el orden en que se agregaron al mapa. Consulte más detalles sobre cómo abrir capas vectoriales [aquí](/gis/net/working-with-vector-layers/).

Finalmente, llamamos a [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) para renderizar el mapa en un archivo. Especificamos una ruta donde guardar el archivo de resultados y un renderizador que se utilizará. La clase [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) contiene referencias a todos los renderizadores incluidos con Aspose.GIS. Por ejemplo, puede especificar Renderers.Png en lugar de Renderers.Svg en el ejemplo anterior para renderizar el mapa en un archivo PNG

## **Estilo avanzado**
Con la API Aspose.GIS, puede personalizar el renderizado y los estilos de las características para lograr el aspecto que desea.

![estilo avanzado](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **Dibujar ráster en el mapa**
Con Aspose.GIS para .NET, puede renderizar un mapa desde formatos ráster.
### **Renderizar con la configuración predeterminada**
Aquí le mostramos cómo renderizar un mapa de GeoTIFF a SVG utilizando la configuración predeterminada:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![ráster predeterminado](default_raster.png)
### **Renderizar rásters sesgados**
Con Aspose.GIS puede renderizar un ráster con celdas de ráster sesgadas.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![ráster sesgado](skew_raster.png)
### **Renderizar en referencia espacial polar**
Aspose.GIS le permite utilizar referencias espaciales polares en un proceso de renderizado de mapas.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![países gnomónicos](gnomonic_countries.png)
