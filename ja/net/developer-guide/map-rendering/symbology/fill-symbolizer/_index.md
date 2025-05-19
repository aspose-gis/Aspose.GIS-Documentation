---
title: "Fill Symbolizer"
type: docs
url: /ja/net/fill-symbolizer/
weight: 30
description: GIS C# Library API は、Simple Fill シンボライザーをサポートし、Point、Line、Surface などあらゆる種類の 2 次元ジオメトリポリゴンのスタイルとストロークを塗りつぶします。
---

## **Fill Symbolizer**
Simple Fill シンボライザーは、カスタマイズ可能な塗りつぶしスタイルとストロークで領域を塗りつぶします。 これは、2 次元ジオメトリ (ポリゴン) のデフォルトのシンボライザーです。 

ポリゴンに「穴」がある場合、「穴」は塗りつぶされませんが、穴の周囲の境界線は通常どおりストロークされます。「穴」の中にある「島」は塗りつぶされてストロークされ、以下同様です。

サポートされているスタイリングオプション：

|**Property**|**Description**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|塗りつぶしに与えられた色と透明度を指定します。|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - 単色の塗りつぶし</p><p>- None - ポリゴンを塗りつぶさない</p><p>- Horizontal Hatch - 水平線のパターン。</p><p>- Vertical Hatch - 垂直線のパターン。</p><p>- Cross Hatch - 水平線と垂直線が交差する指定します。</p><p>- Forward Diagonal Hatch - 上左から下右への斜めの線で構成されるパターンです。</p><p>- Backward Diagonal Hatch - 上右から下左への斜めの線で構成されるパターンです。</p><p>- Diagonal Cross Hatch - 斜め線が criss-cross するパターンです。</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|ストロークラインに与えられた色と透明度を指定します。|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|シンボル線の描画方法を指定します。|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|ストロークラインの幅を指定します。|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|破線の長さを指定する距離の配列を指定します。|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|破線パターンの開始から線の先頭までの距離を指定します。|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>線セグメントの交差点で線がどのようにレンダリングされるかを決定します。</p><p>- Miter - シャープな角</p><p>- Round - 丸みを帯びた角</p><p>- Bevel - 対角線の角</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|ポイントの位置からシェイプアンカーポイントまでの水平オフセットを指定します。|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|ポイントの位置からシェイプアンカーポイントまでの垂直オフセットを指定します。|

### **Geometry Types**
` `シンボライザーは、あらゆる種類のジオメトリに適用できます。

|**Geometry Dimension**|**Geometry Types**|**Rendering Behavior**|
| :-: | :-: | :-: |
|**Point**|Point, MultiPoint|小さな正方形の直交ポリゴンを描画します。|
|**Line**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|線は、開始点と終了点を接続して塗りつぶすために閉じられます。 元の線のみがストロークされます。|
|**Surface**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|ポリゴンを描画します。|

GeometryCollections の場合、レンダリング動作はコレクション内の各ジオメトリに対して個別に決定されます。 Mixed ジオメトリタイプを持つレイヤーは、GeometryCollections のロジックに従います。

特定のジオメトリタイプにシンボライザーを制限するには、MixedGeometrySymbolizer を使用します。

### **Examples**
デフォルトでは Simple Fill シンボライザーは黒いストロークラインと単色の白い塗りつぶしを描画します：



ここからスタイリングを変更する方法：



|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

ポリゴンにラベルを追加することもできます。 ポリゴンの境界線をラベル付けする方法に関する例については [Lines Labeling Examples](/gis/ja/net/simple-labeling/#simplelabeling-lineslabelingexamples) を、ポリゴンの中心をラベル付けする方法に関する例については [Points Labeling Examples](/gis/ja/net/simple-labeling/#simplelabeling-pointslabelingexamples) をご覧ください。
