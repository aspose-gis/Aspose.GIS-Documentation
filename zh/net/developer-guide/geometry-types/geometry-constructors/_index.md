---
title: "几何构造函数"
type: docs
url: /zh/net/geometry-constructors/
weight: 5
description: 您可以使用 Point Geometry、Line String Geometry 和 Poloygon Geometry，并使用 GIS C# Library 构建 Geometry Collections。
---

## **点几何**
### **创建点**
使用 API 创建地理空间点非常简单方便，如下面的代码示例所示。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **创建多点**
Aspose.GIS for .NET 提供了将多个点表示为单个 MultiPoint 类的方法。它可以包含由每个点的经纬度信息定义的一个或多个点。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **线字符串几何**
您可以指定 Point Geometry 创建 Line String。
### **创建线字符串**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **创建多线字符串**
MultiLine 字符串是由 Point geometries 构建的 Line Strings 的集合。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **多边形几何**
多边形是由 Point geometries 的集合，以 LinearRing 形式定义 Points。
### **创建多边形**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **创建多边形**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **创建带孔的多边形**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **创建几何集合**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
