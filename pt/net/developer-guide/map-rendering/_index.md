---
title: Renderização de Mapa para Imagem SVG, PNG, JPG usando a Biblioteca GIS C#
linktitle: "Renderização de Mapa"
type: docs
url: /pt/net/map-rendering/
weight: 50
description: Com a API GIS C#, você pode renderizar um mapa de formatos Shapefile, FileGDB, GeoJSON, KML, realizar estilizações avançadas e desenhar mapas de formatos raster.
---

## **Visão Geral da Renderização de Mapa**
Com a API Aspose.GIS para .NET C# você pode renderizar um mapa de um Shapefile, FileGDB, GeoJSON, KML ou outros [formatos de arquivo suportados](/gis/net/supported-file-formats/) para SVG, PNG, JPEG ou BMP.

Aqui está o código C# ilustrando como renderizar um mapa de um shapefile para SVG usando as configurações padrão:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



Aqui está o resultado:



![renderização de mapa](map_rendering.png)

Vamos analisar mais detalhadamente o código.

Primeiro, instanciamos um objeto [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map). Ele representa uma coleção de camadas de várias fontes que podem ser renderizadas. Um Mapa tem um tamanho em que deve ser exibido. Aqui definimos o mapa para ter 800 pixels de largura e 400 pixels de altura.

Observe que o Map está envolto na instrução using. Isso é necessário porque o mapa rastreia todos os recursos adicionados a ele e os descarta quando terminamos de renderizar e o objeto Map é descartado.

Em seguida, adicionamos uma camada de um arquivo ao mapa. Cada camada é renderizada sobre a camada anterior, na ordem em que foram adicionadas ao mapa. Veja mais detalhes sobre como abrir camadas vetoriais [aqui](/gis/net/working-with-vector-layers/).

Finalmente, chamamos [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) para renderizar o mapa em um arquivo. Especificamos um caminho para onde salvar o arquivo de resultado e um renderer a ser usado. A classe [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) contém referências a todos os renderizadores incluídos com o Aspose.GIS. Por exemplo, você pode especificar Renderers.Png em vez de Renderers.Svg no exemplo acima para renderizar o mapa em um arquivo PNG

## **Estilização Avançada**
Com a API Aspose.GIS, você pode personalizar a renderização e os estilos de recursos para alcançar o visual desejado. 

![estilização avançada](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **Desenhe raster no mapa**
Com o Aspose.GIS para .NET você pode renderizar um mapa de formatos raster.
### **Renderize com as configurações padrão**
Aqui está como renderizar um mapa de um GeoTIFF para SVG usando as configurações padrão:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![raster padrão](default_raster.png)
### **Renderize rasters inclinados**
Com o Aspose.GIS você pode renderizar um raster com células de raster inclinadas.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![raster inclinado](skew_raster.png)
### **Renderize em referência espacial polar**
O Aspose.GIS permite usar referências espaciais polares em um processo de renderização de mapa.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![países gnomônicos](gnomonic_countries.png)
