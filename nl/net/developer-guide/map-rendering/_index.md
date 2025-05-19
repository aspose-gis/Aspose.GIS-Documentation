---
title: Kaartweergave naar Afbeelding SVG, PNG, JPG met GIS C# Bibliotheek
linktitle: "Kaartweergave"
type: docs
url: /nl/net/map-rendering/
weight: 50
description: Met de GIS C# API kunt u een kaart renderen vanuit Shapefile, FileGDB, GeoJSON, KML formaten, geavanceerde styling uitvoeren en kaarten tekenen vanuit rasterformaten. 
---

## **Overzicht Kaartweergave**
Met de Aspose.GIS for .NET C# API kunt u een kaart renderen vanuit een Shapefile, FileGDB, GeoJSON, KML of andere [ondersteunde bestandsformaten](/gis/nl/net/supported-file-formats/) naar SVG, PNG, JPEG of BMP.

Hier is C#-code die illustreert hoe u een kaart uit een shapefile naar SVG kunt renderen met behulp van de standaardinstellingen:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



Hier is het resultaat:



![kaartweergave](map_rendering.png)

Laten we de code eens nader bekijken.

Eerst instantieren we een [Map ](https://reference.aspose.com/gis/nl/net/aspose.gis.rendering/map)object. Het vertegenwoordigt een verzameling lagen uit verschillende bronnen die kunnen worden weergegeven. Een Map heeft een grootte waarop het bedoeld is om te worden weergegeven. Hier stellen we de kaart in op 800 pixels breed en 400 pixels hoog.

Merk op dat de Map is ingesloten in de using-instructie. Dit is noodzakelijk omdat de map alle toegevoegde bronnen bijhoudt en deze verwijdert wanneer we klaar zijn met renderen en het Map-object wordt verwijderd.

Vervolgens voegen we een laag uit een bestand toe aan de kaart. Elke laag wordt bovenop de vorige laag weergegeven, in de volgorde waarin ze aan de kaart zijn toegevoegd. Zie voor meer details over hoe u vectorlagen kunt openen [hier](/gis/nl/net/working-with-vector-layers/).

Ten slotte roepen we [Map.Render](https://reference.aspose.com/gis/nl/net/aspose.gis.rendering.map/render/methods/1) aan om de kaart naar een bestand te renderen. We specificeren een pad waar het resultaatbestand moet worden opgeslagen en een renderer die moet worden gebruikt. Klasse [Renderers ](https://reference.aspose.com/gis/nl/net/aspose.gis.rendering/renderers)bevat verwijzingen naar alle renderers die bij Aspose.GIS zijn inbegrepen. U kunt bijvoorbeeld Renderers.Png specificeren in plaats van Renderers.Svg in het bovenstaande voorbeeld om de kaart naar een PNG-bestand te renderen.
## **Geavanceerde Styling**
Met de Aspose.GIS API kunt u rendering en featurestijlen aanpassen om de look te krijgen die u wilt. 

![geavanceerde styling](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **Teken raster in kaart**
Met Aspose.GIS for .NET kunt u een kaart renderen vanuit rasterformaten.
### **Render met standaardinstellingen**
Hieronder ziet u hoe u een kaart uit een GeoTIFF naar SVG kunt renderen met behulp van de standaardinstellingen:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![standaard raster](default_raster.png)
### **Render scheve rasters**
Met Aspose.GIS kunt u een raster renderen met scheve rastercellen.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![scheef raster](skew_raster.png)
### **Render in polaire ruimtelijke referentie**
Aspose.GIS stelt u in staat om polaire ruimtelijke referenties te gebruiken bij een kaartrenderingsproces.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![gnomonische landen](gnomonic_countries.png)
