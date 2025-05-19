---
title: 在 C# 中使用 GPS 交换格式 GPX 文件
linktitle: GPX - GPS 交换格式
type: docs
url: /zh/net/gpx-gps-exchange/
weight: 60
description: C# GIS 库允许您打开并读取来自 GPS 交换文件 (GPX) 的要素。
---

## **使用 GPS 交换文件 (GPX) 文件**
Aspose.GIS 允许您打开并读取来自 GPS 交换文件 (GPX) 的要素。
## **从 GPX 文件读取要素**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **读取段中每个点的要素**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **将多边形作为线条写入 GPX 文件**
GPX 格式不支持多边形和多重多边形。因此，从其他格式的转换有时会失败。您应该应用 WritePolygonsAsLines 选项来解决此问题。
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
