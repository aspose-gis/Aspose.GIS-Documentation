---
title: Рендиране на карта към изображение SVG, PNG, JPG с помощта на GIS C# библиотека
linktitle: "Рендиране на карта"
type: docs
url: /bg/net/map-rendering/
weight: 50
description: С GIS C# API можете да рендирате карта от Shapefile, FileGDB, GeoJSON, KML формати, да извършвате разширено стилизиране и да рисувате карта от растерни формати.
---

## **Общ преглед на рендирането на карта**
С C# API на Aspose.GIS for .NET можете да рендирате карта от Shapefile, FileGDB, GeoJSON, KML или други [поддържани файлови формати](/gis/net/supported-file-formats/) към SVG, PNG, JPEG или BMP.

Ето примерен C# код, който илюстрира как да рендирате карта от shapefile към SVG с помощта на настройки по подразбиране:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



Ето резултатът:



![рендиране на карта](map_rendering.png)

Нека разгледаме кода по-подробно.

Първо, създаваме обект [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map). Той представлява колекция от слоеве от различни източници, които могат да бъдат рендирани. Картата има размер, в който трябва да бъде показана. Тук задаваме картата да е 800 пиксела широка и 400 пиксела висока.

Забележете, че Map е затворен в оператора using. Това е необходимо, защото картата проследява всички ресурси, добавени към нея, и ги изхвърля, когато сме готови с рендирането и обектът Map е изхвърлен.

След това добавяме слой от файл към картата. Всеки слой се рендира върху предишния слой, в реда, в който са добавени към картата. Вижте повече подробности за това как да отворите векторни слоеве [тук](/gis/net/working-with-vector-layers/).

Накрая извикваме [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1), за да рендираме картата във файл. Указваме път, където да запазим резултатния файл и рендерър, който да използваме. Класът [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) съдържа препратки към всички рендерери, включени в Aspose.GIS. Например, можете да посочите Renderers.Png вместо Renderers.Svg в горния пример, за да рендирате картата в PNG файл.
## **Разширено стилизиране**
С API на Aspose.GIS можете да персонализирате рендирането и стиловете на характеристиките, за да постигнете желаната визия.

![разширено стилизиране](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **Рисуване на растер в карта**
С Aspose.GIS for .NET можете да рендирате карта от растерни формати.
### **Рендиране с настройки по подразбиране**
Ето как да рендирате карта от GeoTIFF към SVG, използвайки настройки по подразбиране:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![растер по подразбиране](default_raster.png)
### **Рендиране на наклонени растери**
С Aspose.GIS можете да рендирате растер с наклонени растерни клетки.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![наклонен растер](skew_raster.png)
### **Рендиране в полярна пространствена референция**
Aspose.GIS ви позволява да използвате полярни пространствени референции в процес на рендиране на карта.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![гномонични държави](gnomonic_countries.png)
