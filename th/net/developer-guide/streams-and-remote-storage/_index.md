---
title: "Streams และที่เก็บข้อมูลระยะไกล"
type: docs
url: /th/net/streams-and-remote-storage/
weight: 70
---

## **การทำงานกับรูปแบบไฟล์หลายไฟล์**
รูปแบบข้อมูล GIS บางรูปแบบแบ่งเนื้อหาออกเป็นหลายไฟล์ ตัวอย่างเช่น shapefile ต้องมีอย่างน้อยสามไฟล์: *.shp, *.shx และ *.dbf รูปแบบเหล่านี้ต้องการให้จัดเก็บไฟล์ทั้งหมดในโครงสร้างไดเรกทอรีเฉพาะด้วยรูปแบบที่กำหนดไว้ล่วงหน้าสำหรับชื่อไฟล์

ในขณะเดียวกัน ไฟล์อาจถูกจัดเก็บบนเซิร์ฟเวอร์ระยะไกล หรือตำแหน่งอื่นที่เข้าถึงได้ผ่านสตรีมเท่านั้น สตรีมไม่มีข้อมูลเกี่ยวกับชื่อไฟล์และโครงสร้างไดเรกทอรี ทำให้ไม่สามารถให้ไดรเวอร์รูปแบบไฟล์ระบุวิธีการประมวลผลข้อมูลได้ Aspose.GIS แก้ปัญหานี้โดยการจัดเตรียมกลไกพาธแบบนามธรรม

พาธแบบนามธรรมแสดงถึงพาธไปยังไฟล์ (หรือไดเรกทอรี) ในที่เก็บข้อมูลที่เหมือนระบบไฟล์ ที่เก็บข้อมูลอาจเป็นอะไรก็ได้ที่มีแนวคิดของไฟล์และไดเรกทอรี ตั้งแต่คลังเก็บไปจนถึงเซิร์ฟเวอร์ FTP มันกำหนดวิธีการดำเนินการปฏิบัติการไฟล์ทั่วไป เช่น การเปิดไฟล์หรือแสดงรายการไดเรกทอรี

คุณสามารถระบุวิธีดำเนินการปฏิบัติการไฟล์สำหรับที่เก็บข้อมูลของคุณได้โดยการใช้งานคลาสที่สืบทอด [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) และให้การใช้งานสำหรับวิธีการแบบนามธรรมของมัน
## **ตัวอย่าง: Azure Blob Storage**
Aspose.GIS Examples repository มีตัวอย่างการใช้งานพาธแบบนามธรรมที่สมบูรณ์แบบสำหรับการจัดเก็บข้อมูล Azure Blob ตัวอย่างนี้แสดงวิธีอ่าน shapefile โดยตรงจาก Azure Blob Storage คุณสามารถค้นหาได้ที่นี่: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **รูปแบบไฟล์เดียว (GeoJSON, KML)**
รูปแบบข้อมูล GIS เช่น GeoJSON และ KML สามารถจัดเก็บข้อมูลทั้งหมดสำหรับเลเยอร์ในไฟล์เดียวได้ หากคุณสามารถรับสตรีมสำหรับไฟล์ได้ คุณสามารถข้ามการใช้งานพาธแบบนามธรรมที่กำหนดเองและใช้เมธอด [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) เพื่อสร้างอินสแตนซ์ของพาธแบบนามธรรมสำหรับสตรีม
### **อ่านไฟล์จากสตรีม**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **เขียนไฟล์ไปยังสตรีม**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
