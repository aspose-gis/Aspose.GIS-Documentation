---
title: "최적 경로 탐색기"
type: docs
url: /ko/net/optimal-path-finder
weight: 70
---

## 요약

도로 네트워크에서 최단 경로를 찾는 것은 지도상의 지점 간 이동하는 가장 효율적인 방법을 결정하기 위한 분석 과정입니다. 이 도구는 여러 정류장을 포함하는 최적의 경로를 생성하거나 다른 위치 간 거리 및 이동 시간을 측정하는 데 유용할 수 있습니다. 각 호출 시, 당사의 기술은 단일 또는 여러 차량에 대한 최적의 경로를 찾을 수 있습니다. 예를 들어, 배송 상품을 위한 최적의 경로를 찾거나 다양한 승객에게 집에서 직장까지의 최적 통근 거리를 결정하는 데 도움이 될 수 있습니다.

## 알고리즘 기능

당사의 라이브러리는 지도상의 두 지점 간 가장 **최적의 경로**를 구축할 수 있는 기능을 제공합니다. 다음과 같은 주요 특징을 가지고 있습니다.

1. 도로 및 장애물을 고려하여 지도에서 최적의 경로 검색: 당사는 도로뿐만 아니라 트레일, 보행자 통로, 최적 경로 선택에 영향을 미칠 수 있는 장애물과 같은 비포장도로도 고려합니다.

2. 도로에서만 최적의 경로 검색: 도로에서만 경로를 찾아야 하는 경우 이 기능을 제공합니다. 예를 들어, 도로에서만 이동이 허용된 차량에 유용합니다.

3. 도로별 속도 설정: 서로 다른 도로에 대해 서로 다른 속도를 할당할 수 있습니다. 예를 들어, 주요 고속도로에는 더 높은 속도를 설정하고 좁은 길에는 더 낮은 속도를 설정할 수 있습니다.

4. 직사각형 장애물 설정: 최적 경로를 구축할 때 고려해야 하는 지도상의 직사각형 장애물을 정의할 수 있습니다. 이는 건물이나 호수(근사치)와 같은 알려진 장애물이 있을 때 유용합니다.

5. 도로 검색 반경 제한: 검색 시간을 줄이고 특정 영역에만 집중하기 위해 도로 검색 반경을 제한할 수 있습니다.

6. 성능 및 정확도 제어: 알고리즘의 성능과 정확도를 제어할 수 있는 기능을 제공합니다. 원하는 검색 속도와 경로 구축 정확도 간의 균형을 달성하도록 미세 조정할 수 있습니다.

다음으로, 이러한 기능 각각에 대한 더 자세한 설명을 제공하고 해당 응용 프로그램의 예를 살펴봅니다.

## 솔루션 접근 방식

경로 탐색은 복잡한 작업이지만 개발 커뮤니티에서 인정받는 여러 가지 좋은 신뢰성 있는 알고리즘이 있습니다.

당사의 구현에서는 수정된 Lee's 알고리즘을 사용했습니다. 평면에 셀 그리드가 있습니다. 시작점에서 파동이 8방향(대각선 포함)으로 이웃 셀에 전파되어 각 셀에 도달하는 데 필요한 시간을 계산합니다. 인접한 셀에는 장애물 또는 도로가 있을 수 있습니다. 도로에는 서로 다른 속도 계수가 있을 수 있습니다. 따라서 당사는 시작 셀에서 각 셀에 도달하는 데 걸리는 시간으로 그리드를 "표시"합니다. 특정 반경 내 또는 목표 지점에 도달할 때까지. 목표 지점에 도달하면 그리드를 사용하여 역 경로를 구축합니다.

도로 네트워크에서 최적의 경로를 결정하려면 여러 단계를 거쳐야 합니다. 먼저 도로를 정의하고 각 도로에서의 이동 속도를 지정해야 합니다. 또한 경로 순회에 영향을 미칠 수 있는 인공 및 자연 장애물의 존재를 고려해야 합니다. 그런 다음 검색 시작점과 목표점을 지정합니다. 이러한 예비 단계가 완료되면 실제 경로 탐색을 진행할 수 있습니다. 결과는 점 좌표 목록으로 표현된 경로가 됩니다.

