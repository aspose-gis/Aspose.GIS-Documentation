---
title: "การติดป้ายแบบง่าย"
type: docs
url: /th/net/simple-labeling/
weight: 10
---

## **การติดป้ายแบบง่าย**
การติดป้ายแบบง่ายจะระบุวิธีการที่ต้องติดป้ายคุณสมบัติ

ตัวเลือกที่รองรับคือ:

|**คุณสมบัติ**|**คำอธิบาย**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|ระบุชื่อคุณสมบัติที่จะใช้เป็นแหล่งที่มาของป้าย|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|ให้วิธีในการปรับแต่งและจัดรูปแบบข้อความป้าย ยกเลิก LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|ระบุครอบครัวแบบอักษรที่จะใช้เพื่อแสดงข้อความ ค่าเริ่มต้นขึ้นอยู่กับระบบ|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>รูปแบบที่จะใช้กับข้อความ</p><p>- FontStyle.Regular - ข้อความปกติ</p><p>- FontStyle.Bold - ข้อความตัวหนา</p><p>- FontStyle.Italic - ข้อความตัวเอียง</p><p>- FontStyle.Underine - ข้อความขีดเส้นใต้</p><p>- FontStyle.StrikeOut - ข้อความที่มีเส้นผ่านกลาง</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|ระบุขนาดของข้อความ|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|กำหนดสีของข้อความ|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|กำหนดขนาดของรัศมี (หรือขอบ) รอบข้อความ|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|กำหนดสีของรัศมีรอบข้อความ|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|นิพจน์เรขาคณิตที่จะใช้เพื่อแปลงรูปทรงก่อนส่งไปยังเอนจินการติดป้าย|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>ระบุพฤติกรรมการแสดงผลสำหรับรูปทรงหลายส่วน</p><p>- MultipartMode.All - วางป้ายใกล้ทุกส่วนของรูปทรงเรขาคณิต</p><p>- MultipartMode.Any - วางป้ายหนึ่งอันใกล้กับส่วนใดส่วนหนึ่งของรูปทรงเรขาคณิต</p><p>- MultipartMode.Largest - วางป้ายใกล้กับส่วนที่ใหญ่ที่สุดของรูปทรงเรขาคณิต</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>ระบุวิธีการวางป้ายเมื่อเทียบกับรูปทรงเรขาคณิต</p><p>- PointLabelPlacement - วางป้ายใกล้กึ่งกลางของรูปทรงเรขาคณิต</p><p>- LineLabelPlacement - วางป้ายตามแนวรูปทรงเรขาคณิตหรือขอบเขต</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|ระบุลำดับความสำคัญของป้ายในกรณีที่ทับซ้อนกับป้ายอื่น<br>ป้ายที่มีลำดับความสำคัญต่ำกว่าจะไม่แสดงผล ค่าเริ่มต้นคือ 1000|

## **ตัวอย่าง**
### **ตัวอย่างการติดป้ายจุด**
โดยค่าเริ่มต้น SimpleLabeling จะวาดข้อความเหนือจุด:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
นี่คือวิธีการจัดรูปแบบแบบอักษร:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
เพื่อควบคุมตำแหน่งข้อความเมื่อเทียบกับคุณสมบัติจุด คุณสมบัติการวางจะต้องถูกตั้งค่า:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
สำหรับสถานการณ์ขั้นสูง คุณอาจต้องการเลือกการติดป้ายที่แตกต่างกันสำหรับคุณสมบัติ นี่คือวิธีการทำ:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **ตัวอย่างการติดป้ายเส้น**
โดยค่าเริ่มต้น SimpleLabeling จะวาดป้ายใกล้กึ่งกลางของเส้น:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
เพื่อหมุนป้ายเพื่อให้ขนานกับเส้น สามารถใช้ LineLabelPlacement พร้อมกับ LineLabelAlignment.Parallel:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
หากคุณต้องการให้ข้อความติดตามเส้นอย่างแม่นยำ สามารถใช้ LineLabelPlacement พร้อมกับ LineLabelAlignment.Curved:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
หากคุณไม่ต้องการให้ข้อความทับซ้อนกับเส้น ให้ใช้ LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
สำหรับสถานการณ์ขั้นสูง คุณอาจต้องการปรับรูปแบบป้ายแบบไดนามิกตามค่าคุณสมบัติของรูปทรงเรขาคณิต นี่คือวิธีการทำ:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
