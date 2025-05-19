---
title: "Costruttori di Geometrie"
type: docs
url: /it/geometry-constructors/
weight: 5
description: Puoi lavorare con la geometria dei Punti, la geometria delle Linee Stringa, la geometria dei Poligoni e costruire Collezioni di Geometrie con la libreria GIS C# .
---

## **Geometria del Punto**
### **Crea Punto**
Creare un punto geospaziale utilizzando l'API è semplice e facile come mostrato nel seguente esempio di codice.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **Crea MultiPunto**
Aspose.GIS per .NET fornisce la possibilità di rappresentare una raccolta di punti come una singola classe MultiPunto. Può contenere uno o più Punti definiti dalle informazioni di lat-long di ciascun Punto.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **Geometria della Linea Stringa**
Puoi creare una Linea Stringa specificando le Geometrie del Punto.
### **Crea una Linea Stringa**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **Crea una MultiLinea Stringa**
Una stringa MultiLinea è una raccolta di Linee Stringa che a loro volta sono costruite da geometrie del Punto.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **Geometria del Poligono**
Un poligono è una raccolta di geometrie del Punto che è definita da Punti sotto forma di Anello Lineare.
### **Crea Poligono**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **Crea MultiPoligono**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **Crea Poligono con Foro**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **Crea Collezione di Geometrie**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
