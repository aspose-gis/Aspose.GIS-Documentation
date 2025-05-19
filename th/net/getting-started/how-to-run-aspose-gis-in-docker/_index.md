---
title: วิธีการเรียกใช้ Aspose.GIS ใน Docker
type: docs
description: "เรียกใช้ Aspose.GIS ในคอนเทนเนอร์ Docker สำหรับ Linux, Windows Server และระบบปฏิบัติการใดๆ"
weight: 139
url: /th/net/how-to-run-aspose-gis-in-docker/
---

## ข้อกำหนดเบื้องต้น

- ต้องติดตั้ง Docker บนระบบของคุณ สำหรับข้อมูลเกี่ยวกับวิธีการติดตั้ง Docker บน Windows หรือ Mac โปรดดูที่ลิงก์ในส่วน "ดูเพิ่มเติม"

- Visual Studio 2022

- NET Core 3.1 SDK ถูกใช้ในตัวอย่าง

## แอปพลิเคชัน Hello World

ในตัวอย่างนี้ คุณจะสร้างแอปพลิเคชันคอนโซล Hello World อย่างง่าย ที่สร้างเส้นโค้งผสมและบันทึกไว้ในไฟล์ จากนั้นแอปพลิเคชันสามารถสร้างและเรียกใช้ใน Docker ได้

### การสร้างแอปพลิเคชันคอนโซล

ในการสร้างโปรแกรม Hello World ให้ทำตามขั้นตอนด้านล่าง:
1. เมื่อติดตั้ง Docker แล้ว ตรวจสอบให้แน่ใจว่าใช้งาน Linux Containers (ค่าเริ่มต้น) หากจำเป็น เลือกตัวเลือก Switch to Linux containers จากเมนู Docker Desktops
1. ใน Visual Studio สร้างแอปพลิเคชันคอนโซล NET Core 3.1<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. ติดตั้ง Aspose.GIS เวอร์ชันล่าสุดจาก NuGet<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. เนื่องจากแอปพลิเคชันจะทำงานบน Linux จึงต้องติดตั้งสินทรัพย์ Linux ที่เหมาะสม เริ่มต้นด้วยอิมเมจฐาน dotnet core sdk 3.1 และติดตั้ง libgdiplus libc6-dev
1. เมื่อเพิ่มการขึ้นต่อที่จำเป็นทั้งหมดแล้ว ให้เขียนโปรแกรมอย่างง่ายที่สร้างเส้นโค้งผสม:<br>
**.NET**<br>
{{< highlight csharp >}}
using System.IO;
using Aspose.Gis.Geometries;
using Aspose.Gis;

namespace Aspose.GIS.Docker.Sample
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string path = Path.Combine("TestOut", "CreateCompoundCurve_out.shp");
            using (VectorLayer layer = VectorLayer.Create(path, Drivers.Shapefile))
            {
                var feature = layer.ConstructFeature();
                // สร้างตัวอักษร 'S' (เริ่มต้นที่ด้านล่างซ้าย)
                var compoundCurve = new CompoundCurve();

                var bottom = (ILineString)Geometry.FromText("LineString (0 0, 3 0)");
                var firstArc = (ICircularString)Geometry.FromText("CircularString (3 0, 4 1, 3 2)");
                var middle = (ILineString)Geometry.FromText("LineString (3 2, 1 2)");
                var secondArc = (ICircularString)Geometry.FromText("CircularString (1 2, 0 3, 1 4)");
                var top = (ILineString)Geometry.FromText("LineString (1 4, 4 4)");

                compoundCurve.AddCurve(bottom);
                compoundCurve.AddCurve(firstArc);
                compoundCurve.AddCurve(middle);
                compoundCurve.AddCurve(secondArc);
                compoundCurve.AddCurve(top);
                feature.Geometry = compoundCurve;

                layer.Add(feature);
            }
        }
    }
}
{{< /highlight >}}

