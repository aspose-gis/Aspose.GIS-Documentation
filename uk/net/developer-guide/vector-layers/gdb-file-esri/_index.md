---
title: Робота з файловим форматом Esri Gdb у C#
linktitle: "GDB ESRI Файл"
type: docs
url: /uk/net/gdb-file-esri/
weight: 80
keywords: esri gdb file format, c# read gdb file
description: Використовуючи GIS C# бібліотеку, ви можете читати, працювати, конвертувати або маніпулювати файлами GeoDatabases FileGDB ESRI.
---

## **ESRI File GeoDatabases (FileGDB)**
ESRI File GeoDatabases (FileGDB) є одним з найбільш широко використовуваних власних форматів серед GIS програмного забезпечення. Aspose.GIS дозволяє вам працювати з файловими форматами FileGDB та перебирати його фічі.
### **Перебір шарів у файлі FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-IterateOverLayersInFileGdb.cs" >}}
### **Конвертація FileGDB у GeoJSON**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-ConvertFeaturesFromFileGdbToGeoJson.cs" >}}
### **Читання FileGDB як шар**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}
### **Відкриття ShapeFile як набір даних**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}
### **Додавання шару до набору даних FileGDB**
Відкрийте існуючий набір даних FileGDB та додайте нові шари до нього

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-AddLayerToFileGdbDataset-AddLayerToFileGdbDataset.cs" >}}
### **Видалення шару з набору даних FileGDB**
Відкрийте існуючий набір даних FileGDB та видаліть шари з нього.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-RemoveLayersFromFileGdbDataset-RemoveLayersFromFileGdbDataset.cs" >}}
### **Створення набору даних FileGDB**
Створює новий набір даних FileGDB та додає шари до нього.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDataset-CreateFileGdbDataset.cs" >}}
### **Створення набору даних FileGDB з одним шаром за допомогою VectorLayer API**
Цей приклад створює набір даних FileGDB з одним шаром, використовуючи VectorLayer API.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDatasetWithSingleLayer-CreateFileGdbDatasetWithSingleLayer.cs" >}}
### **Конвертація GeoJSON шару в шар набору даних FileGDB**
Створіть новий шар у FileGDB та додайте дані з GeoJSON шару до нього.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ConvertGeoJsonLayerToLayerInFileGdbDataset-ConvertGeoJsonLayerToLayerInFileGdbDataset.cs" >}}
### **Читання OBJECTID з шару набору даних FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadObjectIdFromFileGdbLayer-ReadObjectIdFromFileGdbLayer.cs" >}}
### **Вкажіть сітку точності для шару FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyPrecisionGridForFileGdbLayer-SpecifyPrecisionGridForFileGdbLayer.cs" >}}
### **Вкажіть допуски для шару FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyTolerancesForFileGdbLayer-SpecifyTolerancesForFileGdbLayer.cs" >}}
### **Вкажіть імена полів ObjectId та Geometry**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyNamesOfObjectIdAndGeometryFields-SpecifyNamesOfObjectIdAndGeometryFields.cs" >}}
