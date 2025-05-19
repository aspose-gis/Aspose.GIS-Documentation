---
title: Kartenrendering zu Bild SVG, PNG, JPG mit GIS C#-Bibliothek
linktitle: "Kartenrendering"
type: docs
url: /de/net/map-rendering/
weight: 50
description: Mit der GIS C# API können Sie eine Karte aus Shapefile-, FileGDB-, GeoJSON- oder KML-Formaten rendern, fortschrittliche Formatierungen durchführen und Karten aus Rasterformaten zeichnen.
---

## **Überblick über das Kartenrendering**
Mit der Aspose.GIS for .NET C# API können Sie eine Karte aus einem Shapefile, FileGDB, GeoJSON, KML oder anderen [unterstützten Dateiformaten](/gis/net/supported-file-formats/) in SVG, PNG, JPEG oder BMP rendern.

Hier ist ein C#-Code, der veranschaulicht, wie man eine Karte aus einer Shapefile mit Standardeinstellungen in SVG rendert:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



Hier ist das Ergebnis:



![Kartenrendering](map_rendering.png)

Schauen wir uns den Code genauer an.

Zuerst instanziieren wir ein [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map)-Objekt. Es repräsentiert eine Sammlung von Layern aus verschiedenen Quellen, die gerendert werden können. Eine Karte hat eine Größe, in der sie angezeigt werden soll. Hier setzen wir die Karte auf 800 Pixel Breite und 400 Pixel Höhe.

Beachten Sie, dass sich die Map in einer using-Anweisung befindet. Dies ist notwendig, da die Map alle hinzugefügten Ressourcen verfolgt und diese verwirft, wenn wir mit dem Rendern fertig sind und das Map-Objekt verworfen wird.

Als Nächstes fügen wir ein Layer aus einer Datei zur Karte hinzu. Jedes Layer wird über den vorherigen Layern gerendert, in der Reihenfolge, in der sie der Karte hinzugefügt wurden. Weitere Details zum Öffnen von Vektorlayern finden Sie [hier](/gis/net/working-with-vector-layers/).

Schließlich rufen wir [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) auf, um die Karte in eine Datei zu rendern. Wir geben einen Pfad an, wo die Ergebnisdatei gespeichert werden soll, und einen Renderer, der verwendet werden soll. Die Klasse [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) enthält Referenzen auf alle mit Aspose.GIS gelieferten Renderer. Sie können beispielsweise Renderers.Png anstelle von Renderers.Svg im obigen Beispiel angeben, um die Karte in eine PNG-Datei zu rendern.

## **Erweiterte Formatierung**
Mit der Aspose.GIS API können Sie das Rendering und den Feature-Stil anpassen, um das gewünschte Aussehen zu erzielen.

![erweiterte Formatierung](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}

## **Raster in Karte zeichnen**
Mit Aspose.GIS for .NET können Sie eine Karte aus Rasterformaten rendern.

### **Mit Standardeinstellungen rendern**
Hier erfahren Sie, wie Sie eine Karte aus einem GeoTIFF mit Standardeinstellungen in SVG rendern:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![Standardraster](default_raster.png)

### **Schiefe Raster rendern**
Mit Aspose.GIS können Sie ein Raster mit schiefen Rasterzellen rendern.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![Schiefes Raster](skew_raster.png)

### **In polaren räumlichen Referenzen rendern**
Aspose.GIS ermöglicht Ihnen die Verwendung polarer räumlicher Referenzen in einem Kartenrenderingprozess.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![gnomonische Länder](gnomonic_countries.png)
