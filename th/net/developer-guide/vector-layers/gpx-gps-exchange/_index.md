---
title: ทำงานกับไฟล์รูปแบบการแลกเปลี่ยน GPS (GPX) ใน C#
linktitle: GPX - รูปแบบการแลกเปลี่ยน GPS
type: docs
url: /th/net/gpx-gps-exchange/
weight: 60
description: ไลบรารี GIS ของ C# ช่วยให้คุณเปิดและอ่านคุณสมบัติจากไฟล์รูปแบบการแลกเปลี่ยน GPS (GPX) ได้
---

## **ทำงานกับไฟล์รูปแบบการแลกเปลี่ยน GPS (GPX)**
Aspose.GIS ช่วยให้คุณเปิดและอ่านคุณสมบัติจากไฟล์รูปแบบการแลกเปลี่ยน GPS (GPX) ได้
## **อ่านคุณสมบัติจากไฟล์ GPX**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **อ่านคุณสมบัติสำหรับแต่ละจุดในส่วน**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **เขียนรูปหลายเหลี่ยมเป็นเส้นไปยังไฟล์ GPX**
รูปแบบ GPX ไม่รองรับรูปหลายเหลี่ยมและรูปหลายเหลี่ยมซ้อนกัน เป็นผลให้บางครั้งการแปลงจากรูปแบบอื่นอาจล้มเหลว คุณควรใช้ตัวเลือก WritePolygonsAsLines เพื่อแก้ไขปัญหานี้
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
