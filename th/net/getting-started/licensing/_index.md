---
title: "Licensing"
second_title: Aspose.GIS for .NET
type: docs
url: /th/net/licensing/
weight: 50
keywords: c# gis library, .net gis library
description: ประเมินห้องสมุด GIS C# .NET หรือ API ด้วยข้อจำกัดบางประการ ใช้ License โดยใช้ File หรือ Stream Object หรือเป็น Embedded Resource
---

## **Evaluate Aspose.GIS for .NET**
คุณสามารถดาวน์โหลด Aspose.GIS for .NET ได้ฟรี ก่อนที่คุณจะใช้ license ส่วนประกอบจะทำงานในโหมดประเมินผล เมื่อคุณซื้อ license และเพิ่มโค้ดจำนวนเล็กน้อยเพื่อใช้ license ข้อจำกัดในการประเมินผลจะถูกนำออก

{{% alert color="primary" %}} หากคุณต้องการทดสอบ Aspose.GIS โดยไม่มีข้อจำกัดในโหมดประเมินผล คุณสามารถขอ Temporary License ระยะเวลา 30 วันได้ โปรดดู [Get a Temporary License](https://purchase.aspose.com/temporary-license). {{% /alert %}} 
### **Evaluation Mode Limitations**
เมื่อดำเนินการในโหมดประเมินผล (โดยไม่มี license ที่ใช้) Aspose.GIS จะให้ฟังก์ชันผลิตภัณฑ์เต็มรูปแบบ ยกเว้นข้อจำกัดในการประเมินผลบางอย่าง

1. ไม่เกิน **15 เอกสาร** สามารถเปิดและ/หรือสร้าง **ต่อชั่วโมง**
2. ไม่เกิน **100 คุณสมบัติ** สามารถเข้าถึงได้ในแต่ละเอกสาร (อ่านหรือเขียน)
3. ไม่เกิน **10 000 ข้อมูล raster** สามารถเข้าถึงได้ในแต่ละเอกสาร (อ่านหรือเขียน).
4. จำนวนคุณสมบัติที่อนุญาตสูงสุดในเอกสารสำหรับการดำเนินการแปลงคือ **50**

เมื่อดำเนินการในโหมด license คุณสามารถประมวลผลเอกสารและคุณสมบัติจำนวนไม่จำกัด

## **Applying a License**
License คือไฟล์ XML ข้อความธรรมดาที่มีรายละเอียดเช่นชื่อผลิตภัณฑ์ จำนวนนักพัฒนาที่ได้รับอนุญาต วันหมดอายุการสมัครสมาชิก และอื่นๆ ไฟล์นี้ได้รับการลงนามดิจิทัล ดังนั้นอย่าแก้ไขไฟล์ แม้แต่การเพิ่มช่องว่างบรรทัดพิเศษเข้าไปในไฟล์ก็จะทำให้ไม่ถูกต้อง

คุณต้องตั้งค่า license ก่อนที่จะใช้ Aspose.GIS หากคุณต้องการหลีกเลี่ยงข้อจำกัดในการประเมินผล จำเป็นต้องตั้งค่า license เพียงครั้งเดียวต่อแอปพลิเคชัน (หรือกระบวนการ)
### **Setting a License in Aspose.GIS for .NET**
ใน Aspose.GIS license สามารถโหลดจากไฟล์ สตรีม หรือ embedded resource Aspose.GIS จะพยายามค้นหา license ในตำแหน่งต่อไปนี้:

- เส้นทางที่ระบุอย่างชัดเจน
- โฟลเดอร์ที่มี Aspose.GIS.dll
- โฟลเดอร์ที่มี assembly ที่เรียกใช้ Aspose.GIS.dll
- โฟลเดอร์ที่มี entry assembly (ไฟล์ .exe ของคุณ)
- embedded resource ใน assembly ที่เรียกใช้ Aspose.GIS.dll มีสองวิธีทั่วไปในการตั้งค่า license ซึ่งอธิบายไว้ด้านล่าง:
### **Apply License using File or Stream Object**
วิธีที่ง่ายที่สุดในการตั้งค่า license คือการใส่ไฟล์ license ลงในโฟลเดอร์เดียวกับ Aspose.GIS.dll และระบุเฉพาะชื่อไฟล์โดยไม่ต้องใช้เส้นทาง

{{< highlight java >}}

 // Instantiate an instance of license and set the license file through its path

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // Instantiate an instance of license and set the license through a stream

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}

