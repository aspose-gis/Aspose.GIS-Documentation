---
title: "Geometrieconstructors"
type: docs
url: /nl/geometry-constructors/
weight: 5
description: U kunt werken met Point Geometry, Line String Geometry, Poloygon Geometry en Geometry Collections construeren met de GIS C# Library.
---

## **Point Geometrie**
### **Creëer Punt**
Het creëren van een geospatiaal punt met behulp van de API is eenvoudig en gemakkelijk zoals in het volgende codevoorbeeld wordt weergegeven.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **Creëer MultiPunt**
Aspose.GIS voor .NET biedt de mogelijkheid om een verzameling punten weer te geven als één enkele klasse MultiPoint. Het kan één of meer Punten bevatten die zijn gedefinieerd door de lengte- en breedtegraad informatie van elk Punt.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **Line String Geometrie**
U kunt een Line String maken door Point Geometries te specificeren.
### **Creëer een Line String**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **Creëer een MultiLine String**
Een MultiLine string is een verzameling Line Strings die zelf zijn gebouwd uit Point geometries. 

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **Polygongeometrie**
Een Polygon is een verzameling Point geometries die worden gedefinieerd door Punten in de vorm van LinearRing.
### **Creëer Polygon**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **Creëer MultiPolygon**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **Creëer Polygon met Gat**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **Creëer Geometry Collection**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