โปรดทราบว่าโฟลเดอร์ �TestOut� ถูกระบุเป็นโฟลเดอร์เอาต์พุตสำหรับการบันทึกเอกสารเอาต์พุต เมื่อเรียกใช้แอปพลิเคชันใน Docker โฟลเดอร์บนเครื่องโฮสต์จะถูกเมานต์ไปยังโฟลเดอร์นี้ในคอนเทนเนอร์ ซึ่งจะช่วยให้คุณสามารถดูเอาต์พุตที่สร้างโดย Aspose.GIS ในคอนเทนเนอร์ Docker ได้อย่างง่ายดาย

### กำหนดค่า Dockerfile

ขั้นตอนถัดไปคือการสร้างและกำหนดค่า Dockerfile

1. สร้าง Dockerfile และวางไว้ข้างไฟล์โซลูชันของแอปพลิเคชันของคุณ รักษาชื่อไฟล์นี้โดยไม่มีนามสกุล (ค่าเริ่มต้น)
1. ใน Dockerfile ให้ระบุ:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

ด้านบนเป็น Dockerfile อย่างง่าย ซึ่งมีคำสั่งต่อไปนี้:

- อิมเมจ SDK ที่จะใช้ ที่นี่คืออิมเมจ Net 3.1 Docker จะดาวน์โหลดเมื่อการสร้างเสร็จสิ้น ระบุเวอร์ชันของ SDK เป็นแท็ก
- ไดเรกทอรีทำงาน ซึ่งระบุในบรรทัดถัดไป
- คำสั่งเพื่อติดตั้ง libgdiplus ถูกเรียกใช้ในคอนเทนเนอร์ นี่เป็นสิ่งจำเป็นสำหรับ System.Drawing.Common
- คำสั่งเพื่อคัดลอกทุกอย่างไปยังคอนเทนเนอร์ เผยแพร่แอปพลิเคชัน และระบุจุดเข้าใช้งาน

### สร้างและเรียกใช้แอปพลิเคชันใน Docker

ตอนนี้สามารถสร้างและเรียกใช้แอปพลิเคชันใน Docker ได้ เปิดพรอมต์คำสั่งที่คุณชื่นชอบ เปลี่ยนไดเรกทอรีไปยังโฟลเดอร์ที่มีแอปพลิเคชัน (โฟลเดอร์ที่ไฟล์โซลูชันและ Dockerfile อยู่) และรันคำสั่งต่อไปนี้:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

ครั้งแรกที่รันคำสั่งนี้อาจใช้เวลานานกว่า เนื่องจาก Docker ต้องดาวน์โหลดอิมเมจที่จำเป็น เมื่อคำสั่งก่อนหน้านี้เสร็จสิ้น ให้รันคำสั่งต่อไปนี้:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

ใส่ใจกับอาร์กิวเมนต์เมานต์ เนื่องจากดังที่กล่าวมาก่อนหน้านี้ โฟลเดอร์บนเครื่องโฮสต์จะถูกเมานต์เข้าสู่โฟลเดอร์ของคอนเทนเนอร์ เพื่อให้เห็นผลลัพธ์ของการดำเนินการแอปพลิเคชันได้อย่างง่ายดาย เส้นทางใน Linux จะคำนึงถึงตัวพิมพ์เล็กและใหญ่

{{% /alert %}}


## ตัวอย่างเพิ่มเติม

สำหรับตัวอย่างเพิ่มเติมเกี่ยวกับวิธีการใช้ Aspose.GIS ใน Docker โปรดดูที่ [ตัวอย่าง](https://github.com/aspose-gis/Aspose.Gis-for-.NET).

## ดูเพิ่มเติม

- [ติดตั้ง Docker Desktop บน Windows](https://docs.docker.com/docker-for-windows/install/)
- [ติดตั้ง Docker Desktop บน Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- ตัวเลือก [Switch to Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)
- ข้อมูลเพิ่มเติมเกี่ยวกับ [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
