---
title: "스트림 및 원격 저장소"
type: docs
url: /ko/net/streams-and-remote-storage/
weight: 70
---

## **다중 파일 형식으로 작업**
일부 GIS 데이터 형식은 콘텐츠를 여러 파일로 분할합니다. 예를 들어, shapefile에는 최소 세 개의 파일(*.shp, *.shx 및 *.dbf)이 있어야 합니다. 이러한 형식은 파일 이름에 대한 미리 정의된 패턴으로 특정 디렉터리 구조에 모든 파일을 저장해야 합니다.

동시에 파일은 원격 서버 또는 스트림을 통해서만 액세스할 수 있는 다른 위치에 저장될 수 있습니다. 스트림에는 파일 형식 드라이버가 데이터를 처리하는 방법을 결정할 수 없도록 파일 이름 및 디렉터리 구조에 대한 정보가 없습니다. Aspose.GIS는 추상 경로 메커니즘을 제공하여 이 문제를 해결합니다.

추상 경로는 파일 시스템과 유사한 저장소의 파일(또는 디렉토리)에 대한 경로를 나타냅니다. 저장소는 아카이브에서 FTP 서버까지 파일 및 디렉터리의 개념을 가진 모든 것이 될 수 있습니다. 이는 파일을 열거나 디렉토리를 나열하는 것과 같은 일반적인 파일 작업을 수행하는 방법을 정의합니다.

[AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath)를 상속하고 추상 메서드에 대한 구현을 제공하여 저장소에 대한 파일 작업을 수행하는 방법을 지정할 수 있습니다.
## **쇼케이스: Azure Blob Storage**
Aspose.GIS 예제 리포지토리에는 Azure Blob Storage용 사용자 정의 추상 경로의 완전한 기능 구현 예제가 포함되어 있습니다. 이 쇼케이스는 Azure Blob Storage에서 shapefile을 직접 읽는 방법을 보여줍니다. 다음에서 찾을 수 있습니다: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **단일 파일 형식(GeoJSON, KML)**
GeoJSON 및 KML과 같은 GIS 데이터 형식은 레이어의 모든 데이터를 단일 파일에 저장할 수 있습니다. 파일을 위한 스트림을 얻을 수 있는 경우 사용자 정의 추상 경로를 구현하는 것을 건너뛰고 메서드 [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream)을 사용하여 스트림에 대한 추상 경로 인스턴스를 생성할 수 있습니다.
### **스트림에서 파일 읽기**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **스트림에 파일 쓰기**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
