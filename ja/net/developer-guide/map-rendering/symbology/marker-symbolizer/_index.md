---
title: "マーカーシンボライザー"
type: docs
url: /ja/net/marker-symbolizer/
weight: 10
description: GIS C# Library または API は、ポイント、ライン、サーフェスなど、あらゆる種類のジオメトリにカスタマイズ可能な塗りつめとアウトラインで定義済みの形状を描画するシンプルなマーカーシンボライザーをサポートします。
---

## **マーカーシンボライザー**
シンプルなマーカーシンボライザーは、カスタマイズ可能な塗りつめとアウトラインを備えた定義済みの形状を描画します。これは0次元ジオメトリ（ポイント）のデフォルトのシンボライザーです。 

サポートされている形状は次のとおりです。

|![todo:image_alt_text](marker-symbolizer_1.png)|円| |![todo:image_alt_text](marker-symbolizer_2.png)|星|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|正方形| |![todo:image_alt_text](marker-symbolizer_4.png)|十字|
|![todo:image_alt_text](marker-symbolizer_5.png)|三角形| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

サポートされているスタイルオプション：

|**プロパティ**|**説明**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|マーカーの形状を指定します。|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|マーカー形状のサイズを指定します|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|塗りつめに与える色と透明度を指定します|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|線に与える色と透明度を指定します|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|線の幅を指定します|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|線セグメントの交差点で線がどのようにレンダリングされるかを決定します。|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|シンボルの線描画をどのように行うかを指定します。|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|破線の長さとスペースの交互を指定する距離の配列を指定します。|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|破線パターンの開始から線の先までの距離を指定します。|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|シンボルの中心点周りの回転を10進法で指定します。正の値は時計回りの回転を示し、負の値は反時計回りの回転を示します。デフォルトは0です。|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|ポイントの位置から形状アンカーポイントへの水平オフセットを指定します。|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|ポイントの位置から形状アンカーポイントへの垂直オフセットを指定します。|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|ポイントの位置に対して水平に整列するマーカー形状の側面を指定します。|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|ポイントの位置に対して垂直に整列するマーカー形状の側面を指定します。|

### **ジオメトリタイプ**
` `シンボライザーは、あらゆる種類のジオメトリに適用できます。

|**ジオメトリ次元**|**ジオメトリタイプ**|**レンダリング動作**|
| :-: | :-: | :-: |
|**ポイント**|Point, MultiPoint|ポイント座標を中心に形状を描画します。|
|**ライン**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>ジオメトリの中心点を中心に形状を描画します</p><p> </p>|
|**サーフェス**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

GeometryCollectionsの場合、レンダリング動作はコレクション内の各ジオメトリに対して個別に決定されます。混合ジオメトリタイプのレイヤーは、GeometryCollectionsのロジックに従います。

特定のジオメトリタイプにシンボライザーを制限するには、MixedGeometrySymbolizerを使用します。

### **例**
デフォルトでは、マーカーシンボライザーは黒い円を描画します。

-----
塗りつめ色を赤に変更する方法：

|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

定義済みの形状（三角形）を使用したスタイルの別の例：

|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----
より高度なシナリオでは、フィーチャ属性値に基づいてマーカーのスタイルを動的に調整したい場合があります。その方法は次のとおりです。

|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
マーカーにラベルを追加することもできます。[ポイントのラベル付け例](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) をご覧ください。
