---
title: "シンプルなラベル付け"
type: docs
url: /ja/net/simple-labeling/
weight: 10
---

## **シンプルなラベル付け**
シンプルなラベル付けは、フィーチャをどのようにラベル付けする必要があるかを指定します。

サポートされているオプションは次のとおりです。

|**プロパティ**|**説明**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|ラベルのソースとして使用する属性名を指定します。|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|ラベルテキストをカスタマイズおよびフォーマットする方法を提供します。 LabelAttribute をオーバーライドします。|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|テキストのレンダリングに使用するフォントファミリーを指定します。 デフォルト値はシステムに依存します。|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>テキストに適用するスタイル。</p><p>- FontStyle.Regular - 通常のテキスト。</p><p>- FontStyle.Bold - 太字のテキスト。</p><p>- FontStyle.Italic - 斜体のテキスト。</p><p>- FontStyle.Underine - 下線付きのテキスト。</p><p>- FontStyle.StrikeOut - 線が中央を通過するテキスト。</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|テキストのサイズを指定します。|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|テキストの色を決定します。|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|テキストの周りのハロー（またはアウトライン）のサイズを決定します。|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|テキストの周りのハローの色を決定します。|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|ラベル付けエンジンに渡す前にジオメトリを変換するために使用されるジオメトリ式。|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>マルチパートジオメトリのレンダリング動作を指定します。</p><p>- MultipartMode.All - ジオメトリの各部分にラベルを配置します。</p><p>- MultipartMode.Any - ジオメトリのいずれかの部分に1つのラベルを配置します。</p><p>- MultipartMode.Largest - ジオメトリの最大のパーツにラベルを配置します。</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>ラベルがジオメトリに対してどのように配置されるかを指定します。</p><p>- PointLabelPlacement - ラベルをジオメトリの中心近くに配置します。</p><p>- LineLabelPlacement - ジオメトリまたはその周囲に沿ってラベルを配置します。</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|他のラベルと重なり合った場合にラベルの優先順位を指定します。<br>優先順位が低いラベルはレンダリングされません。 デフォルト値は1000です。|

## **例**
### **ポイントのラベル付け例**
デフォルトでは、SimpleLabeling はテキストをポイントの上に描画します。

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
フォントのスタイル設定は次のとおりです。

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
ポイントフィーチャに対するテキストの位置を制御するには、配置プロパティを設定する必要があります。

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
より高度なシナリオでは、フィーチャに異なるラベル付けを選択したい場合があります。 その方法は次のとおりです。

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **ラインのラベル付け例**
デフォルトでは、SimpleLabeling はラインの中心近くにラベルを描画します。

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
ラベルをラインに平行に回転させるには、LineLabelPlacement と LineLabelAlignment.Parallel を使用できます。

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
テキストをラインに正確に従わせたい場合は、LineLabelPlacement と LineLabelAlignment.Curved を使用できます。

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
テキストをラインと重複させたくない場合は、LineLabelPlacement.Offset を使用します。

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
より高度なシナリオでは、フィーチャ属性の値に基づいてラベルのスタイルを動的に調整したい場合があります。 その方法は次のとおりです。

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
