---
title: สัญลักษณ์ - C# GIS API
linktitle: "สัญลักษณ์"
type: docs
url: /th/net/symbology/
weight: 10
description: ห้องสมุดหรือ API ของ GIS C# รองรับตัวสร้างสัญลักษณ์เพื่อวาดเรขาคณิตของฟีเจอร์ เช่น มาร์กเกอร์ เส้น เติม และการรวมตัวสร้างสัญลักษณ์เพื่อสร้างภาพที่ซับซ้อนยิ่งขึ้น
---

ตัวสร้างสัญลักษณ์คือวิธีการวาดเรขาคณิตของฟีเจอร์บนแผนที่

|** **|**ตัวสร้างสัญลักษณ์**|**API Class**|**คำอธิบาย**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**มาร์กเกอร์**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|วาดรูปร่างที่กำหนดไว้ล่วงหน้าด้วยการเติมและขอบที่ปรับแต่งได้|
|![todo:image_alt_text](symbology_2.png)|**เส้น**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|วาดเส้นด้วยรูปแบบที่ปรับแต่งได้|
|![todo:image_alt_text](symbology_3.png)|**เติม**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|เติมรูปหลายเหลี่ยมหรือพื้นที่ที่ล้อมรอบด้วยเส้นด้วยการเติมและขอบที่ปรับแต่งได้|
นอกจากตัวสร้างสัญลักษณ์ที่ทำการวาดจริงแล้ว ยังมีจำนวนของตัวสร้างสัญลักษณ์อื่นๆ ที่ช่วยให้สามารถรวมตัวสร้างสัญลักษณ์อื่น ๆ เพื่อสร้างภาพที่ซับซ้อนยิ่งขึ้น

|**ตัวสร้างสัญลักษณ์**|**API Class**|**คำอธิบาย**|
| :- | :- | :- |
|**ตัวสร้างสัญลักษณ์แบบแบ่งชั้น**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|วาดฟีเจอร์ด้วยตัวสร้างสัญลักษณ์หลายตัวซ้อนกัน|
|**ตัวสร้างสัญลักษณ์เรขาคณิตแบบผสม**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|วาดฟีเจอร์จากเลเยอร์ที่มีเรขาคณิตประเภทต่างๆ ด้วยตัวสร้างสัญลักษณ์เฉพาะสำหรับแต่ละประเภทของเรขาคณิต|
|**ตัวสร้างสัญลักษณ์ตามกฎ**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|เลือกตัวสร้างสัญลักษณ์ที่จะใช้กับฟีเจอร์โดยกฎที่ผู้ใช้ระบุ|
|**ตัวสร้างสัญลักษณ์กลุ่มมาร์กเกอร์**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|วาดการจัดกลุ่มของมาร์กเกอร์ การจัดกลุ่มรายการเหล่านี้|
|**ตัวสร้างเรขาคณิต**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|อนุญาตให้แทนที่เรขาคณิตของฟีเจอร์ก่อนการแสดงผล|
|**ตัวสร้างสัญลักษณ์ว่าง**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|ไม่วาดอะไรเลย มีประโยชน์เมื่อใช้ร่วมกับตัวสร้างสัญลักษณ์อื่น ๆ เช่น ตัวสร้างสัญลักษณ์ตามกฎ|
