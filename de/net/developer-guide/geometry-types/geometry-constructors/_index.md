---
title: "Geometrie Konstruktoren"
type: docs
url: /de/geometry-constructors/
weight: 5
description: Sie können mit Punktgeometrien, Linienstringgeometrien, Polygongeometrien arbeiten und Geometriesammlungen mit der GIS C#-Bibliothek erstellen.
---

## **Punktgeometrie**
### **Punkt erstellen**
Das Erstellen eines geodätischen Punkts mithilfe der API ist einfach und unkompliziert, wie im folgenden Codebeispiel gezeigt.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **MultiPunkt erstellen**
Aspose.GIS for .NET bietet die Möglichkeit, eine Sammlung von Punkten als einzelne MultiPunkt-Klasse darzustellen. Es kann einen oder mehrere Punkte enthalten, die durch die Breiten- und Längengradinformationen jedes Punkts definiert sind.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **Linienstringgeometrie**
Sie können einen Linienstring erstellen, indem Sie Punktgeometrien angeben.
### **Linienstring erstellen**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **MultiLinienstring erstellen**
Ein MultiLinienstring ist eine Sammlung von Linienstrings, die selbst aus Punktgeometrien aufgebaut sind.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **Polygongeometrie**
Ein Polygon ist eine Sammlung von Punktgeometrien, die durch Punkte in Form eines LinearRing definiert sind.
### **Polygon erstellen**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **MultiPolygon erstellen**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **Polygon mit Loch erstellen**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **Geometriesammlung erstellen**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
