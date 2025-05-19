---
title: Работа с файловым форматом Esri Gdb в C#
linktitle: "GDB ESRI File"
type: docs
url: /ru/net/gdb-file-esri/
weight: 80
keywords: esri gdb file format, c# read gdb file
description: Используя GIS C# библиотеку, вы можете читать, работать, конвертировать или манипулировать файлами GeoDatabases FileGDB формата ESRI.
---

## **Файловые Геобазы Данных ESRI (FileGDB)**
Файловые Геобазы Данных ESRI (FileGDB) являются одним из наиболее широко используемых нативных форматов среди GIS-программного обеспечения. Aspose.GIS позволяет вам работать с файлами формата FileGDB и перебирать его объекты.

### **Перебор слоев в файле FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-IterateOverLayersInFileGdb.cs" >}}

### **Конвертация FileGDB в GeoJSON**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-ConvertFeaturesFromFileGdbToGeoJson.cs" >}}

### **Чтение FileGDB как слоя**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}

### **Открытие ShapeFile как набора данных**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}

### **Добавление слоя в набор данных FileGDB**
Откройте существующий набор данных FileGDB и добавьте новые слои в него.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-AddLayerToFileGdbDataset-AddLayerToFileGdbDataset.cs" >}}

### **Удаление слоя из набора данных FileGDB**
Откройте существующий набор данных FileGDB и удалите слои из него.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-RemoveLayersFromFileGdbDataset-RemoveLayersFromFileGdbDataset.cs" >}}

### **Создание набора данных FileGDB**
Создает новый набор данных FileGDB и добавляет слои в него.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDataset-CreateFileGdbDataset.cs" >}}

### **Создание набора данных FileGDB с одним слоем, используя API VectorLayer**
Этот пример создает набор данных FileGDB с одним слоем, используя API VectorLayer.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDatasetWithSingleLayer-CreateFileGdbDatasetWithSingleLayer.cs" >}}

### **Конвертация слоя GeoJSON в слой набора данных FileGDB**
Создайте новый слой в FileGDB и добавьте данные из слоя GeoJSON в него.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ConvertGeoJsonLayerToLayerInFileGdbDataset-ConvertGeoJsonLayerToLayerInFileGdbDataset.cs" >}}

### **Чтение OBJECTID из слоя набора данных FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadObjectIdFromFileGdbLayer-ReadObjectIdFromFileGdbLayer.cs" >}}

### **Указание сетки точности для слоя FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyPrecisionGridForFileGdbLayer-SpecifyPrecisionGridForFileGdbLayer.cs" >}}

### **Указание допусков для слоя FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyTolerancesForFileGdbLayer-SpecifyTolerancesForFileGdbLayer.cs" >}}

### **Указание имен полей ObjectId и Geometry**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyNamesOfObjectIdAndGeometryFields-SpecifyNamesOfObjectIdAndGeometryFields.cs" >}}
