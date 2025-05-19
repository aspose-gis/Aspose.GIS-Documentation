---
title: シンボロジー - C# GIS API
linktitle: "シンボロジー"
type: docs
url: /ja/symbology/
weight: 10
description: GIS C# ライブラリまたは API は、マーカー、線、塗りつぶしなどのフィーチャジオメトリを描画するためのシンボライザーをサポートしており、より複雑な視覚化を作成するためにシンボライザーを組み合わせることができます。
---

シンボライザーは、マップ上にフィーチャジオメトリを描画する方法です。

|** **|**シンボライザー**|**API クラス**|**説明**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**マーカー**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|カスタマイズ可能な塗りつぶしとアウトラインを持つ定義済みの形状を描画します。|
|![todo:image_alt_text](symbology_2.png)|**線**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|カスタマイズ可能なスタイルで線を描画します。|
|![todo:image_alt_text](symbology_3.png)|**塗りつぶし**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|線で囲まれたポリゴンまたは領域をカスタマイズ可能な塗りつぶしとストロークで塗りつぶします。|

実際の描画を行うシンボライザーに加えて、より複雑な視覚化を作成するために他のシンボライザーを組み合わせることができる他の多くのシンボライザーがあります。

|**シンボライザー**|**API クラス**|**説明**|
| :- | :- | :- |
|**レイヤー化されたシンボライザー**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|互いに上にいくつかのシンボライザーでフィーチャを描画します。|
|**混合ジオメトリシンボライザー**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|混合タイプのジオメトリを含むレイヤーからのフィーチャを、各ジオメトリタイプ用の特定のシンボライザーで描画します。|
|**ルールベースのシンボライザー**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|ユーザーが指定したルールによってフィーチャに適用するシンボライザーを選択します。|
|**マーカークラスタシンボライザー**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|これらの項目のグループ化である、マーカーのクラスタリングを描画します。|
|**ジオメトリジェネレーターシンボライザー**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|レンダリング前にフィーチャジオメトリを置き換えることを許可します。|
|**Null シンボライザー**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|何も描画しません。ルールベースのシンボライザーなどの他のシンボライザーと組み合わせて使用​​すると便利です。|
