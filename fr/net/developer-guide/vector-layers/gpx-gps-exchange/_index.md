---
title: Travailler avec les fichiers au format d'échange GPS GPX en C#
linktitle: GPX - Format d'échange GPS
type: docs
url: /fr/net/gpx-gps-exchange/
weight: 60
description: La bibliothèque GIS C# vous permet d'ouvrir et de lire les entités des fichiers au format d'échange GPS (GPX).
---

## **Travailler avec les fichiers au format d'échange GPS (GPX)**
Aspose.GIS vous permet d'ouvrir et de lire les entités des fichiers au format d'échange GPS (GPX).
## **Lecture des entités à partir d'un fichier GPX**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **Lecture des entités pour chaque point dans un segment**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **Écrire les polygones sous forme de lignes dans un fichier GPX**
Le format GPX ne prend pas en charge les polygones et les multipolygones. Par conséquent, la conversion à partir d'autres formats peut parfois échouer. Vous devez appliquer l'option WritePolygonsAsLines pour résoudre ce problème.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
