---
title: Práce se soubory ve formátu GPS Exchange Format GPX v C#
linktitle: GPX - Formát pro výměnu GPS dat
type: docs
url: /cs/net/gpx-gps-exchange/
weight: 60
description: Knihovna C# GIS vám umožní otevřít a číst prvky ze souborů ve formátu GPS Exchange File (GPX).
---

## **Práce se soubory ve formátu GPS Exchange File (GPX)**
Aspose.GIS vám umožňuje otevřít a číst prvky ze souborů ve formátu GPS Exchange File (GPX).
## **Čtení prvků ze souboru GPX**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **Čtení prvků pro každý bod v segmentu**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **Zápis polygonů jako čar do souboru GPX**
Formát GPX nepodporuje polygony a multipolygony. V důsledku toho někdy konverze z jiných formátů selže. Měli byste použít možnost WritePolygonsAsLines pro vyřešení tohoto problému.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
