---
title: "지도 그리기. 타일이 있는 슬라이딩 지도."
type: docs
url: /ko/net/showcases/sliding-map-with-tiles/
description: "타일을 그리고 그것으로 슬라이딩 지도를 만드는 방법."
weight: 80
aliases:
 - /ko/net/showcases/tiles/
---
# 지도 그리기. 타일이 있는 슬라이딩 지도.
이 문서에서는 [Aspose.GIS](https://www.nuget.org/packages/Aspose.GIS/) 라이브러리와 공개 데이터를 사용하여 실시간으로 생성되는 슬라이딩 지도를 만드는 방법을 보여드리겠습니다. 새로운 라이브러리 기능을 통해 SQL 쿼리를 통해 데이터베이스에서 GIS 데이터를 쿼리할 수 있습니다. 다음은 결과로 얻어야 하는 것입니다:

![결과](result.png)

Repository 소스 코드 [여기](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest).

## 데이터 준비.

먼저 데이터베이스에 로드할 지리 공간 정보가 필요합니다. `OpenStreetMap`은 그러한 정보의 인기 있는 소스 중 하나이므로 사용해 보겠습니다. 가장 편리한 방법은 제 생각에는 https://download.geofabrik.de/ 에서 pbf 형식으로 데이터를 추출하는 것입니다. 예를 들어 [헝가리](https://download.geofabrik.de/europe/hungary-latest.osm.pbf)를 다운로드해 보겠습니다.

다음 단계에서는 작동하는 `PostGIS` 인스턴스가 필요합니다. 물론 로컬에 설치된 버전의 `PostgreSQL`을 사용할 수 있지만 Docker 컨테이너를 사용하는 것이 매우 편리하다고 생각합니다. docker compose 파일을 사용하여 PostGIS를 설치해 보겠습니다:

```yaml
services:
  postgis:
    image: postgis/postgis
    environment:
      - POSTGRES_DB=gis
      - POSTGRES_USER=gis
      - POSTGRES_PASSWORD=password
    ports:
      - 5432:5432
    volumes:
      - d:\\local_folder:/usr/share/gisdata
```

볼륨 `d:\local_folder:/usr/share/gisdata`는 로컬 머신에서 GIS 데이터를 로드하는 데 필요합니다.

다음으로 컨테이너를 실행해 보겠습니다:

```bash
docker compose up
```

`pgAdmin`을 사용하여 데이터베이스 인스턴션에 연결하고 헝가리 데이터베이스를 생성하십시오:

![DB 생성](create_db.png)

또는 SQL 명령을 통해:

```sql
CREATE DATABASE Hungary;
```

이 데이터베이스에 필요한 확장을 추가하십시오:

![확장](add_extention.png)

이는 `postgis` 및 `hstore` 확장입니다. hstore은 키-값 데이터 유형을 사용할 수 있도록 하는 확장입니다. OpenStreetMap은 주요 범주에 속하지 않는 특성을 설명하기 위해 광범위하게 사용하므로 별도의 필드가 생성되지 않고 tags 필드에 저장됩니다.

SQL과 같은 버전의 명령도 있습니다:

```sql
CREATE EXTENSION IF NOT EXISTS hstore;
CREATE EXTENSION IF NOT EXISTS postgis;
```

이제 컨테이너에 연결하고, 내 경우에는 `local_folder-postgis-1`입니다:

```bash
docker exec -it local_folder-postgis-1 sh
```

그리고 데이터베이스로 `pbf` 파일에서 데이터를 가져올 프로그램을 설치하십시오:

```bash
apt-get update && apt-get install -y osm2pgsql
```

`hungary-latest.osm.pbf` 파일이 `local_folder` 폴더에 있는지 확인한 다음 import 명령을 실행하십시오:

```bash
osm2pgsql --create --database=Hungary --user=gis --password --host=localhost --port=5432 --hstore /usr/share/gisdata/hungary-latest.osm.pbf
```

헝가리의 경우 이 명령을 완료하는 데 1분 30초가 걸렸습니다. `--create` 옵션은 새 데이터베이스의 간단한 생성 모드를 의미합니다. 그 외에도 데이터를 변경한 경우 업데이트할 수 있는 `--append` 모드도 있습니다:

```bash
osm2pgsql --append --slim OSMFILE
```

`--hstore` 옵션은 애플리케이션에 추가 정보와 기하 도형을 저장하기 위해 hstore 유형의 `tags` 필드를 추가로 생성하도록 지시합니다.

## 백엔드

이제 데이터가 준비되었습니다. 지도를 만드는 다음 단계는 일반적으로 크기가 `256*256`인 특별한 `타일`을 생성하는 백엔드를 만드는 것입니다. 각 타일은 Z(지도의 확대/축소 정도), X(타일 배열의 행) 및 Y(열)와 같은 매개변수의 조합으로 고유하게 식별됩니다. [여기](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames)에서 타일의 본질에 대해 자세히 읽을 수 있습니다.

백엔드는 ASP.NET Core이므로 프로젝트를 시작해 보겠습니다. 따라서 미리 설치된 `ASP.NET Core MVC` 템플릿을 기반으로 프로젝트를 만들어 보겠습니다.

다음으로 프로젝트에 NuGet 패키지 `Aspose.GIS`를 설치하여 타일을 생성합니다:

```cmd
dotnet add package Aspose.GIS --version 24.6.0
```

프로젝트에서 불필요한 파일을 정리하십시오. 구조는 다음과 같아야 합니다:

![솔루션 탐색기](project.png)

그런 다음 wwwroot/lib 폴더의 내용을 삭제하고 `libman`을 통해 종속성을 설치합니다. `libman.json` 파일의 구조는 다음과 같습니다:
```json
{
  "version": "1.0",
  "defaultProvider": "cdnjs",
  "libraries": [
    {
      "library": "leaflet@1.9.4",
      "destination": "wwwroot/lib/leaflet/"
    },
    {
      "library": "bootstrap@5.3.3",
      "destination": "wwwroot/lib/bootstrap/",
      "files": [
        "css/bootstrap-reboot.min.css"
      ]
    }
  ]
}
```

`_Layout.cshtml` 파일에 클라이언트 종속성을 추가하십시오:

```razor
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>@ViewData["Title"] - Aspose.GIS.TilesTest</title>
    <link href="~/lib/bootstrap/css/bootstrap-reboot.min.css" rel="stylesheet" />
    @await RenderSectionAsync("Styles", required: false)
</head>
<body>
    @RenderBody()
    @await RenderSectionAsync("Scripts", required: false)
</body>
</html>
```

그리고 `Index.cshtml`을 편집하십시오:

```razor
@{
    ViewData["Title"] = "Home Page";
}

<div id="map"></div>

@section Styles {
    <link href="~/lib/leaflet/leaflet.min.css" rel="stylesheet" />
    <link href="~/css/map.css" rel="stylesheet" asp-append-version="true"/>
}

@section Scripts {
    <script src="~/lib/leaflet/leaflet.min.js"></script>
    <script src="~/js/map.js" asp-append-version="true"></script>
}
```

이 경우 `bootstrap-reboot.min.css`는 기본 스타일 설정을 재설정하고 `leaflet.min.js`는 타일에서 조각을 모아 지도를 렌더링하는 역할을 합니다. `map.css` 파일에 지도 블록의 높이를 보이는 영역의 전체 높이로 설정해 보겠습니다:

```css
#map {
    min-height: 100vh;
}
```

`map.js` 파일의 내용은 다소 간단하지만 조금 더 흥미롭습니다:

```javascript
var map = L.map('map').setView([47.59995, 19.36623], 13);
const tiles = L.tileLayer('/tiles/{z}/{x}/{y}.png', {
    maxZoom: 19,
    minZoom: 11
}).addTo(map);
```

여기서는 leaflet 라이브러리의 API를 사용하며 `'map'` ID의 지도 블록을 지정한 다음 `setView` 메서드에서 초기 지도 로드를 시작할 위치의 좌표와 축척(예: 13)을 설정합니다. `tileLayer` 메서드는 서버에 대한 타일 요청 패턴 문자열을 허용합니다. 이 주소는 타사 타일 서버에 액세스하기 위한 절대 경로이거나 현재 사례처럼 상대적일 수 있습니다. 아직 구현되지 않은 경로는 `/tiles/{z}/{x}/{y}.png`입니다. 이것은 우리 이야기에 가장 중요한 부분이며 이제 구현해야 합니다.

타일을 생성하기 위한 요청 처리기를 구현하려면 먼저 `Program.cs` 파일에 별도의 경로를 정의해 보겠습니다:

```csharp
app.MapControllerRoute(name: "tiles",
  pattern: "tiles/{z}/{x}/{y}.png",
  defaults: new { controller = "Tiles", action = "Index" });

app.MapControllerRoute(
  name: "default",
  pattern: "{controller=Home}/{action=Index}/{id?}");
```

여기서 두 개의 경로가 정의되어 있으며, 첫 번째는 타일용이고 두 번째는 표준 경로입니다. `MapControllerRoute`의 경우 순서가 중요하므로 예기치 않은 동작을 피하려면 타일에 대한 경로는 표준 경로보다 먼저 배치하는 것이 좋습니다.

다음으로 핸들러 자체로 이동해 보겠습니다. `TilesController.cs` 컨트롤러를 만드십시오. 단일 작업이 다음과 같습니다:

```csharp
public async Task<ActionResult> Index(int z, int x, int y)
```

이제 모든 필요한 데이터가 해당 좌표 시스템에서 타일을 덮는 경계 상자를 계산할 수 있습니다. 현재 구현에서는 데이터베이스의 데이터가 Web Mercator 좌표 시스템에 저장됩니다. OpenStreetMap은 기본적으로 이 좌표 시스템에서 데이터를 제공합니다. Web Mercator는 거의 전체 지구를 다루고 거리는 미터 단위로 측정되므로 다른 것보다 계산이 간단하기 때문에 다양한 인기 있는 서비스에서 매핑에 가장 자주 사용되는 투영(좌표 시스템 형식)입니다. 예를 들어 `WGS 84`와 달리 거리가 각도로 측정되기 때문입니다.

```csharp
VectorLayer inputLayer;
using (var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary"))
{
  var builder = new DatabaseDataSourceBuilder();

  builder
    .FromQuery(query)
    .GeometryField("way")
    .AddAttribute("osm_id", AttributeDataType.Long)
    .AddAttribute("addr:housenumber", AttributeDataType.String)
    .AddAttribute("building", AttributeDataType.String)
    .AddAttribute("name", AttributeDataType.String)
    .AddAttribute("source", AttributeDataType.String)
    .AddAttribute("admin_level", AttributeDataType.Integer)
    .AddAttribute("place", AttributeDataType.String)
    .AddAttribute("landuse", AttributeDataType.String)
    .AddAttribute("water", AttributeDataType.String);
  conn.Open();

  var inputLayer = await builder.Build().ReadAsync(conn);
}
```

우리는 단일 레이어를 받았는데, 이는 타일에 교차하는 모든 기하 도형을 포함합니다.

좋아요, 이제 도시, 수역 또는 숲과 같이 지도를 조금 색칠할 수 있습니다. 이렇게 하려면 데이터 가져오기 단계에서 생성된 `planet_osm_polygon`, `planet_osm_roads`, `planet_osm_point`, `planet_osm_line` 테이블에 해당하는 다른 기하 도형 및 속성에 관련된 여러 레이어로 단일 레이어를 분리해야 합니다. 다음은 예입니다:

```csharp
var cities = inputLayer.Where(x => x.GetValue<string>("place") == "city");
citiesLayer = CopyToNewLayer(cities, inputLayer);

var forest = inputLayer.Where(x => x.GetValue<string>("landuse") == "forest");
forestLayer = CopyToNewLayer(forest, inputLayer);

var water = inputLayer.Where(x => !x.IsValueNull("water"));
waterLayer = CopyToNewLayer(water, inputLayer);
```

아래에서 이러한 레이어를 사용하는 방법을 알 수 있습니다. `CopyToNewLayer` 함수는 보조 함수이며 이 문서에서는 중요하지 않으므로 시작 부분에 참조한 저장소에서 구현을 볼 수 있습니다.

이제 PNG 타일로 렌더링하고 클라이언트에 반환하기만 하면 됩니다. 다음은 샘플 코드입니다:

```csharp
using var map = new Map(256, 256);
var pngStream = new MemoryStream();
var labeling = new RuleBasedLabeling
{
  { x => x.GetValue<string>("source") == "polygon",  new SimpleLabeling("addr:housenumber") },
  LabelingRule.CreateElseRule(new SimpleLabeling("name"))
};

map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);            
map.Add(citiesLayer, new SimpleFill { FillColor = Color.PeachPuff }, labeling);
map.Add(forestLayer, new SimpleFill { FillColor = Color.PaleGreen }, labeling);
map.Add(waterLayer, new SimpleFill { FillColor = Color.SkyBlue }, labeling);
map.Add(buildingsLayer, new SimpleFill { FillColor = Color.SandyBrown }, labeling);
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

pngStream.Seek(0, SeekOrigin.Begin);

return File(pngStream, "image/png");
```

여기서 표준 타일 크기 256x256으로 `Map` 개체가 생성됩니다. 기본적으로 `Map`은 타일을 렌더링하기 위한 캔버스입니다. 다음으로 레이블링을 위한 특별한 객체를 초기화하고, 예를 들어 주소 번호, 거리 이름 등과 같이 그려진 기하 도형에 텍스트를 렌더링하는 규칙이 전달됩니다. 이 경우 다각형이 아니고/또는 `addr:housenumber` 속성이 비어 있으면 데이터가 `name` 속성에서 가져옵니다.

중요한 점은 Map 객체는 렌더링할 좌표계를 명시적으로 지정해야 합니다:

```csharp
map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
```

다음으로 실제 타일 영역을 설정해야 하며 확장된 영역이 아니라 데이터베이스에서 요청한 영역입니다. 이렇게 하려면 `Extent` 속도를 통해 렌더링 영역을 명시적으로 설정하십시오:

```csharp
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);
```

그런 다음 레이어를 순차적으로 타일에 추가합니다. 첫 번째는 모든 것 아래에 추가되고 마지막은 위에 있습니다.

마지막으로 메모리의 바이트 스트림으로 타일을 렌더링한 다음 스트림을 시작 부분으로 재설정하고 ASP.NET Core 플랫폼에 전달하여 클라이언트로 더 전송하십시오:

```csharp
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

pngStream.Seek(0, SeekOrigin.Begin);

return File(pngStream, "image/png");
```

희망적으로 기본 지도 구축 아이디어와 기술을 전달할 수 있었습니다. 실험에 행운이 있기를 바랍니다.