---
title: การแสดงผลแผนที่ไปยังรูปภาพ SVG, PNG, JPG โดยใช้ไลบรารี GIS C#
linktitle: "การแสดงผลแผนที่"
type: docs
url: /th/net/map-rendering/
weight: 50
description: ด้วย API ของ GIS C# คุณสามารถแสดงผลแผนที่จาก Shapefile, FileGDB, GeoJSON, KML formats ทำการปรับแต่งรูปแบบขั้นสูง และวาดแผนที่จากรูปแบบ raster ได้
---

## **ภาพรวมการแสดงผลแผนที่**
ด้วย Aspose.GIS for .NET C# API คุณสามารถแสดงผลแผนที่จาก Shapefile, FileGDB, GeoJSON, KML หรือ [รูปแบบไฟล์ที่รองรับอื่นๆ](/gis/net/supported-file-formats/) ไปยัง SVG, PNG, JPEG หรือ BMP

นี่คือโค้ด C# ที่แสดงวิธีการแสดงผลแผนที่จาก shapefile ไปยัง SVG โดยใช้การตั้งค่าเริ่มต้น:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



นี่คือผลลัพธ์:



![map rendering](map_rendering.png)

ลองดูโค้ดอย่างใกล้ชิดกัน

ขั้นแรก เราสร้างอินสแตนซ์ออบเจ็กต์ [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map) ออบเจ็กต์นี้แสดงถึงคอลเลกชันของเลเยอร์จากแหล่งต่างๆ ที่สามารถแสดงผลได้ แผนที่หนึ่งแผนที่มีขนาดที่ตั้งใจจะแสดงผล ที่นี่เรากำหนดให้แผนที่เป็นความกว้าง 800 พิกเซล และสูง 400 พิกเซล

โปรดสังเกตว่า Map ถูกปิดไว้ในคำสั่ง using นี่เป็นสิ่งจำเป็นเนื่องจาก map จะติดตามทรัพยากรทั้งหมดที่เพิ่มเข้าไป และกำจัดทิ้งเมื่อเราเสร็จสิ้นการแสดงผลและออบเจ็กต์ Map ถูกกำจัดทิ้ง

ถัดไป เราเพิ่มเลเยอร์จากไฟล์ไปยังแผนที่ แต่ละเลเยอร์จะถูกแสดงซ้อนทับบนเลเยอร์ก่อนหน้า ตามลำดับที่เพิ่มลงในแผนที่ ดูรายละเอียดเพิ่มเติมเกี่ยวกับวิธีการเปิดเลเยอร์เวกเตอร์ [ได้ที่นี่](/gis/net/working-with-vector-layers/)

สุดท้าย เราเรียกใช้ [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) เพื่อแสดงผลแผนที่เป็นไฟล์ เรากำหนดเส้นทางไปยังตำแหน่งที่จะบันทึกไฟล์ผลลัพธ์ และตัวเรนเดอร์ที่จะใช้ คลาส [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) มีการอ้างอิงถึงตัวเรนเดอร์ทั้งหมดที่รวมอยู่ใน Aspose.GIS ตัวอย่างเช่น คุณสามารถระบุ Renderers.Png แทน Renderers.Svg ในตัวอย่างข้างต้นเพื่อแสดงผลแผนที่เป็นไฟล์ PNG

## **รูปแบบขั้นสูง**
ด้วย API ของ Aspose.GIS คุณสามารถปรับแต่งการแสดงผลและรูปแบบคุณสมบัติเพื่อให้ได้รูปลักษณ์ที่คุณต้องการ

![advanced styling](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **วาด raster ในแผนที่**
ด้วย Aspose.GIS for .NET คุณสามารถแสดงผลแผนที่จากรูปแบบ raster ได้
### **แสดงผลด้วยการตั้งค่าเริ่มต้น**
นี่คือวิธีการแสดงผลแผนที่จาก GeoTIFF ไปยัง SVG โดยใช้การตั้งค่าเริ่มต้น:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![default raster](default_raster.png)
### **แสดงผล rasters ที่เบ้**
ด้วย Aspose.GIS คุณสามารถแสดงผล raster ที่มีเซลล์ raster เบ้ได้

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![skew raster](skew_raster.png)
### **แสดงผลในการอ้างอิงเชิงพื้นที่แบบ polar**
Aspose.GIS ช่วยให้คุณใช้การอ้างอิงเชิงพื้นที่แบบ polar ในกระบวนการแสดงผลแผนที่ได้

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![gnomonic countries](gnomonic_countries.png)
