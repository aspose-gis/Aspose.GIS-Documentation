---
title: "레이어드 심볼라이저"
type: docs
url: /ko/net/layered-symbolizer/
weight: 40
description: GIS C# 라이브러리 API의 레이어드 심볼라이저는 특징 또는 레이어를 기반으로 렌더링 순서 모드를 사용하여 여러 심볼라이저를 위에 쌓아 특징을 그립니다.
---

## **레이어드 심볼라이저**
레이어드 심볼라이저는 여러 심볼라이저를 위에 쌓아 특징을 그립니다. 다음 두 가지 렌더링 순서 모드 중에서 선택할 수 있습니다.

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - 레이어드 심볼라이저에 추가된 모든 심볼라이저로 첫 번째 특징을 그린 다음, 다음 특징 그리기를 진행합니다.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - 첫 번째 심볼라이저로 모든 특징을 그린 다음, 다음 심볼라이저로 모든 특징을 그립니다.

### **특징별 렌더링**

### **레이어별 렌더링**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
