---
title: "Геометрични Конструктори"
type: docs
url: /bg/net/geometry-constructors/
weight: 5
description: Можете да работите с Точкова геометрия, Геометрия на полилиния, Полигонна геометрия и да конструирате Колекции от геометрии с GIS C# Библиотеката.
---

## **Точкова геометрия**
### **Създаване на точка**
Създаването на геопространствена точка чрез API е просто и лесно, както е показано в следния примерен код.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **Създаване на MultiPoint**
Aspose.GIS за .NET предоставя възможността да представи колекция от точки като един клас MultiPoint. Той може да съдържа една или повече точки, определени от географска ширина и дължина информация на всяка точка.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **Геометрия на полилиния**
Можете да създадете полилиния, като посочите Точкови геометрии.
### **Създаване на полилиния**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **Създаване на MultiLine String**
MultiLine string е колекция от полилинии, които сами са изградени от точкови геометрии.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **Полигонна геометрия**
Полигон е колекция от точкови геометрии, която се определя от точки под формата на LinearRing.
### **Създаване на полигон**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **Създаване на MultiPolygon**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **Създаване на полигон с дупка**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **Създаване на колекция от геометрии**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
