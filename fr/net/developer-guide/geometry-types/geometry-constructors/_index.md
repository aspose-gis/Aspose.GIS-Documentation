---
title: "Constructeurs de géométrie"
type: docs
url: /fr/net/geometry-constructors/
weight: 5
description: Vous pouvez travailler avec la géométrie Point, la géométrie Line String, la géométrie Poloygon et construire des collections de géométries avec la bibliothèque GIS C# .
---

## **Géométrie Point**
### **Créer un point**
La création d'un point géospatial à l'aide de l'API est simple et facile comme le montre l'exemple de code suivant.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **Créer un MultiPoint**
Aspose.GIS pour .NET fournit la possibilité de représenter une collection de points sous forme d'une seule classe MultiPoint. Il peut contenir un ou plusieurs Points définis par les informations de latitude et longitude de chaque Point.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **Géométrie Line String**
Vous pouvez créer une Line String en spécifiant des géométries Point.
### **Créer une Line String**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **Créer une MultiLine String**
Une MultiLine string est une collection de Line Strings qui sont elles-mêmes construites à partir de géométries Point. 

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **Géométrie Polygon**
Un Polygon est une collection de géométries Point qui est définie par des Points sous forme d'Anneau linéaire.
### **Créer un Polygon**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **Créer un MultiPolygon**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **Créer un Polygon avec trou**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **Créer une collection de géométries**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
