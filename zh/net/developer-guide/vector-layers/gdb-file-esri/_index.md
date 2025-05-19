---
title: 在 C# 中使用 Esri Gdb 文件格式
linktitle: "GDB ESRI 文件"
type: docs
url: /zh/net/gdb-file-esri/
weight: 80
keywords: esri gdb 文件格式, c# 读取 gdb 文件
description: 使用 GIS C# 库，您可以读取、处理、转换或操作 ESRI File GeoDatabases FileGDB 格式。
---

## **ESRI File GeoDatabases (FileGDB)**
ESRI File GeoDatabases (FileGDB) 是 GIS 软件中最广泛使用的原生格式之一。Aspose.GIS 使您能够使用 FileGDB 文件格式并迭代其要素。
### **迭代 FileGDB 文件中的图层**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-IterateOverLayersInFileGdb.cs" >}}
### **将 FileGDB 转换为 GeoJSON**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-ConvertFeaturesFromFileGdbToGeoJson.cs" >}}
### **将 FileGDB 作为图层读取**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}
### **将 ShapeFile 作为数据集打开**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}
### **将图层添加到 FileGDB 数据集**
打开现有的 FileGDB 数据集并向其中添加新图层

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-AddLayerToFileGdbDataset-AddLayerToFileGdbDataset.cs" >}}
### **从 FileGDB 数据集中删除图层**
打开现有的 FileGDB 数据集并从中删除图层。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-RemoveLayersFromFileGdbDataset-RemoveLayersFromFileGdbDataset.cs" >}}
### **创建 FileGDB 数据集**
创建一个新的 FileGDB 数据集并添加图层到其中。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDataset-CreateFileGdbDataset.cs" >}}
### **使用 VectorLayer API 创建带有单个图层的 FileGDB 数据集**
此示例创建了一个使用 VectorLayer API 的带有单个图层的 FileGDB 数据集。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDatasetWithSingleLayer-CreateFileGdbDatasetWithSingleLayer.cs" >}}
### **将 GeoJSON 图层转换为 FileGDB 数据集图层**
在 FileGDB 中创建新图层，并将来自 GeoJSON 图层的数据添加到其中。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ConvertGeoJsonLayerToLayerInFileGdbDataset-ConvertGeoJsonLayerToLayerInFileGdbDataset.cs" >}}
### **从 FileGDB 数据集图层读取 OBJECTID**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadObjectIdFromFileGdbLayer-ReadObjectIdFromFileGdbLayer.cs" >}}
### **为 FileGDB 图层指定精度网格**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyPrecisionGridForFileGdbLayer-SpecifyPrecisionGridForFileGdbLayer.cs" >}}
### **为 FileGDB 图层指定容差**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyTolerancesForFileGdbLayer-SpecifyTolerancesForFileGdbLayer.cs" >}}
### **指定 ObjectId 和 Geometry 字段的名称**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyNamesOfObjectIdAndGeometryFields-SpecifyNamesOfObjectIdAndGeometryFields.cs" >}}
