---
title: C#에서 Esri Gdb 파일 형식으로 작업하기
linktitle: "GDB ESRI 파일"
type: docs
url: /ko/net/gdb-file-esri/
weight: 80
keywords: esri gdb 파일 형식, c# gdb 파일 읽기
description: GIS C# 라이브러리를 사용하면 ESRI File GeoDatabases FileGDB 형식을 읽고 작업하고 변환하거나 조작할 수 있습니다.
---

## **ESRI File GeoDatabases (FileGDB)**
ESRI File GeoDatabases (FileGDB)는 GIS 소프트웨어에서 가장 널리 사용되는 기본 형식 중 하나입니다. Aspose.GIS를 사용하면 FileGDB 파일 형식을 작업하고 해당 기능을 반복할 수 있습니다.

### **FileGDB 파일의 레이어 반복**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-IterateOverLayersInFileGdb.cs" >}}

### **FileGDB를 GeoJSON으로 변환**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-ConvertFeaturesFromFileGdbToGeoJson.cs" >}}

### **레이어로 FileGDB 읽기**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}

### **ShapeFile을 데이터 세트로 열기**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}

### **FileGDB 데이터 세트에 레이어 추가**
기존 FileGDB 데이터 세트를 열고 새 레이어를 추가합니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-AddLayerToFileGdbDataset-AddLayerToFileGdbDataset.cs" >}}

### **FileGDB 데이터 세트에서 레이어 제거**
기존 FileGDB 데이터 세트를 열고 해당 레이어를 제거합니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-RemoveLayersFromFileGdbDataset-RemoveLayersFromFileGdbDataset.cs" >}}

### **FileGDB 데이터 세트 만들기**
새 FileGDB 데이터 세트를 만들고 레이어를 추가합니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDataset-CreateFileGdbDataset.cs" >}}

### **VectorLayer API를 사용하여 단일 레이어가 있는 FileGDB 데이터 세트 만들기**
이 예제는 VectorLayer API를 사용하여 단일 레이어가 있는 FileGDB 데이터 세트를 만듭니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDatasetWithSingleLayer-CreateFileGdbDatasetWithSingleLayer.cs" >}}

### **GeoJSON 레이어를 FileGDB 데이터 세트 레이어로 변환**
FileGDB에 새 레이어를 만들고 GeoJSON 레이어의 데이터를 추가합니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ConvertGeoJsonLayerToLayerInFileGdbDataset-ConvertGeoJsonLayerToLayerInFileGdbDataset.cs" >}}

### **FileGDB 데이터 세트 레이어에서 OBJECTID 읽기**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadObjectIdFromFileGdbLayer-ReadObjectIdFromFileGdbLayer.cs" >}}

### **FileGDB 레이어에 대한 정밀도 그리드 지정**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyPrecisionGridForFileGdbLayer-SpecifyPrecisionGridForFileGdbLayer.cs" >}}

### **FileGDB 레이어에 대한 허용 오차 지정**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyTolerancesForFileGdbLayer-SpecifyTolerancesForFileGdbLayer.cs" >}}

### **ObjectId 및 Geometry 필드 이름 지정**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyNamesOfObjectIdAndGeometryFields-SpecifyNamesOfObjectIdAndGeometryFields.cs" >}}
