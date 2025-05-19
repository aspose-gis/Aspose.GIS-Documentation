---
title: "Geometri Oluşturucuları"
type: docs
url: /tr/net/geometry-constructors/
weight: 5
description: GIS C# Kütüphanesi ile Nokta Geometrisi, Çizgi Dizi Geometrisi, Poligon Geometrisi üzerinde çalışabilir ve Geometri Koleksiyonları oluşturabilirsiniz.
---

## **Nokta Geometrisi**
### **Nokta Oluştur**
Coğrafi bir noktayı API kullanarak oluşturmak basit ve kolaydır; aşağıdaki kod örneğinde gösterildiği gibi.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **Çoklu Nokta Oluştur**
Aspose.GIS for .NET, bir nokta koleksiyonunu tek bir ÇokluNokta sınıfı olarak temsil etme olanağı sağlar. Her Noktanın enlem-boylam bilgisiyle tanımlanan bir veya daha fazla Nokta içerebilir.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **Çizgi Dizi Geometrisi**
Nokta Geometrilerini belirterek bir Çizgi Dizi oluşturabilirsiniz.
### **Bir Çizgi Dizi Oluştur**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **Çoklu Çizgi Dizi Oluştur**
Bir Çoklu Çizgi dize, Nokta geometrilerinden oluşturulan Çizgi Dizilerinin bir koleksiyonudur.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **Poligon Geometrisi**
Bir Poligon, Nokta geometrilerinden oluşan ve Noktalarla LineerHalka şeklinde tanımlanan bir koleksiyondur.
### **Poligon Oluştur**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **Çoklu Poligon Oluştur**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **Delikli Poligon Oluştur**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **Geometri Koleksiyonu Oluştur**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
