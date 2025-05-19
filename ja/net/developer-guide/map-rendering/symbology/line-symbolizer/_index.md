---
title: "ラインシンボライザー"
type: docs
url: /ja/net/line-symbolizer/
weight: 20
description: GIS C# Library または API は、1 次元ジオメトリの線に対するシンプルなラインシンボライザーをサポートしており、Point、Line、Surface などあらゆるタイプのジオメトリに適用できます。
---

## **ラインシンボライザー**
シンプルなラインシンボライザーは、カスタマイズ可能なスタイルでラインを描画します。これは、1 次元ジオメトリ (線) のデフォルトのシンボライザーです。 

サポートされているスタイリングオプション：

|**プロパティ**|**説明**|
| :- | :- |
|[Color](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|ラインに与えられた色と透明度を指定します。|
|[Width](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|ラインの幅を指定します|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|ラインセグメントの交差点でラインがどのようにレンダリングされるかを決定します。|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|シンボルラインワークをどのように描画するかを指定します。|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|破線における交互のダッシュとスペースの長さを指定する距離の配列を指定します。|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|ラインの開始からダッシュパターンの開始までの距離を指定します。|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>ラインの端部がどのようにレンダリングされるかを指定します。</p><p>- Butt - シャープな角</p><p>- Round - 丸みを帯びたエッジ</p><p>- Square - わずかに細長い角</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|元のラインからのオフセットを指定します。正の距離の場合、オフセットは入力ライン (ライン方向に関連) の左側に配置されます。負の距離の場合は右側に配置されます。|

### **ジオメトリタイプ**
` `シンボライザーはあらゆるタイプのジオメトリに適用できます。

|**ジオメトリ次元**|**ジオメトリタイプ**|**レンダリング動作**|
| :-: | :-: | :-: |
|**Point**|Point, MultiPoint|ポイントを中心に水平方向に配置された小さな長さのラインを描画し、2 つのエンドキャップを持ちます。|
|**Line**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|ラインを描画します。|
|**Surface**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|ジオメトリの閉じたアウトラインをラインストリングとして使用します (エンドキャップなし)|

GeometryCollections の場合、レンダリング動作はコレクション内の各ジオメトリに対して個別に決定されます。混合ジオメトリタイプのレイヤーは GeometryCollections のロジックに従います。

MixedGeometrySymbolizer を使用して、シンボライザーを特定のジオメトリタイプに制限します。

### **例**
デフォルトでは、ラインシンボライザーは黒い線を描画します。



ここからラインの色を青に変更する方法です。



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

より高度なシナリオでは、フィーチャ属性値に基づいてラインスタイルを動的に調整したい場合があります。その方法は次のとおりです。



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |

また、ラインにラベルを追加したい場合があります。例については [Lines Labeling Examples](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) をご覧ください。
