---
title: C# ile Esri Gdb dosya formatıyla çalışın
linktitle: "GDB ESRI Dosyası"
type: docs
url: /tr/net/gdb-file-esri/
weight: 80
keywords: esri gdb file format, c# read gdb file
description: GIS C# kütüphanesi kullanarak, ESRI File GeoDatabases FileGDB formatını okuyabilir, üzerinde çalışabilir, dönüştürebilir veya manipüle edebilirsiniz.
---

## **ESRI File GeoDatabases (FileGDB)**
ESRI File GeoDatabases (FileGDB), GIS Yazılımları arasında en yaygın kullanılan yerel formatlardan biridir. Aspose.GIS, FileGDB dosya formatlarıyla çalışmanıza ve özelliklerini yinelemenize olanak tanır.

### **FileGDB Dosyasındaki Katmanlar Üzerinde Yineleme**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-IterateOverLayersInFileGdb.cs" >}}

### **FileGDB'yi GeoJSON'a Dönüştür**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-ConvertFeaturesFromFileGdbToGeoJson.cs" >}}

### **FileGDB'yi Katman Olarak Okuma**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}

### **ShapeFile'ı Veri Kümesi Olarak Açma**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}

### **FileGDB Veri Kümesine Katman Ekleme**
Mevcut FileGDB veri kümesini açar ve içine yeni katmanlar ekler.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-AddLayerToFileGdbDataset-AddLayerToFileGdbDataset.cs" >}}

### **FileGDB Veri Kümesinden Katmanı Kaldırma**
Mevcut bir FileGDB veri kümesini açar ve içindeki katmanları kaldırır.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-RemoveLayersFromFileGdbDataset-RemoveLayersFromFileGdbDataset.cs" >}}

### **FileGDB Veri Kümesi Oluşturma**
Yeni bir FileGDB veri kümesi oluşturur ve içine katmanlar ekler.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDataset-CreateFileGdbDataset.cs" >}}

### **VectorLayer API'sini Kullanarak Tek Katmanlı FileGDB Veri Kümesi Oluşturma**
Bu örnek, VectorLayer API’sini kullanarak tek katmanlı bir FileGDB veri kümesi oluşturur.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDatasetWithSingleLayer-CreateFileGdbDatasetWithSingleLayer.cs" >}}

### **GeoJSON Katmanını FileGDB Veri Kümesi Katmanına Dönüştürme**
FileGDB'de yeni bir katman oluşturun ve GeoJSON Katmanından verileri içine ekleyin.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ConvertGeoJsonLayerToLayerInFileGdbDataset-ConvertGeoJsonLayerToLayerInFileGdbDataset.cs" >}}

### **FileGDB Veri Kümesi Katmanından OBJECTID'yi Okuma**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadObjectIdFromFileGdbLayer-ReadObjectIdFromFileGdbLayer.cs" >}}

### **FileGDB Katmanı için Hassasiyet Izgarası Belirleme**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyPrecisionGridForFileGdbLayer-SpecifyPrecisionGridForFileGdbLayer.cs" >}}

### **FileGDB Katmanı için Toleransları Belirleme**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyTolerancesForFileGdbLayer-SpecifyTolerancesForFileGdbLayer.cs" >}}

### **ObjectId ve Geometri Alanlarının Adlarını Belirleme**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyNamesOfObjectIdAndGeometryFields-SpecifyNamesOfObjectIdAndGeometryFields.cs" >}}
