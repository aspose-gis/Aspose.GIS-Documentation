---
title: "Konstruktory Geometrie"
type: docs
url: /cs/geometry-constructors/
weight: 5
description: Můžete pracovat s geometrií bodu, Line String Geometry, Polygon Geometry a konstruovat kolekce geometrie pomocí GIS C# Library.
---

## **Geometrie bodu**
### **Vytvoření bodu**
Vytváření geografického bodu pomocí API je jednoduché a snadné, jak ukazuje následující příklad kódu.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **Vytvoření MultiPoint**
Aspose.GIS for .NET poskytuje možnost reprezentovat kolekci bodů jako jednu třídu MultiPoint. Může obsahovat jeden nebo více bodů definovaných zeměpisnou šířkou a délkou každého bodu.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **Line String Geometry**
Můžete vytvořit Line String zadáním geometrií bodů.
### **Vytvoření Line String**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **Vytvoření MultiLine String**
MultiLine string je kolekce Line Strings, které jsou samy o sobě sestaveny z geometrií bodů.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **Polygon Geometry**
Polygon je kolekce geometrií bodů, která je definována body ve formě LinearRing.
### **Vytvoření Polygonu**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **Vytvoření MultiPolygonu**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **Vytvoření Polygonu s dírou**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **Vytvoření kolekce geometrií**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
