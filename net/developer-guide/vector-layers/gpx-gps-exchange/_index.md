---
title: Work with GPS Exchange Format GPX files in C#
linktitle: GPX - GPS Exchange Format
type: docs
url: /net/gpx-gps-exchange/
weight: 60
description: C# GIS Library lets you open and read features from GPS Exchange File (GPX) files. 
---

## **Working with GPS Exchange File (GPX) Files**
Aspose.GIS lets you open and read features from GPS Exchange File (GPX) files.
## **Reading Features from GPX File**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **Reading Features for each point in segment**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **Write Polygons As Lines to GPX File**
GPX format does not support polygons and multipolygons. As result, sometime conversion is failed from other formats. You should apply the WritePolygonsAsLines option to resolve this issue.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
