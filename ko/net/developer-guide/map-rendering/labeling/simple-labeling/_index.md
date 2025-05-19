---
title: "간단한 레이블링"
type: docs
url: /ko/net/simple-labeling/
weight: 10
---

## **간단한 레이블링**
간단한 레이블링은 피처를 어떻게 레이블해야 하는지를 지정합니다.

지원되는 옵션은 다음과 같습니다.

|**속성**|**설명**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|레이블의 소스로 사용할 속성 이름을 지정합니다.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|레이블 텍스트를 사용자 정의하고 형식을 지정하는 방법을 제공합니다. LabelAttribute를 재정의합니다.|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|텍스트를 렌더링하는 데 사용할 글꼴 패밀리를 지정합니다. 기본값은 시스템에 따라 다릅니다.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>텍스트에 적용할 스타일입니다.</p><p>- FontStyle.Regular - 일반 텍스트.</p><p>- FontStyle.Bold - 굵은 텍스트.</p><p>- FontStyle.Italic - 기울임꼴 텍스트.</p><p>- FontStyle.Underine - 밑줄이 그어진 텍스트.</p><p>- FontStyle.StrikeOut - 가운데에 줄이 있는 텍스트입니다.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|텍스트 크기를 지정합니다.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|텍스트의 색상을 결정합니다.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|텍스트 주위의 후광(또는 윤곽선) 크기를 결정합니다.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|텍스트 주변의 후광 색상을 결정합니다.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|레이블링 엔진에 전달하기 전에 지오메트리를 변환하는 데 사용할 지오메트리 표현식입니다.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>다중 파트 지오메트리에 대한 렌더링 동작을 지정합니다.</p><p>- MultipartMode.All - 지오메트리의 모든 부분 근처에 레이블을 배치합니다.</p><p>- MultipartMode.Any - 지오메트리의 임의의 부분 근처에 하나의 레이블을 배치합니다.</p><p>- MultipartMode.Largest - 지오메트리에서 가장 큰 부분 근처에 레이블을 배치합니다.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>지오메트에 상대적으로 레이블이 배치되는 방법을 지정합니다.</p><p>- PointLabelPlacement - 지오메트리 중앙 근처에 레이블을 배치합니다.</p><p>- LineLabelPlacement - 지오메트리 또는 둘레를 따라 레이블을 배치합니다.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|다른 레이블과 겹치는 경우 레이블의 우선 순위를 지정합니다.<br>우선 순위가 낮은 레이블은 렌더링되지 않습니다. 기본값은 1000입니다.|

## **예제**
### **점 레이블링 예제**
기본적으로 SimpleLabeling은 점 위에 텍스트를 그립니다.

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
글꼴 스타일을 지정하는 방법은 다음과 같습니다.

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
점 피처에 상대적인 텍스트 위치를 제어하려면 placement 속성을 설정해야 합니다.

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
더 고급 시나리오의 경우 피처에 대해 다른 레이블링을 선택할 수 있습니다. 방법은 다음과 같습니다.

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **선 레이블링 예제**
기본적으로 SimpleLabeling은 선 중앙 근처에 레이블을 그립니다.

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
레이블을 선과 평행하게 회전하려면 LineLabelAlignment.Parallel이 있는 LineLabelPlacement를 사용할 수 있습니다.

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
텍스트가 선을 정확하게 따라야 하는 경우 LineLabelAlignment.Curved가 있는 LineLabelPlacement를 사용할 수 있습니다.

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
텍스트가 선과 겹치지 않도록 하려면 LineLabelPlacement.Offset을 사용하십시오.

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
더 고급 시나리오의 경우 피처 속성 값에 따라 레이블 스타일을 동적으로 조정할 수 있습니다. 방법은 다음과 같습니다.

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
