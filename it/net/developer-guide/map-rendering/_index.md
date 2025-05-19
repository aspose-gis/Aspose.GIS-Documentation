---
title: Rendering di mappe in immagine SVG, PNG, JPG utilizzando la libreria GIS C#
linktitle: "Rendering di mappe"
type: docs
url: /it/net/map-rendering/
weight: 50
description: Con l'API GIS C#, puoi renderizzare una mappa da Shapefile, FileGDB, GeoJSON, formati KML, eseguire uno styling avanzato e disegnare una mappa da formati raster.
---

## **Panoramica del rendering di mappe**
Con l'API Aspose.GIS per .NET C# puoi renderizzare una mappa da un Shapefile, FileGDB, GeoJSON, KML o altri [formati di file supportati](/gis/net/supported-file-formats/) in SVG, PNG, JPEG o BMP.

Ecco il codice C# che illustra come renderizzare una mappa da un shapefile a SVG utilizzando le impostazioni predefinite:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



Ecco il risultato:



![rendering di mappa](map_rendering.png)

Esaminiamo più da vicino il codice.

Innanzitutto, istanziamo un oggetto [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map). Rappresenta una raccolta di layer provenienti da varie fonti che possono essere renderizzati. Una mappa ha una dimensione in cui deve essere visualizzata. Qui impostiamo la mappa su 800 pixel di larghezza e 400 pixel di altezza.

Nota che la Mappa è racchiusa nell'istruzione using. Questo è necessario perché la mappa tiene traccia di tutte le risorse aggiunte ad essa e le elimina quando abbiamo finito di renderizzare e l'oggetto Map viene eliminato.

Successivamente, aggiungiamo un layer da un file alla mappa. Ogni layer viene renderizzato sopra il layer precedente, nell'ordine in cui sono stati aggiunti alla mappa. Vedi maggiori dettagli su come aprire i layer vettoriali [qui](/gis/net/working-with-vector-layers/).

Infine, chiamiamo [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) per renderizzare la mappa in un file. Specifichiamo un percorso dove salvare il file di risultato e un renderer da utilizzare. La classe [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) contiene riferimenti a tutti i renderer inclusi con Aspose.GIS. Ad esempio, puoi specificare Renderers.Png invece di Renderers.Svg nell'esempio precedente per renderizzare la mappa in un file PNG

## **Styling avanzato**
Con l'API Aspose.GIS, puoi personalizzare il rendering e gli stili delle feature per ottenere l'aspetto desiderato.

![styling avanzato](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **Disegna raster nella mappa**
Con Aspose.GIS per .NET puoi renderizzare una mappa da formati raster.
### **Render con impostazioni predefinite**
Ecco come renderizzare una mappa da un GeoTIFF a SVG utilizzando le impostazioni predefinite:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![raster predefinito](default_raster.png)
### **Render raster distorti**
Con Aspose.GIS puoi renderizzare un raster con celle raster distorte.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![raster distorto](skew_raster.png)
### **Render in riferimento spaziale polare**
Aspose.GIS ti consente di utilizzare riferimenti spaziali polari su un processo di rendering della mappa.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![paesi gnomonici](gnomonic_countries.png)
