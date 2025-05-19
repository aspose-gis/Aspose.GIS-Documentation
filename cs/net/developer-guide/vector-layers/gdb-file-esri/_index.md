---
title: Práce se souborovým formátem Esri Gdb v C#
linktitle: "GDB ESRI Soubor"
type: docs
url: /cs/net/gdb-file-esri/
weight: 80
keywords: esri gdb file format, c# read gdb file
description: Pomocí GIS knihovny C# můžete číst, pracovat s, převádět nebo manipulovat se souborovým formátem FileGDB ESRI GeoDatabases.
---

## **ESRI GeoDatabases (FileGDB)**
ESRI GeoDatabases (FileGDB) jsou jedním z nejrozšířenějších nativních formátů mezi GIS softwarem. Aspose.GIS vám umožňuje pracovat se souborovými formáty FileGDB a procházet jeho prvky.
### **Procházení vrstev v souboru FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-IterateOverLayersInFileGdb.cs" >}}
### **Převod FileGDB do GeoJSON**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-ConvertFeaturesFromFileGdbToGeoJson.cs" >}}
### **Čtení FileGDB jako vrstvy**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}
### **Otevření ShapeFile jako Datasetu**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}
### **Přidání vrstvy do FileGDB Datasetu**
Otevře existující FileGDB dataset a přidá do něj nové vrstvy

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-AddLayerToFileGdbDataset-AddLayerToFileGdbDataset.cs" >}}
### **Odebrání vrstvy z FileGDB Datasetu**
Otevře existující FileGDB dataset a odebere z něj vrstvy.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-RemoveLayersFromFileGdbDataset-RemoveLayersFromFileGdbDataset.cs" >}}
### **Vytvoření FileGDB Datasetu**
Vytvoří nový FileGDB dataset a přidá do něj vrstvy.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDataset-CreateFileGdbDataset.cs" >}}
### **Vytvoření FileGDB Datasetu s jednou vrstvou pomocí API VectorLayer**
Tento příklad vytvoří FileGDB dataset s jednou vrstvou pomocí API VectorLayer.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDatasetWithSingleLayer-CreateFileGdbDatasetWithSingleLayer.cs" >}}
### **Převod vrstvy GeoJSON do vrstvy FileGDB Datasetu**
Vytvoří novou vrstvu v FileGDB a přidá do ní data z vrstvy GeoJSON.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ConvertGeoJsonLayerToLayerInFileGdbDataset-ConvertGeoJsonLayerToLayerInFileGdbDataset.cs" >}}
### **Čtení OBJECTID z vrstvy FileGDB Datasetu**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadObjectIdFromFileGdbLayer-ReadObjectIdFromFileGdbLayer.cs" >}}
### **Specifikace mřížky přesnosti pro vrstvu FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyPrecisionGridForFileGdbLayer-SpecifyPrecisionGridForFileGdbLayer.cs" >}}
### **Specifikace tolerancí pro vrstvu FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyTolerancesForFileGdbLayer-SpecifyTolerancesForFileGdbLayer.cs" >}}
### **Specifikace názvů polí ObjectId a Geometry**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyNamesOfObjectIdAndGeometryFields-SpecifyNamesOfObjectIdAndGeometryFields.cs" >}}
