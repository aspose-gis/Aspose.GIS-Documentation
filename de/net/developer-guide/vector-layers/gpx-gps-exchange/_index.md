---
title: Arbeiten mit GPS Exchange Format GPX Dateien in C#
linktitle: GPX - GPS Exchange Format
type: docs
url: /de/net/gpx-gps-exchange/
weight: 60
description: Die C#-GIS-Bibliothek ermöglicht es Ihnen, Features aus GPS Exchange Files (GPX) zu öffnen und zu lesen.
---

## **Arbeiten mit GPS Exchange File (GPX) Dateien**
Aspose.GIS ermöglicht es Ihnen, Features aus GPS Exchange Files (GPX) zu öffnen und zu lesen.
## **Lesen von Features aus GPX Datei**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **Lesen von Features für jeden Punkt in einem Segment**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **Polygone als Linien in GPX Datei schreiben**
Das GPX Format unterstützt keine Polygone und Multipolygone. Daher kann die Konvertierung aus anderen Formaten manchmal fehlschlagen. Sie sollten die Option WritePolygonsAsLines verwenden, um dieses Problem zu lösen.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
