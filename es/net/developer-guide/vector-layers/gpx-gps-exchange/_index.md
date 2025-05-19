---
title: Trabajar con archivos de formato de intercambio GPS GPX en C#
linktitle: GPX - Formato de intercambio GPS
type: docs
url: /es/net/gpx-gps-exchange/
weight: 60
description: La biblioteca GIS de C# le permite abrir y leer características de los archivos de formato de intercambio GPS (GPX).
---

## **Trabajar con archivos de formato de intercambio GPS (GPX)**
Aspose.GIS le permite abrir y leer características de los archivos de formato de intercambio GPS (GPX).
## **Leer características de un archivo GPX**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **Leer características para cada punto en un segmento**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **Escribir polígonos como líneas en un archivo GPX**
El formato GPX no admite polígonos y multipolígonos. Como resultado, a veces la conversión falla desde otros formatos. Debe aplicar la opción WritePolygonsAsLines para resolver este problema.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
