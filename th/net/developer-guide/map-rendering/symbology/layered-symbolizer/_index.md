---
title: "Layered Symbolizer"
type: docs
url: /th/net/layered-symbolizer/
weight: 40
description: Layered symbolizer ใน GIS C# Library API วาดฟีเจอร์ด้วย symbolizers หลายรายการซ้อนทับกัน โดยมีโหมดการเรียงลำดับการแสดงผลตามฟีเจอร์หรือเลเยอร์
---

## **Layered Symbolizer**
Layered symbolizer จะวาดฟีเจอร์ด้วย symbolizers หลายรายการซ้อนทับกัน คุณสามารถเลือกจากสองโหมดการเรียงลำดับการแสดงผล:

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - วาดฟีเจอร์แรกด้วย symbolizers ทั้งหมดที่เพิ่มลงใน layered symbolizer จากนั้นดำเนินการวาดฟีเจอร์ถัดไป
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - วาดฟีเจอร์ทั้งหมดด้วย symbolizer แรก จากนั้นวาดฟีเจอร์ทั้งหมดด้วย symbolizer ถัดไป
### **Rendering by Features**

### **Rendering by Layers**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
