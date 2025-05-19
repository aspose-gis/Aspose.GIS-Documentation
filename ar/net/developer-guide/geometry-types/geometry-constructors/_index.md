---
title: "منشئات الهندسة"
type: docs
url: /ar/net/geometry-constructors/
weight: 5
description: يمكنك العمل مع هندسة النقطة، وهندسة الخطوط المتسلسلة، وهندسة المضلع، وإنشاء مجموعات هندسة باستخدام مكتبة GIS C#.
---

## **هندسة النقطة**
### **إنشاء نقطة**
إنشاء نقطة جغرافية مكانية باستخدام واجهة برمجة التطبيقات أمر بسيط وسهل كما هو موضح في نموذج التعليمات البرمجية التالي.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **إنشاء نقطة متعددة**
توفر Aspose.GIS for .NET إمكانية تمثيل مجموعة من النقاط كفئة نقطة متعددة واحدة. يمكن أن تحتوي على نقطة واحدة أو أكثر محددة بمعلومات خطوط الطول والعرض لكل نقطة.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **هندسة الخطوط المتسلسلة**
يمكنك إنشاء سلسلة خطوط عن طريق تحديد هندسات النقطة.
### **إنشاء سلسلة خطوط**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **إنشاء سلسلة خطوط متعددة**
سلسلة الخطوط المتعددة هي مجموعة من سلاسل الخطوط التي يتم بناؤها بدورها من هندسات النقطة.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **هندسة المضلع**
المضلع هو مجموعة من هندسات النقطة التي يتم تعريفها بنقاط في شكل حلقة خطية.
### **إنشاء مضلع**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **إنشاء مضلع متعدد**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **إنشاء مضلع مع ثقب**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **إنشاء مجموعة هندسة**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