최적의 경로는 선택한 운송 모드에 따라 달라질 수 있다는 점에 유의하는 것이 중요합니다. 이동 속도와 장애물 세트가 다를 수 있기 때문입니다. 따라서 최적의 경로를 검색할 때 각 유형의 운송에 대해 다른 도로 및 장애물 세트를 사용해야 합니다.

## GitHub 데모 프로젝트

당사 라이브러리의 기능을 더 잘 이해하려면 [사용 예](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths)를 고려해 보겠습니다. 이 코드는 경로 탐색 알고리즘에서 도로와 장애물을 설정하고 최적의 경로를 찾는 방법을 보여줍니다.

예제는 다음 단계로 구성됩니다.

1. 도로 정보(RoadInfo) 목록을 생성합니다. 여기에는 도로 세그먼트(Segment) 및 이동 속도(Velocity)에 대한 정보가 포함됩니다.
2. 빠른 도로를 목록에 추가합니다.
3. 느린 순환 도로를 목록에 추가합니다.
4. 웨이 레이어 생성기(WayLayerGenerator)를 만들고 도로를 생성기에 추가합니다.
5. 지정된 반경(radius)을 사용하여 시작점(startPoint)에서 목표 지점(goalPoint01, goalPoint02, goalPoint03)까지 여러 경로를 검색합니다.
6. 지도에 표시하기 위한 도로 레이어(roadsLayer)를 준비하고 도로 객체를 추가합니다.
7. 지도에 표시하기 위한 웨이 레이어(wayLayer)를 준비하고 각 찾은 경로에 대한 기하학적 객체를 만듭니다.
8. 지정된 경로에서 지도를 [표시](https://docs.aspose.com/gis/net/how-to-draw-geometry/)하고 지정된 경로에 지도를 저장합니다.

이 코드는 도로 정보와 웨이 레이어 생성기를 사용하여 지정된 점에 대한 지도상의 도로 경로를 구축하고 표시합니다.

## 검색 옵션

경로 탐색은 Aspose.Gis.GeoTools.WayAnalyzer 네임스페이스에 있는 **WayLayerGenerator** 클래스를 사용하여 수행됩니다.

WayLayerGenerator 클래스는 시작점에서 목표 지점까지의 경로를 찾는 **FindTheWay 메서드**를 가지고 있습니다. WayLayerGenerator 클래스의 인스턴스를 만들려면 WayOptions를 매개변수로 전달합니다(모든 매개변수는 선택 사항입니다).

- StartPoint: 시작점

- GoalPoint: 대상 점

- Radius: 검색 반경

- Scale: 그리드의 크기

- IsMoveOnlyRoad: 도로에서만 경로를 검색할지 여부

여기서 주목할 만한 특징은 Scale 매개변수입니다. 생성자에서 지정하면 후속 검색에 대한 고정된 크기를 설정합니다. Scale 매개변수가 설정되지 않았지만 StartPoint와 GoalPoint가 설정되면 시작점과 목표 지점 간 거리를 100으로 나눈 값으로 크기를 계산합니다. 다른 모든 경우, Scale의 기본값은 1입니다. 숙련된 사용자의 경우 Scale을 설정하거나 StartPoint와 GoalPoint를 직접 설정하여 도로와 장애물을 그리드에 가장 효율적으로 표현하는 것이 좋습니다(특히 많은 수의 도로와 장애물이 있는 경우).

FindTheWay 메서드를 사용하려면 시작점과 목표점을 지정해야 합니다. 또한 검색 반경(파동이 전파되는 거리)을 설정할 수도 있습니다. 기본적으로 반경은 시작점과 목표 지점 간 거리에 3을 곱한 값으로 계산됩니다. 시작점과 목표점은 서로 가깝거나 매우 멀리 떨어져 있을 수 있으므로 이들 사이의 거리를 기반으로 그리드의 크기를 계산합니다. 현재 크기가 이전 크기와 일치하지 않으면 그리드를 다시 계산합니다. Scale 매개변수를 사용하여 크기를 고정할 수 있습니다. 이 경우 계산되지 않고 그리드가 다시 계산되지 않습니다.

검색을 시작하기 전에 해당 AddRoad 및 AddBlock 메서드를 사용하여 도로 및 장애물 지도를 정의해야 합니다.

**AddRoad 메서드**의 경우 다음을 지정해야 합니다.

- startPoint: 도로의 시작점

- endPoint: 도로의 끝점

- velocity: 도로에서의 이동 속도

**AddBlock 메서드**의 경우 다음을 지정해야 합니다.

- x: 블록 왼쪽 상단 모서리의 x 좌표

- y: 블록 왼쪽 상단 모서리의 y 좌표

- sizeX: x축 크기

- sizeY: y축 크기

이러한 방법을 사용하면 경로 탐색 프로세스를 시작하기 전에 도로 및 장애물 지도를 정의할 수 있습니다.

## 코드 예제

경로 탐색 알고리즘에서 도로와 장애물을 설정하고 최적의 경로를 찾는 방법을 설명하는 몇 가지 코드 예제가 있습니다.

예제 1: 시작점과 목표점 간의 경로 찾기.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**예제 2**: Scale 매개변수를 설정하고 점에 음수 좌표를 지정합니다.

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**예제 3**: IsMoveOnlyRoad 매개변수와 검색 반경을 설정합니다.

```
WayOptions mapGeneratorOptions = new WayOptions();
mapGeneratorOptions.IsMoveOnlyRoad = true;
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddRoad(new Point(100, 100), new Point(140, 150), 10);
generator.AddRoad(new Point(140, 150), new Point(190, 100), 10);
Point startPoint = new Point(100, 100);
Point goalPoint = new Point(190, 100);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 100);
```

**예제 4**: 더 빠른 검색을 위해 Scale 매개변수를 설정합니다.

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**예제 5**: 다중 검색 예제입니다.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddBlock(200, 1700, 1500, 100, 0);
generator.AddBlock(1700, 200, 100, 1600, 0);
generator.AddBlock(200, 200, 1500, 100, 0);
generator.AddRoad(new Point(1000, 1150), new Point(200, 600), 10);
generator.AddRoad(new Point(50, 450), new Point(150, 1850), 10);

Point startPoint = new Point(1000, 1000);
Point goalPoint = new Point(1900, 1000);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 3500);

