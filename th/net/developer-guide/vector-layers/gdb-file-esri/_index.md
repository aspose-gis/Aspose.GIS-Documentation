---
title: ทำงานกับรูปแบบไฟล์ Esri Gdb ใน C#
linktitle: "GDB ESRI File"
type: docs
url: /th/net/gdb-file-esri/
weight: 80
keywords: รูปแบบไฟล์ esri gdb, อ่านไฟล์ gdb c#
description: การใช้ไลบรารี GIS C# คุณสามารถอ่าน ทำงาน แปลง หรือจัดการรูปแบบไฟล์ FileGDB ของ ESRI File GeoDatabases ได้
---

## **ESRI File GeoDatabases (FileGDB)**
ESRI File GeoDatabases (FileGDB) เป็นหนึ่งในรูปแบบดั้งเดิมที่ใช้กันอย่างแพร่หลายที่สุดในซอฟต์แวร์ GIS Aspose.GIS ช่วยให้คุณทำงานกับรูปแบบไฟล์ FileGDB และวนซ้ำคุณสมบัติของมันได้

### **วนซ้ำเลเยอร์ในไฟล์ FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-IterateOverLayersInFileGdb.cs" >}}

### **แปลง FileGDB เป็น GeoJSON**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-ConvertFeaturesFromFileGdbToGeoJson.cs" >}}

### **อ่าน FileGDB เป็นเลเยอร์**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}

### **เปิด ShapeFile เป็นชุดข้อมูล**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}

### **เพิ่มเลเยอร์ลงในชุดข้อมูล FileGDB**
เปิดชุดข้อมูล FileGDB ที่มีอยู่และเพิ่มเลเยอร์ใหม่เข้าไป

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-AddLayerToFileGdbDataset-AddLayerToFileGdbDataset.cs" >}}

### **ลบเลเยอร์ออกจากชุดข้อมูล FileGDB**
เปิดชุดข้อมูล FileGDB ที่มีอยู่และลบเลเยอร์ออกจากมัน

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-RemoveLayersFromFileGdbDataset-RemoveLayersFromFileGdbDataset.cs" >}}

### **สร้างชุดข้อมูล FileGDB**
สร้างชุดข้อมูล FileGDB ใหม่และเพิ่มเลเยอร์เข้าไป

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDataset-CreateFileGdbDataset.cs" >}}

### **สร้างชุดข้อมูล FileGDB พร้อมเลเยอร์เดียวโดยใช้ VectorLayer API**
ตัวอย่างนี้สร้างชุดข้อมูล FileGDB ที่มีเลเยอร์เดียวโดยใช้ VectorLayer API

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDatasetWithSingleLayer-CreateFileGdbDatasetWithSingleLayer.cs" >}}

### **แปลงเลเยอร์ GeoJSON เป็นเลเยอร์ชุดข้อมูล FileGDB**
สร้างเลเยอร์ใหม่ใน FileGDB และเพิ่มข้อมูลจากเลเยอร์ GeoJSON เข้าไป

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ConvertGeoJsonLayerToLayerInFileGdbDataset-ConvertGeoJsonLayerToLayerInFileGdbDataset.cs" >}}

### **อ่าน OBJECTID จากเลเยอร์ชุดข้อมูล FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadObjectIdFromFileGdbLayer-ReadObjectIdFromFileGdbLayer.cs" >}}

### **ระบุ Grid ความแม่นยำสำหรับเลเยอร์ FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyPrecisionGridForFileGdbLayer-SpecifyPrecisionGridForFileGdbLayer.cs" >}}

### **ระบุค่าความคลาดเคลื่อนสำหรับเลเยอร์ FileGDB**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyTolerancesForFileGdbLayer-SpecifyTolerancesForFileGdbLayer.cs" >}}

### **ระบุชื่อของฟิลด์ ObjectId และ Geometry**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyNamesOfObjectIdAndGeometryFields-SpecifyNamesOfObjectIdAndGeometryFields.cs" >}}
