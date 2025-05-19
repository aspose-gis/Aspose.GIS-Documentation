---
title: C#에서 GPS 교환 형식 GPX 파일 작업하기
linktitle: GPX - GPS 교환 형식
type: docs
url: /ko/net/gpx-gps-exchange/
weight: 60
description: C# GIS 라이브러리를 사용하면 GPS 교환 파일(GPX)에서 기능을 열고 읽을 수 있습니다.
---

## **GPS 교환 파일(GPX) 작업하기**
Aspose.GIS를 사용하면 GPS 교환 파일(GPX)에서 기능을 열고 읽을 수 있습니다.
## **GPX 파일에서 기능 읽기**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **세그먼트의 각 지점에 대한 기능 읽기**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **GPX 파일에 선으로 다각형 쓰기**
GPX 형식은 다각형 및 멀티폴리곤을 지원하지 않습니다. 결과적으로 다른 형식에서 변환이 실패하는 경우가 있습니다. 이 문제를 해결하려면 WritePolygonsAsLines 옵션을 적용해야 합니다.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
