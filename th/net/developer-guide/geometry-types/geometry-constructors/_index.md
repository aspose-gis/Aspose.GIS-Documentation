---
title: "ตัวสร้างรูปทรงเรขาคณิต"
type: docs
url: /th/net/geometry-constructors/
weight: 5
description: คุณสามารถทำงานกับ Point Geometry, Line String Geometry, Poloygon Geometry และสร้าง Geometry Collections ด้วย GIS C# Library
---

## **Point Geometry**
### **สร้าง Point**
การสร้างจุดทางภูมิศาสตร์โดยใช้ API นั้นง่ายและสะดวกตามที่แสดงในตัวอย่างโค้ดต่อไปนี้

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **สร้าง MultiPoint**
Aspose.GIS for .NET มีสิ่งอำนวยความสะดวกในการแสดงชุดของจุดเป็นคลาส MultiPoint เดียว สามารถมีหนึ่งหรือหลาย Point ที่กำหนดโดยข้อมูลละติจูดและลองจิจูดของแต่ละ Point

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **Line String Geometry**
คุณสามารถสร้าง Line String โดยระบุ Point Geometries ได้
### **สร้าง Line String**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **สร้าง MultiLine String**
MultiLine string คือชุดของ Line Strings ที่สร้างขึ้นจากรูปทรงเรขาคณิต Point 

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **Polygon Geometry**
Polygon คือชุดของรูปทรงเรขาคณิต Point ซึ่งกำหนดโดย Points ในรูปแบบ LinearRing
### **สร้าง Polygon**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **สร้าง MultiPolygon**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **สร้าง Polygon พร้อม Hole**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **สร้าง Geometry Collection**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
