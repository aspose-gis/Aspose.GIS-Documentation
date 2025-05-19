---
title: C# での GIS ベクトルレイヤーのフィルタリングとインデックス作成
linktitle: フィルタリングとインデックス作成
second_title: Aspose.GIS for .NET
type: docs
url: /ja/net/filtering-and-indexing/
weight: 30
description: GIS C# .NET ライブラリまたは API を使用すると、属性値または空間範囲で GIS ベクトルレイヤーをフィルタリングできます。また、インデックスを使用して、フィルタリングと空間クエリの速度を向上させることができます。
---

Aspose.GIS for .NET を使用すると、属性値または空間範囲でレイヤーをフィルタリングできます。また、インデックスを使用して、フィルタリングと空間クエリの速度を向上させることができます。
## **属性インデックス**
### **インデックスなしでのフィルタリング**
ここでは、属性の値でレイヤーをフィルタリングする方法を示します。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **インデックス付きでのフィルタリング**
上記のコードは、レイヤーが一度だけフィルタリングされる限り問題ありません。ただし、レイヤーが複数回クエリされる可能性が高い場合は、属性インデックスからメリットを得ることができます。属性インデックスの構築には時間がかかりますが、フィルタリングを高速化するために何度も再利用できます。

次の例では、属性インデックスファイルを使用して、属性の値によるレイヤーのフィルタリングを高速化します。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **フィルタリングされたフィーチャの保存**
フィルタリングされたフィーチャはレイヤーに保存できます。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **フィルタリングされたフィーチャのレンダリング**
フィルタリングされたフィーチャをレンダリングすることも可能です。次の例では、属性インデックスを使用して、人口が 2000 を超えるすべてのフィーチャをすばやく選択し、マップに追加します。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **空間インデックス**
空間インデックスは、空間クエリを高速化するために使用されます。属性インデックスと同様に、空間インデックスは作成後に再利用されます。
### **ポイントに最も近いフィーチャの検索**
ここでは、空間インデックスを使用して、ある点に最も近いフィーチャをすばやく見つける方法を示します。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **ジオメトリと交差するフィーチャの選択**
次の例では、空間インデックスを使用して、ジオメトリと交差するフィーチャの選択を高速化します。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
