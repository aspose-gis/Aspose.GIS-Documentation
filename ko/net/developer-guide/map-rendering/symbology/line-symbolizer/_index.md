---
title: "라인 심볼라이저"
type: docs
url: /ko/net/line-symbolizer/
weight: 20
description: GIS C# 라이브러리 또는 API는 1차원 기하 도형인 선에 대한 단순선 심볼라이저를 지원하며, 점, 선, 표면 등 모든 유형의 기하 도형에 적용할 수 있습니다.
---

## **라인 심볼라이저**
단순 라인 심볼라이저는 사용자 정의 가능한 스타일로 선을 그립니다. 이것은 1차원 기하 도형(선)의 기본 심볼라이저입니다. 

지원되는 스타일링 옵션:

|**속성**|**설명**|
| :- | :- |
|[Color](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|선에 적용되는 색상 및 투명도를 지정합니다.|
|[Width](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|선의 너비를 지정합니다|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|선 분의 교차점에서 선이 렌더링되는 방식을 결정합니다.|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|심볼 라인워크가 어떻게 그려져야 하는지를 지정합니다.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|대시 및 간격의 길이를 번갈아 나타내는 거리를 배열로 지정합니다.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|대시 패턴 시작점으로부터의 거리를 지정합니다.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>선의 끝부분이 어떻게 렌더링되는지를 지정합니다.</p><p>- Butt - 날카로운 사각형 가장자리</p><p>- Round - 둥근 가장자리</p><p>- Square - 약간 길어진 사각형 가장자리</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|원래 선으로부터의 오프셋을 지정합니다. 양수 거리의 경우 오프셋은 입력 선 방향에 대해 선의 왼쪽에 위치합니다. 음수 거리는 오른쪽에 위치합니다.|

### **기하 유형**
` `심볼라이저는 모든 유형의 기하 도형에 적용할 수 있습니다.

|**기하 차원**|**기하 유형**|**렌더링 동작**|
| :-: | :-: | :-: |
|**점**|Point, MultiPoint|점을 중심으로 가로 방향으로 작은 길이의 선을 그리고 두 개의 캡 엔드를 갖습니다.|
|**선**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|선을 그립니다.|
|**표면**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|기하 도형의 닫힌 윤곽선을 선 문자열로 사용합니다(캡 엔드 없음)|

GeometryCollections의 경우 컬렉션 내 각 기하 도형에 대해 별도로 렌더링 동작이 결정됩니다. Mixed geometry 유형 레이어는 GeometryCollections에 대한 논리를 따릅니다.

MixedGeometrySymbolizer를 사용하여 심볼라이저를 특정 기하 유형으로 제한합니다.

### **예제**
기본적으로 라인 심볼라이저는 검은색 선을 그립니다:



여기에서 선 색상을 파란색으로 변경하는 방법입니다:



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

더욱 고급 시나리오의 경우 기능 속성 값에 따라 라인 스타일을 동적으로 조정하려는 경우가 있을 수 있습니다. 다음과 같이 수행할 수 있습니다:



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |

또한 라인에 레이블을 추가하려는 경우도 있습니다. 예제는 [라인 레이블링 예제](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples)를 방문하십시오.
