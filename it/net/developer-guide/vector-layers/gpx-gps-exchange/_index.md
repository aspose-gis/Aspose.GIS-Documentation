---
title: Lavorare con i file in formato GPX Exchange Format in C#
linktitle: GPX - Formato di scambio GPS
type: docs
url: /it/net/gpx-gps-exchange/
weight: 60
description: La libreria GIS C# consente di aprire e leggere le funzionalità dai file in formato GPS Exchange File (GPX).
---

## **Lavorare con i file in formato GPS Exchange File (GPX)**
Aspose.GIS consente di aprire e leggere le funzionalità dai file in formato GPS Exchange File (GPX).
## **Lettura delle funzionalità da un file GPX**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **Lettura delle funzionalità per ogni punto in un segmento**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **Scrittura di poligoni come linee in un file GPX**
Il formato GPX non supporta poligoni e multipoligonali. Di conseguenza, a volte la conversione da altri formati può fallire. È necessario applicare l'opzione WritePolygonsAsLines per risolvere questo problema.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
