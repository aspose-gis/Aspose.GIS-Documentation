---
title: "마커 클러스터 심볼라이저"
type: docs
url: /ko/net/marker-cluster-symbolizer/
weight: 65
description: GIS C# 라이브러리 또는 API의 마커 클러스터 심볼라이저는 지정된 거리 내에서 마커를 클러스터링할 수 있습니다.
---

## **마커 클러스터 심볼라이저**
마커 클러스터 심볼라이저는 고급 심볼라이저 중 하나입니다. 지정된 거리 내에서 마커를 클러스터링할 수 있습니다.

이 C# 예제에서는 클러스터 중심을 빨간색 원으로 그렸습니다. 또한 각 클러스터에 대해 고유한 스타일을 설정하는 FeaturesBasedConfiguration 함수를 사용하여 모든 중첩 클러스터 포인트를 다른 색상으로 그렸습니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterMarkerSymbolizer.cs" >}}

결과는 다음과 같습니다:

![points cluster](points-cluster.png)

## **총 항목 그리기**

이 샘플은 클러스터의 총 항목 수를 표시합니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterTextSymbolizer.cs" >}}

결과는 다음과 같습니다:

![digits cluster](digits-cluster.png)
