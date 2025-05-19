---
title: "สัญลักษณ์เครื่องหมาย"
type: docs
url: /th/net/marker-symbolizer/
weight: 10
description: GIS C# Library หรือ API รองรับสัญลักษณ์เครื่องหมายแบบง่ายที่วาดรูปทรงที่กำหนดไว้ล่วงหน้าด้วยการเติมและขอบที่ปรับแต่งได้บนเรขาคณิตทุกประเภท เช่น จุด เส้น พื้นผิว
---

## **สัญลักษณ์เครื่องหมาย**
สัญลักษณ์เครื่องหมายแบบง่ายจะวาดรูปทรงที่กำหนดไว้ล่วงหน้าด้วยการเติมและขอบที่ปรับแต่งได้ นี่คือสัญลักษณ์เริ่มต้นสำหรับเรขาคณิต 0 มิติ (จุด) 

รูปทรงที่รองรับมีดังนี้:

|![todo:image_alt_text](marker-symbolizer_1.png)|วงกลม| |![todo:image_alt_text](marker-symbolizer_2.png)|ดาว|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|สี่เหลี่ยมจัตุรัส| |![todo:image_alt_text](marker-symbolizer_4.png)|กากบาท|
|![todo:image_alt_text](marker-symbolizer_5.png)|สามเหลี่ยม| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

ตัวเลือกการจัดรูปแบบที่รองรับ:

|**คุณสมบัติ**|**คำอธิบาย**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|ระบุรูปทรงของเครื่องหมาย|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|ระบุขนาดของรูปทรงเครื่องหมาย|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|ระบุสีและความโปร่งใสที่กำหนดให้กับการเติม|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|ระบุสีและความโปร่งใสที่กำหนดให้กับเส้น|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|ระบุความกว้างของเส้น|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|กำหนดวิธีการแสดงเส้นที่จุดตัดของส่วนของเส้น|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|ระบุวิธีการวาดภาพเส้นสัญลักษณ์|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|ระบุอาร์เรย์ของระยะทางที่ระบุความยาวของเส้นประและช่องว่างในเส้นขีด|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|ระบุระยะห่างจากจุดเริ่มต้นของเส้นไปยังจุดเริ่มต้นของรูปแบบเส้นประ|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|ระบุการหมุนของสัญลักษณ์รอบจุดศูนย์กลางในองศาเดซิมอล ค่าบวกแสดงถึงการหมุนตามเข็มนาฬิกา ค่าลบแสดงถึงการหมุนทวนเข็มนาฬิกา ค่าเริ่มต้นคือ 0|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|ระบุค่าออฟเซ็ตแนวนอนจากตำแหน่งจุดไปยังจุดยึดรูปร่าง|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|ระบุค่าออฟเซ็ตแนวตั้งจากตำแหน่งจุดไปยังจุดยึดรูปร่าง|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|ระบุด้านใดของรูปทรงเครื่องหมายที่จะจัดเรียงแนวนอนกับตำแหน่งจุด|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|ระบุด้านใดของรูปทรงเครื่องหมายที่จะจัดเรียงแนวตั้งกับตำแหน่งจุด|

### **ประเภทเรขาคณิต**
` `สัญลักษณ์สามารถใช้กับเรขาคณิตทุกประเภทได้

|**มิติเรขาคณิต**|**ประเภทเรขาคณิต**|**พฤติกรรมการแสดงผล**|
| :-: | :-: | :-: |
|**จุด**|Point, MultiPoint|วาดรูปทรงโดยกึ่งกลางที่พิกัดของจุด|
|**เส้น**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>วาดรูปทรงโดยกึ่งกลางที่จุดศูนย์ถ่วงของเรขาคณิต</p><p> </p>|
|**พื้นผิว**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

สำหรับ GeometryCollections พฤติกรรมการแสดงผลจะถูกกำหนดแยกกันสำหรับแต่ละเรขาคณิตภายในคอลเลกชัน เลเยอร์ที่มีประเภทเรขาคณิตแบบผสมตามตรรกะสำหรับ GeometryCollections

ใช้ MixedGeometrySymbolizer เพื่อจำกัดสัญลักษณ์ให้กับประเภทเรขาคณิตเฉพาะ

### **ตัวอย่าง**
โดยค่าเริ่มต้น สัญลักษณ์เครื่องหมายจะวาดวงกลมสีดำ:



นี่คือวิธีการเปลี่ยนสีเติมเป็นสีแดง:




|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

ตัวอย่างอื่นของการจัดรูปแบบด้วยรูปทรงที่กำหนดไว้ล่วงหน้า (สามเหลี่ยม):




|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----
สำหรับสถานการณ์ขั้นสูง คุณอาจต้องการปรับรูปแบบเครื่องหมายแบบไดนามิกตามค่าคุณลักษณะของฟีเจอร์ นี่คือวิธีการทำเช่นนั้น:




|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
คุณอาจต้องการเพิ่มป้ายกำกับให้กับเครื่องหมายของคุณ ไปที่ [ตัวอย่างการติดป้ายจุด](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) สำหรับตัวอย่าง
