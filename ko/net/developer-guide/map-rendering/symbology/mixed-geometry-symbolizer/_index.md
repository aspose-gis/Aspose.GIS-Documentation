---
title: "혼합 도형 심볼라이저"
type: docs
url: /ko/net/mixed-geometry-symbolizer/
weight: 50
description: GIS C# 라이브러리 API의 혼합 도형 심볼라이저는 레이어에 혼합된 도형 유형이 포함되어 있는 경우 각 도형 유형별로 심볼라이저를 별도로 지정할 수 있습니다.
---

## **혼합 도형 심볼라이저**
혼합 도형 심볼라이저는 레이어에 혼합된 도형 유형이 포함되어 있는 경우 각 도형 유형별로 심볼라이저를 별도로 지정할 수 있습니다.

|**속성**|**설명**|
| :- | :- |
|[PointSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/pointsymbolizer)|레이어의 점 도형(Point, MultiPoint)에 사용할 심볼라이저를 지정합니다.|
|[LineSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/linesymbolizer)|레이어의 선 도형(LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString)에 사용할 심볼라이저를 지정합니다.|
|[PolygonSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/polygonsymbolizer)|레이어의 폴리곤 도형(Polygon, CurvePolygon, MultiPolygon, MultiSurface)에 사용할 심볼라이저를 지정합니다.|
### **예제**
이 예제에서 레이어에는 점, 선 및 폴리곤이 포함되어 있습니다. 각 도형 유형을 별도로 스타일링하겠습니다.
