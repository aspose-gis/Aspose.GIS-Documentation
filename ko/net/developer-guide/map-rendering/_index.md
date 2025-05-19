---
title: 지도 렌더링을 이미지 SVG, PNG, JPG로 변환하는 GIS C# 라이브러리
linktitle: "지도 렌더링"
type: docs
url: /ko/net/map-rendering/
weight: 50
description: GIS C# API를 사용하면 Shapefile, FileGDB, GeoJSON, KML 형식에서 지도를 렌더링하고, 고급 스타일을 적용하며, 래스터 형식에서 지도를 그릴 수 있습니다.
---

## **지도 렌더링 개요**
Aspose.GIS for .NET C# API를 사용하면 Shapefile, FileGDB, GeoJSON, KML 또는 기타 [지원되는 파일 형식](/gis/net/supported-file-formats/)에서 지도를 SVG, PNG, JPEG 또는 BMP로 렌더링할 수 있습니다.

다음은 기본 설정을 사용하여 shapefile에서 SVG로 지도를 렌더링하는 방법을 보여주는 C# 코드입니다.



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



다음은 결과입니다.



![지도 렌더링](map_rendering.png)

코드에 대해 자세히 살펴보겠습니다.

먼저 [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map) 객체를 인스턴스화합니다. 이는 다양한 소스의 레이어 모음으로 렌더링할 수 있습니다. Map은 표시될 크기를 가지고 있습니다. 여기서는 지도를 너비 800픽셀, 높이 400픽셀로 설정합니다.

Map은 using 문 안에 포함되어 있다는 점에 유의하십시오. 이는 지도가 추가된 모든 리소스를 추적하고 렌더링이 완료되고 Map 객체가 삭제될 때 해당 리소스를 삭제하기 때문에 필요합니다.

다음으로 파일을 통해 레이어를 지도에 추가합니다. 각 레이어는 추가된 순서대로 이전 레이어 위에 렌더링됩니다. 벡터 레이어를 여는 방법에 대한 자세한 내용은 [여기](/gis/net/working-with-vector-layers/)를 참조하십시오.

마지막으로 [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1)를 호출하여 지도를 파일로 렌더링합니다. 결과 파일을 저장할 경로와 사용할 렌더러를 지정합니다. 클래스 [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers)에는 Aspose.GIS에 포함된 모든 렌더러에 대한 참조가 있습니다. 예를 들어, 위의 예에서 Renderers.Png 대신 Renderers.Svg를 지정하여 지도를 PNG 파일로 렌더링할 수 있습니다.

## **고급 스타일**
Aspose.GIS API를 사용하면 원하는 모양을 얻기 위해 렌더링 및 기능 스타일을 사용자 정의 할 수 있습니다.

![고급 스타일](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}

## **지도에 래스터 그리기**
Aspose.GIS for .NET을 사용하면 래스터 형식에서 지도를 렌더링 할 수 있습니다.

### **기본 설정으로 렌더링**
다음은 기본 설정을 사용하여 GeoTIFF에서 SVG로 지도를 렌더링하는 방법입니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![기본 래스터](default_raster.png)

### **왜곡된 래스터 렌더링**
Aspose.GIS를 사용하면 왜곡된 래스터 셀로 래스터를 렌더링 할 수 있습니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![왜곡된 래스터](skew_raster.png)

### **극좌표 공간 참조로 렌더링**
Aspose.GIS를 사용하면 지도 렌더링 프로세스에서 극좌표 공간 참조를 사용할 수 있습니다.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![등각 투영 국가](gnomonic_countries.png)
