---
title: "สัญลักษณ์เส้น"
type: docs
url: /th/net/line-symbolizer/
weight: 20
description: ไลบรารี GIS C# หรือ API รองรับสัญลักษณ์เส้นแบบง่ายสำหรับรูปทรงเรขาคณิต 1 มิติ เส้น และสามารถใช้กับรูปทรงเรขาคณิตทุกประเภท เช่น จุด เส้น พื้นผิว
---

## **สัญลักษณ์เส้น**
สัญลักษณ์เส้นแบบง่ายจะวาดเส้นด้วยรูปแบบที่ปรับแต่งได้ นี่คือสัญลักษณ์เริ่มต้นสำหรับรูปทรงเรขาคณิต 1 มิติ (เส้น) 

ตัวเลือกการจัดรูปแบบที่รองรับ:

|**คุณสมบัติ**|**คำอธิบาย**|
| :- | :- |
|[Color](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|ระบุสีและความโปร่งใสที่กำหนดให้กับเส้น|
|[Width](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|ระบุความกว้างของเส้น|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|กำหนดวิธีการแสดงเส้นที่จุดตัดของส่วนเส้น|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|ระบุวิธีการวาดโครงร่างสัญลักษณ์|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|ระบุอาร์เรย์ของระยะทางที่ระบุความยาวของเส้นประและช่องว่างสลับกันในเส้นขีด|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|ระบุระยะห่างจากจุดเริ่มต้นของเส้นไปยังจุดเริ่มต้นของรูปแบบเส้นประ|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>ระบุวิธีการแสดงเส้นที่ปลาย</p><p>- Butt - ขอบสี่เหลี่ยมคมชัด</p><p>- Round - ขอบโค้งมน</p><p>- Square - ขอบสี่เหลี่ยมจัตุรัสยาวเล็กน้อย</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|ระบุการชดเชยจากเส้นเดิม สำหรับระยะทางที่เป็นบวก การชดเชยจะอยู่ด้านซ้ายของเส้น (เมื่อเทียบกับทิศทางของเส้น) สำหรับระยะทางที่เป็นลบ จะอยู่ด้านขวา|

### **ประเภทรูปทรงเรขาคณิต**
` `สัญลักษณ์สามารถใช้กับรูปทรงเรขาคณิตทุกประเภทได้

|**มิติรูปทรงเรขาคณิต**|**ประเภทรูปทรงเรขาคณิต**|**พฤติกรรมการแสดงผล**|
| :-: | :-: | :-: |
|**จุด**|Point, MultiPoint|วาดเส้นที่มีความยาวเล็กน้อยโดยมีการวางแนวในแนวนอนซึ่งอยู่ตรงกลางจุด โดยมีฝาปิดสองอัน|
|**เส้น**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|วาดเส้น|
|**พื้นผิว**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|โครงร่างที่ปิดของรูปทรงเรขาคณิตใช้เป็นเส้นสตริง (ไม่มีฝาปิด)|

สำหรับ GeometryCollections พฤติกรรมการแสดงผลจะถูกกำหนดแยกกันสำหรับแต่ละรูปทรงเรขาคณิตภายในคอลเลกชัน เลเยอร์ที่มีประเภทรูปทรงเรขาคณิตแบบผสมผสานจะปฏิบัติตามตรรกะสำหรับ GeometryCollections

ใช้ MixedGeometrySymbolizer เพื่อจำกัดสัญลักษณ์ให้กับประเภทรูปทรงเรขาคณิตเฉพาะ

### **ตัวอย่าง**
โดยค่าเริ่มต้น สัญลักษณ์เส้นจะวาดเส้นสีดำ:



นี่คือวิธีการเปลี่ยนสีเส้นเป็นสีน้ำเงิน:




|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

สำหรับสถานการณ์ขั้นสูง คุณอาจต้องการปรับรูปแบบเส้นแบบไดนามิกตามค่าคุณลักษณะของฟีเจอร์ นี่คือวิธีการทำเช่นนั้น:




|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |

คุณอาจต้องการเพิ่มป้ายกำกับให้กับเส้นของคุณ เยี่ยมชม [ตัวอย่างการติดป้ายเส้น](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) สำหรับตัวอย่าง
