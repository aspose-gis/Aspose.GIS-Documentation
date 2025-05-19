---
title: "Marker Cluster Symbolizer"
type: docs
url: /th/net/marker-cluster-symbolizer/
weight: 65
description: Marker Cluster Symbolizer ใน GIS C# Library หรือ API ช่วยให้สามารถจัดกลุ่มมาร์กเกอร์ในระยะที่กำหนดได้
---

## **Marker Cluster Symbolizer**
Marker Cluster Symbolizer เป็นหนึ่งใน symbolizers ขั้นสูง มันช่วยให้สามารถจัดกลุ่มมาร์กเกอร์ในระยะที่กำหนดได้

ในตัวอย่าง C# นี้ เราได้วาดจุดศูนย์กลางของคลัสเตอร์เป็นวงกลมสีแดง นอกจากนี้เรายังได้วาดจุดคลัสเตอร์ทั้งหมดโดยใช้สีต่างๆ ในการทำเช่นนี้ เราใช้ฟังก์ชัน FeaturesBasedConfiguration ซึ่งตั้งค่ารูปแบบของแต่ละคลัสเตอร์

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterMarkerSymbolizer.cs" >}}

นี่คือผลลัพธ์:

![points cluster](points-cluster.png)

## **Draw Total Of Items**

ตัวอย่างนี้แสดงจำนวนรวมของรายการในคลัสเตอร์

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterTextSymbolizer.cs" >}}

นี่คือผลลัพธ์:

![digits cluster](digits-cluster.png)
