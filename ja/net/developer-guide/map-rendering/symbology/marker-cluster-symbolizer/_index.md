---
title: "マーカークラスタシンボライザー"
type: docs
url: /ja/net/marker-cluster-symbolizer/
weight: 65
description: GIS C# ライブラリまたは API のマーカークラスタシンボライザーは、指定された距離内のマーカーのクラスタリングを可能にします。
---

## **マーカークラスタシンボライザー**
マーカークラスタシンボライザーは、高度なシンボライザーの一つです。これにより、指定された距離内のマーカーをクラスタリングできます。

この C# の例では、クラスターの中心を赤い円として描画しています。また、異なる色を使用してすべてのネストされたクラスターポイントを描画しました。これを行うために、各クラスターに独自のスタイルを設定する FeaturesBasedConfiguration 関数を使用しました。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterMarkerSymbolizer.cs" >}}

結果は次のとおりです。

![points cluster](points-cluster.png)

## **アイテムの合計を描画**

このサンプルでは、クラスター内のアイテムの合計を表示します。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterTextSymbolizer.cs" >}}

結果は次のとおりです。

![digits cluster](digits-cluster.png)
