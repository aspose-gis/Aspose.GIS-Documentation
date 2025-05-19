---
title: "ジオメトリコンストラクタ"
type: docs
url: /ja/net/geometry-constructors/
weight: 5
description: GIS C#ライブラリを使用して、Pointジオメトリ、Line Stringジオメトリ、Poloygonジオメトリを操作したり、Geometryコレクションを作成したりできます。
---

## **ポイントジオメトリ**
### **ポイントの作成**
APIを使用して測地ポイントを作成するのは簡単です。以下のコードサンプルを参照してください。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **マルチポイントの作成**
Aspose.GIS for .NETは、複数のポイントを単一のMultiPointクラスとして表現する機能を提供します。各ポイントの緯度経度情報によって定義された1つまたは複数のポイントを含めることができます。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **ラインストリングジオメトリ**
ポイントジオメトリを指定してラインストリングを作成できます。
### **ラインストリングの作成**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **マルチラインストリングの作成**
マルチラインストリングは、Pointジオメトリから構築されたLine Stringのコレクションです。 

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **ポリゴンジオメトリ**
ポリゴンは、LinearRingの形式でポイントによって定義されたPointジオメトリのコレクションです。
### **ポリゴンの作成**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **マルチポリゴンの作成**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **穴のあるポリゴンの作成**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **ジオメトリコレクションの作成**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
