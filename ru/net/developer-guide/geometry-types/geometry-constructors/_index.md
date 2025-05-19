---
title: "Конструкторы геометрии"
type: docs
url: /ru/net/geometry-constructors/
weight: 5
description: Вы можете работать с точечной геометрией, геометрией ломаной линии, полигональной геометрией и создавать коллекции геометрий с помощью GIS C# Library.
---

## **Точечная геометрия**
### **Создание точки**
Создание геопространственной точки с использованием API просто и легко, как показано в следующем примере кода.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **Создание мультиточки**
Aspose.GIS for .NET предоставляет возможность представления коллекции точек в виде одного класса MultiPoint. Он может содержать одну или несколько точек, определенных информацией о широте и долготе каждой точки.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **Геометрия ломаной линии**
Вы можете создать ломаную линию, указав геометрии точек.
### **Создание ломаной линии**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **Создание мультиломаной линии**
Мультиломаная линия — это коллекция ломаных линий, которые сами построены из геометрий точек.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **Полигональная геометрия**
Полигон — это коллекция геометрий точек, которая определяется точками в форме линейного кольца.
### **Создание полигона**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **Создание мультиполигона**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **Создание полигона с отверстием**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **Создание коллекции геометрий**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
