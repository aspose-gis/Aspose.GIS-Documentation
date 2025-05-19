---
title: "Fill Symbolizer"
type: docs
url: /ko/net/fill-symbolizer/
weight: 30
description: GIS C# Library API는 Simple Fill symbolizer를 지원하여 Point, Line, Surface와 같이 모든 유형의 2차원 기하 도형 폴리곤에 대한 스타일 및 스트로크 채우기를 제공합니다.
---

## **Fill Symbolizer**
Simple Fill symbolizer는 사용자 정의 가능한 채우기 스타일과 스트로크로 영역을 채웁니다. 이것은 2차원 기하 도형(폴리곤)의 기본 symbolizer입니다. 

폴리곤에 “구멍”이 있는 경우, 구멍은 채워지지 않지만 구멍 주변의 경계선은 일반적으로 스트로크됩니다. 구멍 내의 “섬”은 채워지고 스트로크되며, 등등입니다.

지원되는 스타일 옵션:

|**Property**|**Description**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|채우기에 지정된 색상 및 투명도를 지정합니다.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - 단색 채우기</p><p>- None - 폴리곤을 채우지 않음</p><p>- Horizontal Hatch - 수평선 패턴입니다.</p><p>- Vertical Hatch - 수직선 패턴입니다.</p><p>- Cross Hatch - 수평 및 수직선이 교차하는 것을 지정합니다.</p><p>- Forward Diagonal Hatch - 상단 왼쪽에서 하단 오른쪽으로의 대각선 패턴입니다.</p><p>- Backward Diagonal Hatch - 상단 오른쪽에서 하단 왼쪽으로의 대각선 패턴입니다.</p><p>- Diagonal Cross Hatch - 교차 대각선 패턴입니다.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|스트로크 선에 지정된 색상 및 투명도를 지정합니다.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|심볼 라인워크가 어떻게 그려져야 하는지를 지정합니다.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|스트로크 선의 너비를 지정합니다.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|대시 및 간격의 길이를 번갈아 나타내는 거리를 배열로 지정합니다.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|대시 패턴의 시작부터 선의 시작까지의 거리를 지정합니다.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>선 분 교차점에서 선이 어떻게 렌더링되는지를 결정합니다.</p><p>- Miter - 날카로운 모서리</p><p>- Round - 둥근 모서리</p><p>- Bevel - 대각선 모서리</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|점 위치에서 모양 앵커 포인트까지의 수평 오프셋을 지정합니다.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|점 위치에서 모양 앵커 포인트까지의 수직 오프셋을 지정합니다.|

### **Geometry Types**
` `심볼라이저는 모든 유형의 기하 도형에 적용할 수 있습니다.

|**Geometry Dimension**|**Geometry Types**|**Rendering Behavior**|
| :-: | :-: | :-: |
|**Point**|Point, MultiPoint|직교 폴리곤인 작은 사각형을 그립니다.|
|**Line**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|선을 시작점과 끝점을 연결하여 채우기 위해 닫습니다. 원래 선만 스트로크됩니다.|
|**Surface**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|폴리곤을 그립니다.|

GeometryCollections의 경우 각 기하 도형에 대해 별도로 렌더링 동작이 결정됩니다. Mixed geometry 유형 레이어는 GeometryCollections에 대한 논리를 따릅니다.

특정 기하 도형 유형으로 심볼라이저를 제한하려면 MixedGeometrySymbolizer를 사용하십시오.

### **Examples**
기본적으로 Simple Fill symbolizer는 검은색 스트로크 선과 단색 흰색 채우기를 그립니다:



Here's how to change styling:




|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

-----
폴리곤에 레이블을 추가할 수도 있습니다. 폴리곤 경계선을 레이블 지정하는 방법에 대한 예제는 [Lines Labeling Examples](/gis/ko/net/simple-labeling/#simplelabeling-lineslabelingexamples)를 방문하고, 폴리곤 중심을 레이블 지정하는 방법에 대한 예제는 [Points Labeling Examples](/gis/ko/net/simple-labeling/#simplelabeling-pointslabelingexamples)를 참조하십시오.
