---
title: "Конструктори геометрії"
type: docs
url: /uk/net/geometry-constructors/
weight: 5
description: Ви можете працювати з точковою геометрією, лінійною геометрією, полігональною геометрією та створювати колекції геометрій за допомогою GIS C# Library.
---

## **Точкова геометрія**
### **Створення точки**
Створення геопросторової точки з використанням API є простим і легким, як показано в наступному прикладі коду.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **Створення MultiPoint**
Aspose.GIS для .NET надає можливість представляти колекцію точок як єдиний клас MultiPoint. Він може містити одну або кілька точок, визначених інформацією про широту та довготу кожної точки.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **Лінійна геометрія**
Ви можете створити лінійну геометрію, вказавши точкові геометрії.
### **Створення лінійної геометрії**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **Створення MultiLine String**
MultiLine string - це колекція лінійних геометрій, які самі будуються з точкових геометрій.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **Полігональна геометрія**
Полігон - це колекція точкових геометрій, яка визначається точками у формі LinearRing.
### **Створення полігону**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **Створення MultiPolygon**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **Створення полігону з отвором**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **Створення колекції геометрій**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
