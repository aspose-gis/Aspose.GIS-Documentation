---
title: "GPX - GPS Exchange Format"
type: docs
url: /net/gpx-gps-exchange/
weight: 60
---

## **Working with GPS Exchange File (GPX) Files**
Aspose.GIS lets you open and read features from GPS Exchange File (GPX) files. At present, the API doesn't provide the facility to create a new GPX file and only reading is supported.
### **Reading Features from GPX File**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
### **Write Polygons As Lines to GPX File**
GPX format does not support polygons and multipolygons. As result, sometime conversion is failed from other formats. You should apply the WritePolygonsAsLines option to resolve this issue.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}