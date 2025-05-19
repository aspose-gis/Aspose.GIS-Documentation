---
title: C#에서 GIS 벡터 레이어 필터링 및 인덱싱
linktitle: 필터링 및 인덱싱
second_title: Aspose.GIS for .NET
type: docs
url: /ko/net/filtering-and-indexing/
weight: 30
description: GIS C# .NET 라이브러리 또는 API를 사용하면 속성 값이나 공간 경계로 GIS 벡터 레이어를 필터링할 수 있습니다. 또한 인덱스를 사용하여 필터링 및 공간 쿼리를 빠르게 할 수 있습니다.
---

Aspose.GIS for .NET을 사용하면 속성 값이나 공간 경계로 레이어를 필터링할 수 있습니다. 또한 인덱스를 사용하여 필터링 및 공간 쿼리를 빠르게 할 수 있습니다.
## **속성 인덱스**
### **인덱스 없이 필터링**
레이어의 속성 값을 기준으로 필터링하는 방법은 다음과 같습니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **인덱스를 사용한 필터링**
위의 코드는 레이어가 한 번만 필터링되는 경우에 적합합니다. 그러나 레이어가 여러 번 쿼리될 가능성이 있는 경우 속성 인덱스의 이점을 누릴 수 있습니다. 속성 인덱스를 빌드하는 데는 시간이 걸리지만, 필터링을 빠르게 하기 위해 여러 번 재사용할 수 있습니다.

다음 예제에서는 속성 인덱스 파일을 사용하여 속성 값을 기준으로 레이어 필터링 속도를 높입니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **필터링된 기능 저장**
필터링된 기능을 레이어에 저장할 수 있습니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **필터링된 기능 렌더링**
필터링된 기능을 렌더링하는 것도 가능합니다. 다음 예제에서는 속성 인덱스를 사용하여 모집구가 2000보다 큰 모든 기능을 빠르게 선택하고 지도로 추가합니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **공간 인덱스**
공간 인덱스는 공간 쿼리를 빠르게 하기 위해 사용됩니다. 속성 인덱스와 마찬가지로 공간 인덱스는 생성 후 재사용됩니다.
### **지점에 가장 가까운 기능 찾기**
공간 인덱스를 사용하여 특정 지점에 가장 가까운 기능을 찾는 속도를 높이는 방법은 다음과 같습니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **지오메트리와 교차하는 기능 선택**
다음 예제에서는 공간 인덱스를 사용하여 지오메트리와 교차하는 기능을 선택하는 속도를 높입니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
