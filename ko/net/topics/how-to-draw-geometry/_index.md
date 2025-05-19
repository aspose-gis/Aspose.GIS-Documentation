---
title: "지도에 도형 그리는 방법"
type: docs
url: /ko/net/how-to-draw-geometry
weight: 70
---

지도를 사용하여 기하학적 객체를 생성하고 표시하려면 먼저 **기하학적 객체**를 만들어야 합니다. 사용할 수 있는 두 가지 방법이 있습니다.

- **각 도형 기능 유형에 대한 생성자**
이 방법은 각 도형 기능 유형에 대해 사용자 지정 생성자를 사용하는 것을 포함합니다. 예를 들어, 점을 만들려면 다음 코드를 사용합니다.

```
Point point = new Point(40.7128, -74.006);
```

그러나 이 방법은 폴리라인이나 컬렉션과 같이 복잡한 객체를 생성할 때 관리하기 어려워질 수 있습니다. 결과적으로 개발자는 많은 줄의 코드를 추가해야 할 수 있으며 코드 가독성이 떨어집니다. 초기화 중에 데이터 무결성을 보장하는 것도 어려울 수 있습니다. 예를 들어, 내부에 구멍이 있는 다각형을 만드는 다음 예제를 고려하십시오.

```
Polygon polygon = new Polygon();

LinearRing ring = new LinearRing();
ring.AddPoint(50.02, 36.22);
ring.AddPoint(49.99, 36.26);
ring.AddPoint(49.97, 36.23);
ring.AddPoint(49.98, 36.17);
ring.AddPoint(50.02, 36.22);

LinearRing hole = new LinearRing();
hole.AddPoint(50.00, 36.22);
hole.AddPoint(49.99, 36.20);
hole.AddPoint(49.98, 36.23);
hole.AddPoint(50.00, 36.24);
hole.AddPoint(50.00, 36.22);

polygon.ExteriorRing = ring;
polygon.AddInteriorRing(hole);
```

이 접근 방식의 또 다른 단점은 초기화에 대한 데이터의 균일성이 부족하다는 것입니다. 프로젝트 내에서 상수 또는 파일 저장소를 만들 수 없습니다.

- **WKT (Well-Known Text)**
이 방법은 기하학적 객체를 생성하기 위한 표준화된 방법을 제공하는 WKT(Well-Known Text)에서 기하학을 생성하는 것을 포함합니다. 다음 코드는 점과 선을 만드는 방법을 보여줍니다.

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

이 접근 방식은 문자열을 구문 분석해야 하므로 성능이 약간 저하될 수 있지만 더 복잡한 객체를 생성하는 것을 단순화합니다.

WKT에 대한 자세한 내용은 다음 기사에서 확인할 수 있습니다: "Exporting and Importing Data from/to WKT and WKB."

지도에 기하학적 객체 표시
기하학적 객체를 만들었으면 다음 단계는 지도에 표시하는 것입니다. 지도는 다양한 소스 및 형식에서 로드된 레이어를 표시할 수 있지만 InMemoryLayer는 소스가 필요하지 않은 레이어입니다.

**기하학적 객체를 표시하려면** InMemoryLayer를 생성하고 객체를 추가합니다.

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

이제 **이 레이어를 지도에 표시하고 다음 코드를 사용하여 SVG와 같은 지원되는 형식으로 파일을 만들 수 있습니다.**

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

레이어를 추가하고 지도에 표시하면 지원되는 형식 중 하나로 저장할 수 있습니다. 이 예에서는 잠재적인 비트맵 지원 문제점을 피하기 위해 SVG 형식을 선택합니다. Net 6.0은 클라이언트 측 Blazor WebAsm에서 비트맵 이미지를 렌더링할 수 없다는 제한 사항이 있는 제한된 비트맵 지원을 가지고 있다는 점에 유의하는 것이 중요합니다. 따라서 지도를 저장할 형식을 선택할 때 대상 플랫폼의 제한 사항을 고려하고 호환되는 형식을 선택해야 합니다.

기사는 기본, 일반 스타일로 지도에 기하학적 객체를 생성하고 표시하는 방법을 설명합니다. 그러나 Aspose 라이브러리는 요구 사항에 맞게 사용자 지정할 수 있는 광범위한 스타일링 옵션을 제공합니다. 이러한 옵션을 탐색하려면 [Aspose.MapRendering 문서]( https://docs.aspose.com/gis/net/map-rendering/)를 참조하십시오. 여기에는 다양한 스타일링 기술을 사용하여 지도의 시각적 매력을 향상시키는 방법에 대한 자세한 정보가 제공됩니다.

**요약하자면**, 지도에 기하학적 객체를 만들려면 각 도형 기능 유형에 대한 생성자를 사용하거나 WKT에서 기하학을 생성할 수 있습니다. 객체를 표시하려면 레이어에 배치하고 기본 지도 스타일로 레이어를 지도에 표시합니다. 지도를 SVG와 같은 지원되는 형식으로 저장하고 라이브러리를 사용하여 스타일링 옵션을 탐색하십시오. 또한 라이브러리는 구현하는 방법을 이해하는 데 도움이 될 수 있는 문서에서 제공된 [링크]( https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer)를 클릭하여 완성된 예제를 볼 수 있는 기회를 제공합니다.