เมื่อคุณเรียกใช้เมธอด SetLicense ชื่อ license ควรเหมือนกับชื่อไฟล์ license ของคุณ ตัวอย่างเช่น คุณสามารถเปลี่ยนชื่อไฟล์ license เป็น "Aspose.GIS.lic.xml" จากนั้นในโค้ดของคุณ คุณควรใช้ชื่อ license ที่แก้ไข (นั่นคือ Aspose.GIS.lic.xml) สำหรับเมธอด SetLicense

## **Including the License File as an Embedded Resource**
อีกวิธีหนึ่งที่ยอดเยี่ยมในการบรรจุ license พร้อมกับแอปพลิเคชันของคุณและทำให้แน่ใจว่าจะไม่สูญหาย คือการรวมไว้เป็น embedded resource ในหนึ่งใน assemblies ที่เรียกใช้ dll ของส่วนประกอบ (รวมอยู่ใน Aspose.GIS) หากต้องการรวมไฟล์ license เป็น embedded resource ให้ทำตามขั้นตอนต่อไปนี้:

- ใน Visual Studio รวมไฟล์ license (.lic) ลงในโปรเจ็กต์โดยใช้เมนู File | Add Existing Item...
- เลือกไฟล์ใน Solution Explorer และตั้งค่า Build Action เป็น Embedded Resource ในหน้าต่าง Properties
- เพื่อเข้าถึง license ที่ฝังอยู่ใน assembly (เป็น embedded resource) ไม่จำเป็นต้องเรียกใช้เมธอด GetExecutingAssembly และ GetManifestResourceStream ของคลาส System.Reflection.Assembly ของ Microsoft .NET Framework สิ่งที่ต้องทำคือเพิ่มไฟล์ license เป็น embedded resource ลงในโปรเจ็กต์ของคุณและส่งชื่อไฟล์ license ไปยังเมธอด License.SetLicense คลาส License จะค้นหาไฟล์ license ใน embedded resources โดยอัตโนมัติ

โปรดตรวจสอบตัวอย่างด้านล่างเพื่อทำความเข้าใจวิธีการตั้งค่า license (embedded) นี้ในแอปพลิเคชันของคุณ

{{< highlight java >}}

 // Instantiate the License class

Aspose.Gis.License license = new Aspose.Gis.License();

// Pass only the name of the license file embedded in the assembly

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **Applying Metered Key**
[Aspose.Gis for .NET API](/gis/net/) อนุญาตให้นักพัฒนาใช้ metered key เป็นกลไกการออกใบอนุญาตใหม่ กลไกการออกใบอนุญาตใหม่จะถูกใช้ควบคู่ไปกับวิธีการออกใบอนุญาตที่มีอยู่ ลูกค้าที่ต้องการเรียกเก็บเงินตามการใช้งานคุณสมบัติของ API สามารถใช้การออกใบอนุญาตแบบวัดปริมาณได้ สำหรับรายละเอียดเพิ่มเติม โปรดดูส่วน [Metered Licensing FAQ](https://purchase.aspose.com/faqs/licensing/metered)

มีการนำคลาสใหม่ **Metered** มาใช้เพื่อใช้ metered key ต่อไปนี้เป็นโค้ดตัวอย่างที่แสดงวิธีการตั้งค่า public และ private key แบบวัดปริมาณ

**[C#]**

{{< highlight csharp >}}

 // set metered public and private keys

Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();

// Access the setMeteredKey property and pass public and private keys as parameters

metered.SetMeteredKey("*****", "*****");

// DO PROCESSING

// get metered data amount

decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();

// Display information

Console.WriteLine("Amount Consumed : " + amount.ToString());


{{< /highlight >}}
