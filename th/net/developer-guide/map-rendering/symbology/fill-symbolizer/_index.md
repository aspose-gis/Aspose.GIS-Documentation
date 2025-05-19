---
title: "Fill Symbolizer"
type: docs
url: /th/net/fill-symbolizer/
weight: 30
description: GIS C# Library API รองรับ Simple Fill symbolizer เพื่อเติมสไตล์และขอบสำหรับรูปทรงเรขาคณิต 2 มิติ รูปหลายเหลี่ยมทุกชนิด เช่น จุด เส้น พื้นผิว
---

## **Fill Symbolizer**
Simple Fill symbolizer เติมพื้นที่ด้วยสไตล์การเติมและขอบที่ปรับแต่งได้ นี่คือ symbolizer เริ่มต้นสำหรับรูปทรงเรขาคณิต 2 มิติ (รูปหลายเหลี่ยม) 

หากรูปหลายเหลี่ยมมี “รู” จะไม่ถูกเติม แต่ขอบรอบรูจะถูกขีดเส้นตามปกติ “เกาะ” ภายในรูจะถูกเติมและขีดเส้น และอื่นๆ

ตัวเลือกการจัดรูปแบบที่รองรับ:

|**Property**|**Description**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|ระบุสีและความโปร่งใสที่กำหนดให้กับพื้นที่เติม|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - เติมเต็มด้วยสีทึบ</p><p>- None - ไม่เติมรูปหลายเหลี่ยม</p><p>- Horizontal Hatch - รูปแบบของเส้นแนวนอน</p><p>- Vertical Hatch - รูปแบบของเส้นแนวตั้ง</p><p>- Cross Hatch - ระบุเส้นแนวนอนและแนวตั้งที่ตัดกัน</p><p>- Forward Diagonal Hatch - รูปแบบของเส้นทแยงมุมจากซ้ายบนไปขวาล่าง</p><p>- Backward Diagonal Hatch - รูปแบบของเส้นทแยงมุมจากขวาบนไปซ้ายล่าง</p><p>- Diagonal Cross Hatch - รูปแบบของเส้นทแยงมุมที่ตัดกัน</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|ระบุสีและความโปร่งใสที่กำหนดให้กับเส้นขอบ|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|ระบุวิธีการวาดโครงร่างสัญลักษณ์|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|ระบุความกว้างของเส้นขอบ|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|ระบุอาร์เรย์ของระยะทางที่ระบุความยาวของเส้นประสลับและช่องว่างในเส้นขีด|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|ระบุระยะห่างจากจุดเริ่มต้นของเส้นไปยังจุดเริ่มต้นของรูปแบบเส้นประ|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>กำหนดวิธีการแสดงเส้นที่จุดตัดของส่วนเส้น</p><p>- Miter - มุมแหลม</p><p>- Round - มุมโค้งมน</p><p>- Bevel - มุมเฉียง</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|ระบุค่าออฟเซ็ตแนวนอนจากตำแหน่งจุดไปยังจุดยึดรูปร่าง|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|ระบุค่าออฟเซ็ตแนวตั้งจากตำแหน่งจุดไปยังจุดยึดรูปร่าง|

### **Geometry Types**
` `Symbolizer สามารถใช้กับรูปทรงเรขาคณิตทุกประเภทได้

|**Geometry Dimension**|**Geometry Types**|**Rendering Behavior**|
| :-: | :-: | :-: |
|**Point**|Point, MultiPoint|วาดสี่เหลี่ยมจัตุรัสขนาดเล็ก|
|**Line**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|เส้นจะถูกปิดเพื่อเติมโดยการเชื่อมต่อจุดสิ้นสุดไปยังจุดเริ่มต้น เฉพาะเส้นเดิมเท่านั้นที่ถูกขีดเส้น|
|**Surface**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|วาดรูปหลายเหลี่ยม|

สำหรับ GeometryCollections พฤติกรรมการแสดงผลจะถูกกำหนดแยกกันสำหรับแต่ละรูปทรงเรขาคณิตภายในคอลเลกชัน เลเยอร์ที่มีประเภทรูปทรงเรขาคณิตแบบผสมจะปฏิบัติตามตรรกะสำหรับ GeometryCollections

ใช้ MixedGeometrySymbolizer เพื่อจำกัด symbolizer ให้กับประเภทรูปทรงเรขาคณิตเฉพาะ

### **Examples**
โดยค่าเริ่มต้น Simple Fill symbolizer จะวาดเส้นขอบสีดำและเติมสีขาวทึบ:



Here's how to change styling:




|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

-----
คุณอาจต้องการเพิ่มป้ายกำกับให้กับรูปหลายเหลี่ยมของคุณ เยี่ยมชม [Lines Labeling Examples](/gis/th/net/simple-labeling/#simplelabeling-lineslabelingexamples) สำหรับตัวอย่างวิธีการติดป้ายกำกับขอบรูปหลายเหลี่ยม หรือ [Points Labeling Examples](/gis/th/net/simple-labeling/#simplelabeling-pointslabelingexamples) สำหรับตัวอย่างวิธีการติดป้ายกำกับจุดศูนย์กลางของรูปหลายเหลี่ยม
