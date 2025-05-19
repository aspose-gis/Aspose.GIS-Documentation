---
title: 기호 - C# GIS API
linktitle: "기호"
type: docs
url: /ko/net/symbology/
weight: 10
description: GIS C# 라이브러리 또는 API는 마커, 선, 채우기와 같은 피처 지오메트리를 그리고 더 복잡한 시각화를 만들기 위해 기호자를 지원합니다.
---

기호자는 지도에서 피처 지오메트리를 그리는 방법입니다.

|** **|**기호자**|**API 클래스**|**설명**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**마커**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|사용자 정의 채우기 및 윤곽선으로 미리 정의된 모양을 그립니다.|
|![todo:image_alt_text](symbology_2.png)|**선**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|사용자 정의 스타일로 선을 그립니다.|
|![todo:image_alt_text](symbology_3.png)|**채우기**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|사용자 정의 채우기 및 획으로 선으로 둘러싸인 다각형 또는 영역을 채웁니다.|
실제 그림을 그리는 기호자 외에도 다른 기호자를 결합하여 더 복잡한 시각화를 만들 수 있는 다른 기호자가 있습니다.

|**기호자**|**API 클래스**|**설명**|
| :- | :- | :- |
|**계층화된 기호자**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|서로 위에 여러 기호자로 피처를 그립니다.|
|**혼합 지오메트리 기호자**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|각 지오메트리 유형에 대한 특정 기호자로 혼합된 지오메트리를 포함하는 레이어에서 피처를 그립니다.|
|**규칙 기반 기호자**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|사용자가 지정한 규칙에 따라 피처에 적용할 기호자를 선택합니다.|
|**마커 클러스터 기호자**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|이러한 항목의 그룹화인 마커 클러스터링을 그립니다.|
|**지오메트리 생성기 기호자**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|렌더링 전에 피처 지오메트리를 대체할 수 있습니다.|
|**Null 기호자**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|아무것도 그리지 않습니다. 규칙 기반 기호자와 같은 다른 기호자와 결합할 때 유용합니다.|