Point startPoint = new Point(50, 50);
Point goalPoint = new Point(70, 70);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

이러한 코드 예제는 도로 정보와 웨이 레이어 생성기를 사용하여 지정된 점에 대한 지도상의 도로 경로를 구축하고 표시합니다.

**요약하자면**, 최적 경로 탐색기는 도로 네트워크를 분석하고 지도상의 지점 간 가장 효율적인 경로를 결정하는 강력한 도구입니다. 이는 도로 유형, 장애물 및 다양한 속도를 고려하여 최적의 경로를 계산합니다. 도로와 비포장도로에서 모두 경로를 검색할 수 있는 기능뿐만 아니라 검색 반경을 제어하고 성능과 정확성을 조정할 수 있는 기능을 통해 이 알고리즘은 다재다능한 경로 최적화 솔루션을 제공합니다. 다양한 운송 모드를 고려하고 그에 따라 도로 및 장애물 세트를 조정하면 배달 계획 또는 통근 최적화와 같은 다양한 시나리오에서 사용할 수 있습니다. 제공된 코드 예제와 설명은 알고리즘의 기능을 보여주고 이를 활용하는 단계를 설명합니다. 궁극적으로 최적 경로 탐색기는 가장 효율적인 경로를 찾고 도로 네트워크에서의 내비게이션을 개선하는 강력한 방법을 제공합니다.