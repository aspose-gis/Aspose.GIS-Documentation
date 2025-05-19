---
title: "기하 구조자"
type: docs
url: /ko/net/geometry-constructors/
weight: 5
description: GIS C# 라이브러리를 사용하여 Point Geometry, Line String Geometry, Poloygon Geometry를 작업하고 Geometry Collections을 구성할 수 있습니다.
---

## **Point Geometry**
### **Point 생성**
API를 사용하여 지리 공간 점을 만드는 것은 다음과 같은 코드 샘플에서 볼 수 있듯이 간단하고 쉽습니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **MultiPoint 생성**
Aspose.GIS for .NET은 점 컬렉션을 단일 MultiPoint 클래스로 표현할 수 있는 기능을 제공합니다. 각 Point의 위도-경도 정보로 정의된 하나 이상의 Point를 포함할 수 있습니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **Line String Geometry**
Point Geometries을 지정하여 Line String을 만들 수 있습니다.
### **Line String 생성**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **MultiLine String 생성**
MultiLine string은 Point geometries로 구성된 Line Strings의 컬렉션입니다. 

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **Polygon Geometry**
Polygon은 LinearRing 형식의 Point로 정의된 Point geometries 컬렉션입니다.
### **Polygon 생성**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **MultiPolygon 생성**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **Hole이 있는 Polygon 생성**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **Geometry Collection 생성**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
