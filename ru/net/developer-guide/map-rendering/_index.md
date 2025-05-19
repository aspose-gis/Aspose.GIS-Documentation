---
title: Отображение карты в изображение SVG, PNG, JPG с использованием GIS C# Library
linktitle: "Отображение карты"
type: docs
url: /ru/net/map-rendering/
weight: 50
description: С помощью GIS C# API вы можете отображать карту из Shapefile, FileGDB, GeoJSON, KML форматов, выполнять расширенное стилизование и рисовать карту из растровых форматов.
---

## **Обзор отображения карты**
С помощью Aspose.GIS для .NET C# API вы можете отобразить карту из Shapefile, FileGDB, GeoJSON, KML или других [поддерживаемых форматов файлов](/gis/net/supported-file-formats/) в SVG, PNG, JPEG или BMP.

Вот код на C#, иллюстрирующий, как отобразить карту из shapefile в SVG с использованием настроек по умолчанию:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



Вот результат:



![отображение карты](map_rendering.png)

Давайте посмотрим на код подробнее.

Во-первых, мы создаем экземпляр объекта [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map). Он представляет собой коллекцию слоев из различных источников, которые можно отобразить. Карта имеет размер, при котором она должна быть отображена. Здесь мы устанавливаем ширину карты 800 пикселей и высоту 400 пикселей.

Обратите внимание, что Map заключен в оператор using. Это необходимо, потому что карта отслеживает все ресурсы, добавленные к ней, и удаляет их, когда мы заканчиваем рендеринг и объект Map утилизирован.

Затем мы добавляем слой из файла на карту. Каждый слой отображается поверх предыдущего слоя в порядке их добавления на карту. Более подробную информацию о том, как открывать векторные слои, можно найти [здесь](/gis/net/working-with-vector-layers/).

Наконец, мы вызываем [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1), чтобы отобразить карту в файл. Мы указываем путь к месту сохранения результирующего файла и отрисовщик для использования. Класс [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) содержит ссылки на все отрисовщики, включенные в Aspose.GIS. Например, вы можете указать Renderers.Png вместо Renderers.Svg в приведенном выше примере, чтобы отобразить карту в PNG-файл.

## **Расширенное стилизование**
С помощью API Aspose.GIS вы можете настроить рендеринг и стили функций для достижения желаемого внешнего вида.

![расширенное стилизование](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}

## **Рисование растра в карте**
С помощью Aspose.GIS для .NET вы можете отображать карту из растровых форматов.

### **Отображение с настройками по умолчанию**
Вот как отобразить карту из GeoTIFF в SVG, используя настройки по умолчанию:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![растр по умолчанию](default_raster.png)

### **Отображение искаженных растров**
С помощью Aspose.GIS вы можете отображать растр с искаженными ячейками растра.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![искаженный растр](skew_raster.png)

### **Отображение в полярной пространственной ссылке**
Aspose.GIS позволяет использовать полярные пространственные ссылки в процессе отображения карты.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![гномонические страны](gnomonic_countries.png)
