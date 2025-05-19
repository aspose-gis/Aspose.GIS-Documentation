---
title: 使用 GIS C# 库处理栅格图层
linktitle: 栅格图层
type: docs
url: /zh/raster-layers/
weight: 20
description: GIS C# 库允许您读取或使用 GeoTIFF 栅格格式，它是 GIS 软件中最广泛使用的栅格格式之一。
---

## **在 GeoTIFF 样本上处理多波段栅格**
GeoTIFF 是 GIS 软件中最广泛使用的栅格格式之一。Aspose.GIS 允许您使用 GeoTIFF 栅格格式。
### **读取多波段栅格中的常规数据**
```csharp
// 读取多波段栅格中的常规数据
```
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-InteractWithRasterFormats-ReadGeneralDataInGeoTiff.cs" >}}
### **逐行读取值**
```csharp
// 逐行读取值
```
{{< gist "evgeniy-timofeev-aspose" "bf3543d44881bfd31b27a80173268d52" "raster-layers-ReadValuesByLine.cs" >}}
### **读取指定类型的数值**
```csharp
// 读取指定类型的数值
```
{{< gist "evgeniy-timofeev-aspose" "bf3543d44881bfd31b27a80173268d52" "raster-layers-ReadValuesWithSpecifiedType.cs" >}}
### **使用 LINQ 或表达式方法分析栅格值**
```csharp
// 使用 LINQ 或表达式方法分析栅格值
```
{{< gist "evgeniy-timofeev-aspose" "bf3543d44881bfd31b27a80173268d52" "raster-layers-ReadValuesByLine.cs" >}}
### **读取 GoeTIFF 中的原始字节**
```csharp
// 读取 GoeTIFF 中的原始字节
```
{{< gist "evgeniy-timofeev-aspose" "bf3543d44881bfd31b27a80173268d52" "raster-layers-ReadRawBytesInGeoTiff.cs" >}}

## **在 Esri ASCII 样本上处理单波段栅格格式**
EsriAscii 格式始终只有一个波段。
### **读取单波段栅格中的常规数据**
```csharp
// 读取单波段栅格中的常规数据
```
{{< gist "evgeniy-timofeev-aspose" "bf3543d44881bfd31b27a80173268d52" "raster-layers-ReadSingleBandEsriAscii.cs" >}}
