---
title: Відображення карти у зображення SVG, PNG, JPG за допомогою GIS C# бібліотеки
linktitle: "Відображення карти"
type: docs
url: /uk/net/map-rendering/
weight: 50
description: За допомогою GIS C# API ви можете відображати карту з Shapefile, FileGDB, GeoJSON, KML форматів, виконувати розширене стилізування та малювати карту з растрових форматів.
---

## **Огляд відображення карти**
За допомогою Aspose.GIS для .NET C# API ви можете відображати карту з Shapefile, FileGDB, GeoJSON, KML або інших [підтримуваних файлових форматів](/gis/net/supported-file-formats/) у SVG, PNG, JPEG або BMP.

Ось код C#, який ілюструє, як відобразити карту з shapefile в SVG за допомогою налаштувань за замовчуванням:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



Ось результат:



![відображення карти](map_rendering.png)

Давайте уважніше розглянемо код.

Спочатку ми створюємо об’єкт [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map). Він представляє собою колекцію шарів з різних джерел, які можна відобразити. Карта має розмір, при якому вона повинна бути відображена. Тут ми встановлюємо ширину карти 800 пікселів і висоту 400 пікселів.

Зверніть увагу, що Map знаходиться в операторі using. Це необхідно, тому що карта відстежує всі додані до неї ресурси та звільняє їх після завершення рендерингу та утилізації об’єкта Map.

Далі ми додаємо шар з файлу на карту. Кожен шар відображається поверх попереднього шару в порядку, в якому вони були додані на карту. Більш детальна інформація про відкриття векторних шарів [тут](/gis/net/working-with-vector-layers/).

Нарешті, ми викликаємо [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1), щоб відобразити карту у файл. Ми вказуємо шлях до місця збереження файлу результату та рендерер для використання. Клас [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) містить посилання на всі рендерери, включені в Aspose.GIS. Наприклад, ви можете вказати Renderers.Png замість Renderers.Svg у прикладі вище, щоб відобразити карту у PNG файл.
## **Розширене стилізування**
За допомогою API Aspose.GIS ви можете налаштувати рендеринг та стилі об’єктів для досягнення бажаного вигляду.

![розширене стилізування](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **Малювання растру на карті**
За допомогою Aspose.GIS для .NET ви можете відображати карту з растрових форматів.
### **Відображення за налаштуваннями за замовчуванням**
Ось як відобразити карту з GeoTIFF в SVG, використовуючи налаштування за замовчуванням:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![растр за замовчуванням](default_raster.png)
### **Відображення перекошених растрових зображень**
За допомогою Aspose.GIS ви можете відображати растр з перекошеними клітинками растру.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![перекошений растр](skew_raster.png)
### **Відображення в полярній просторовій системі відліку**
Aspose.GIS дозволяє використовувати полярні просторові системи відліку в процесі рендерингу карти.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![гномонічні країни](gnomonic_countries.png)
