---
title: "마커 심볼라이저"
type: docs
url: /ko/net/marker-symbolizer/
weight: 10
description: GIS C# 라이브러리 또는 API는 포인트, 선, 표면과 같은 모든 유형의 지오메트리에 사용자 정의 가능한 채우기 및 윤곽선으로 미리 정의된 모양을 그리는 간단한 마커 심볼라이저를 지원합니다.
---

## **마커 심볼라이저**
간단한 마커 심볼라이저는 사용자 정의 가능한 채우기 및 윤곽선으로 미리 정의된 모양을 그립니다. 이것은 0차원 지오메트리(포인트)의 기본 심볼라이저입니다. 

지원되는 모양은 다음과 같습니다.

|![todo:image_alt_text](marker-symbolizer_1.png)|Circle| |![todo:image_alt_text](marker-symbolizer_2.png)|Star|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Square| |![todo:image_alt_text](marker-symbolizer_4.png)|Cross|
|![todo:image_alt_text](marker-symbolizer_5.png)|Triangle| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

지원되는 스타일 옵션:

|**속성**|**설명**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|마커의 모양을 지정합니다.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|마커 모양의 크기를 지정합니다|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|채우기에 제공되는 색상 및 투명도를 지정합니다|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|선에 제공되는 색상 및 투명도를 지정합니다|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|선의 너비를 지정합니다|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|선 분면의 교차점에서 선이 렌더링되는 방식을 결정합니다.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|심볼 라인워크가 어떻게 그려져야 하는지를 지정합니다.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|대시 및 간격의 길이가 교대로 변경되는 대시 선에서 거리를 배열로 지정합니다.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|대시 패턴의 시작부터 선까지의 거리를 지정합니다.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|십진수로 중심점을 기준으로 심볼을 회전시키는 각도를 지정합니다. 양수 값은 시계 방향으로 회전을 나타내고, 음수 값은 반시계 방향으로 회전을 나타냅니다. 기본값은 0입니다.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|포인트 위치에서 모양 앵커 포인트까지의 수평 오프셋을 지정합니다|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|포인트 위치에서 모양 앵커 포인트까지의 수직 오프셋을 지정합니다.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|포인트 위치와 수평으로 정렬될 마커 모양의 측면을 지정합니다.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|포인트 위치와 수직으로 정렬될 마커 모양의 측면을 지정합니다.|

### **지오메트리 유형**
` `심볼라이저는 모든 유형의 지오메트리에 적용할 수 있습니다.

|**지오메트리 차원**|**지오메트리 유형**|**렌더링 동작**|
| :-: | :-: | :-: |
|**포인트**|Point, MultiPoint|포인트 좌표를 중심으로 모양을 그립니다.|
|**선**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>지오메트리의 중심점을 중심으로 모양을 그립니다</p><p> </p>|
|**표면**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

GeometryCollections의 경우 컬렉션 내 각 지오메트에 대해 별도로 렌더링 동작이 결정됩니다. Mixed geometry 유형 레이어는 GeometryCollections에 대한 논리를 따릅니다.

특정 지오메트리 유형으로 심볼라이저를 제한하려면 MixedGeometrySymbolizer를 사용하십시오.

### **예제**
기본적으로 마커 심볼라이저는 검은색 원을 그립니다:



여기서 채우기 색상을 빨간색으로 변경하는 방법입니다:



|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

또 다른 예로 미리 정의된 모양(삼각형)으로 스타일을 지정하는 방법이 있습니다:



|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----

더욱 고급 시나리오의 경우 기능 속성 값에 따라 마커 스타일을 동적으로 조정하려는 경우가 있습니다. 다음과 같이 수행할 수 있습니다:



|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----

마커에 레이블을 추가할 수도 있습니다. 예제는 [포인트 라벨링 예제](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples)를 방문하십시오.
