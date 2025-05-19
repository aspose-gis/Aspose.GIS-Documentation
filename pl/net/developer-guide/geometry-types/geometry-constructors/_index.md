---
title: "Konstruktory geometrii"
type: docs
url: /pl/net/geometry-constructors/
weight: 5
description: Możesz pracować z geometrią Punkt, geometrią Łańcucha linii, geometrią Wielokąta oraz konstruować Kolekcje geometrii za pomocą biblioteki GIS C#.
---

## **Geometria punktu**
### **Utwórz punkt**
Tworzenie punktu geoprzestrzennego przy użyciu API jest proste i łatwe, jak pokazano w poniższym przykładzie kodu.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **Utwórz MultiPoint**
Aspose.GIS for .NET zapewnia możliwość reprezentowania kolekcji punktów jako pojedynczej klasy MultiPoint. Może zawierać jeden lub więcej Punktów zdefiniowanych przez informacje o szerokości i długości geograficznej każdego Punktu.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **Geometria łańcucha linii**
Możesz utworzyć Łańcuch linii, określając geometrie Punktów.
### **Utwórz łańcuch linii**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **Utwórz MultiLine String**
MultiLine string to kolekcja Łańcuchów linii, które same są zbudowane z geometrii Punktów.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **Geometria wielokąta**
Wielokąt to kolekcja geometrii Punktów, która jest zdefiniowana przez Punkty w postaci LinearRing.
### **Utwórz Wielokąt**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **Utwórz MultiWielokąt**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **Utwórz Wielokąt z dziurą**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **Utwórz Kolekcję geometrii**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
