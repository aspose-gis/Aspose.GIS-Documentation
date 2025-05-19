---
title: "Aspose.GIS 업데이트: 기능 및 지오메트리 편집 및 데이터베이스에 변경 사항 저장"
type: docs
url: /ko/net/showcases/saving-changes-to-database/
description: "이 문서는 매핑 애플리케이션에서 지오메트리와 기능의 변경 사항을 감지하고 저장하는 기능을 중심으로 Aspose.GIS 라이브러리의 최근 개선 사항을 살펴봅니다."
weight: 80
---
# Aspose.GIS 업데이트: 기능 및 지오메트리 편집 및 데이터베이스에 변경 사항 저장

## 소개

[Aspose.GIS](https://www.nuget.org/packages/Aspose.gis) 라이브러리의 최근 변경 사항 중 일부를 강조하는 것이 중요합니다. 이 문서에서는 데이터베이스에서 지오메트리와 기능의 변경 사항을 감지하고 저장하는 새로운 기능을 논의합니다.

데모 예제로 ["Draw a map. A sliding map with tiles"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) 문서에 설명된 애플리케이션을 계속 사용하고 지도에서 객체 편집 기능을 추가하여 약간 확장합니다. 데이터 세트는 이전 문서와 동일하게 유지됩니다.

## 프론트엔드

지오메트리 수정 기능의 데모를 위해 [leaflet](https://leafletjs.com/)용 인기 있는 오픈 소스 확장을 선택했습니다 — [leaflet-geoman](https://geoman.io/).

libman.json 파일을 통해 이 라이브러리를 추가합니다:
![Libman](libman.png)

다음으로 페이지에 스타일과 스크립트를 연결합니다:
```razor
@section Styles {
    <link href="~/lib/leaflet/leaflet.min.css" rel="stylesheet" />
    <link href="~/lib/contagt/leaflet-geoman-free/dist/leaflet-geoman.min.css" rel="stylesheet" />
    <link href="~/css/map.css" rel="stylesheet" asp-append-version="true"/>
}

@section Scripts {
    <script src="~/lib/leaflet/leaflet.js"></script>
    <script src="~/lib/contagt/leaflet-geoman-free/dist/leaflet-geoman.min.js"></script>
    <script src="~/js/map.js" asp-append-version="true"></script>
}
```

데모 목적으로 편집 기능을 건물로 제한합니다. 사용자는 지도에서 왼쪽 마우스 버튼을 클릭하고 해당 위치에 건물이 있으면 강조 표시되어 편집 가능하게 됩니다. 이는 타일 위에 추가 레이어를 겹쳐서 달성됩니다.

사용자가 지도를 클릭하면 Leaflet 라이브러리는 클릭의 지리 공간 좌표를 계산합니다. 이러한 좌표를 백엔드로 보내고 클릭한 점과 교차하는 지오메트리를 데이터베이스에서 검색합니다. 이러한 지오메트리에 건물들이 있으면 반환합니다.

건물은 백엔드에서 `GeoJSON` 형식으로 반환되고 편집을 위한 별도의 레이어로 지도에 추가됩니다. 클릭을 처리하는 방법은 다음과 같습니다:
```javascript
var featuresLayer = L.featureGroup().addTo(map);

map.on('click', function (e) {
    var latlng = e.latlng;
    var featureFound = false;

    console.log(latlng.lat + ' ' + latlng.lng);

    featuresLayer.eachLayer(function (layer) {
        if (layer.getBounds && layer.getBounds().contains(latlng)) {
            featureFound = true;
            return;
        }
    });

    if (!featureFound) {
        loadGeoJSON(latlng.lat, latlng.lng)
            .then((addedFeatureLayer) => {
                if (addedFeatureLayer) {
                    addedFeatureLayer.addTo(featuresLayer);
                    addedFeatureLayer.pm.enable();
                    console.log('Feature added.');
                } else {
                    console.log('No feature to add.');
                }
            });
    }

    featureFound = false;
});
```

편집 가능한 지오메트리를 위한 영구 레이어 그룹인 `featuresLayer`를 지도에 추가했습니다. 이미 로드된 지오메트리에서 클릭이 이루어졌는지 확인하고 그렇지 않은 경우 건물 폴리곤을 로드하기 위해 백엔드로 요청합니다. 로드된 기능 레이어를 featuresLayer에 추가하고 편집 모드를 활성화합니다.

기능을 로드하고 `GeoJSON`으로 변환하는 함수는 다음과 같습니다:
```javascript
function loadGeoJSON(lat, lng) {
    return fetch(`/features?lat=${lat}&lng=${lng}`)
        .then(response => response.json())
        .then(data => {
            if (data && data.features && data.features.length > 0) {
                return L.geoJSON(data);
                
            } else {
                return null;
            }
        })
        .catch(error => console.error('Error loading a feature:', error));
}
```

편집 세션 후 사용자는 사용자 지정 `Save` 버튼을 클릭합니다:

![Save](save-btn.png)

페이지를 새로 고침하고 변경 사항을 확인하십시오:

![Changes](changes.png)

불행히도 `tiles.redraw()` 함수는 이전에 로드된 타일이 캐시되어 `Ctrl + F5`를 통해 지도를 강제로 새로 고쳐야 제대로 작동하지 않습니다.

저장 버튼을 누르는 핸들러는 다음과 같습니다:
```javascript
function saveResult() {
    if (featuresLayer.getLayers().length === 0) {
        console.log('There are no layers to send to the server.');
        return;
    }
    sendGeoJSONToServer()
        .then(() => {
            console.log('clear and update map');
            featuresLayer.clearLayers();
            tiles.redraw();
        });
}

function sendGeoJSONToServer() {
    var geojsonData = featuresLayer.toGeoJSON();

    return fetch('/features', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/geo+json'
        },
        body: JSON.stringify(geojsonData)
    })
        .then(data => {
            console.log('The data has been successfully sent to the server.');
        })
        .catch(error => {
            console.error('Error when sending GeoJSON:', error);
        });
}
```

## 백엔드

여기에서 새로운 컨트롤러 `FeaturesController`를 추가하고 전송된 좌표에 따라 하우스/기능을 추출하는 핸들러를 만듭니다.

SQL 요청은 다음과 같습니다:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

좌표는 원래 클라이언트 요청의 좌표계 (WGS 84)를 나타내는 점으로 변환된 다음 데이터베이스 데이터가 표시되는 시스템 (Web Mercator)로 번역됩니다. 건물로 표시된 지오메트리에 대한 교차점을 찾습니다.

요청 실행 및 클라이언트로 데이터 전송은 이전 문서에서 논의한 것과 유사하게 발생합니다:
```csharp
VectorLayer inputLayer;

using (var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary"))
{
    var dataSource = Drivers.PostGis
        .FromQuery(query)
        .GeometryField("way")
        .AddAttribute("osm_id", AttributeDataType.Long)
        .AddAttribute("name", AttributeDataType.String)
        .AddAttribute("building", AttributeDataType.String)
        .Build();

    conn.Open();

    inputLayer = await dataSource.ReadAsync(conn);
}

var jsonStream = new MemoryStream();

inputLayer.SaveTo(AbstractPath.FromStream(jsonStream), Drivers.GeoJson);

var result = Encoding.UTF8.GetString(jsonStream.ToArray());

return new ContentResult()
{
    Content = result,
    ContentType = "application/geo+json"
};
```
작은 차이점과 함께: 메모리 레이어를 GeoJSON으로 메모리에 스트림으로 저장한 다음 문자열로 변환하여 클라이언트로 보냅니다.

이제 Aspose.GIS 업데이트의 핵심인 데이터베이스에 변경 사항을 저장합니다. `Edit()` 메서드가 이를 처리합니다. 요청 본문을 완전히 로드하여 메모리로 읽고 스트림으로 읽습니다:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync(); 
Request.Body.Position = 0;
```
다음으로 GeoJSON 형식의 편집된 기능을 읽습니다:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
다음 단계는 전송된 기능 집합에서 데이터베이스의 해당 기능에 대한 고유 식별자를 나타내는 속성을 추출하는 것입니다. 편집을 위한 특수 레이어를 채우기 위해 요청을 구성하고 해당 데이터 소스를 구축합니다:
```csharp
var ids = string.Join(", ", inputLayer.Select(x => x.GetValue<long>("osm_id")));

var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
               FROM public.planet_osm_polygon
               WHERE osm_id IN ({ids});";

var dataSource = Drivers.PostGis
    .FromQuery(query)
    .GeometryField("way")
    .AddAttribute("osm_id", AttributeDataType.Integer, System.Data.DbType.Int64)
    .AddAttribute("name", AttributeDataType.String)
    .AddAttribute("building", AttributeDataType.String)
    .AsTrackableForChanges("public.planet_osm_polygon", "osm_id", true)
    .Build();
```
`AsTrackableForChanges` 메서드를 구성하는 것에 주목하십시오. 이것은 변경 사항을 추적할 수 있는 특정 데이터 소스를 만들 것을 나타내는 특수 방법입니다. 첫 번째 매개변수는 변경 요청이 전송되어야 하는 테이블을 지정합니다. 두 번째는 데이터베이스의 변경 사항을 만들기 위해 식별자로 간주될 속성을 나타냅니다. 가장 흥미로운 부분은 세 번째 매개변수입니다. True로 설정되면 레이어는 두 번째 매개변수에 따라 중복 항목이 나타나는 것을 추적하고 새 것으로 이전 기능을 "덮어쓰기"합니다. 그러나 편집 결과의 경우 즉, 동일한 식별자로 새 기능이 추가되는 경우 이전 값에 대한 비교 변경 사항에 따라 `UPDATE` 명령이 생성됩니다. 세 번째 매개변수가 false로 설정되면 초기화 중 또는 편집 중에 중복 항목이 나타나면 예외가 발생합니다.

속성 이름은 편집 가능한 테이블의 필드 이름으로 사용됩니다. 변경 감지에 관한 중요한 점을 주목하는 것이 중요합니다. 새로 추가되거나 수정된 유형에 대해 정확하게 일치하도록 레이어에 저장될 속성의 정확한 데이터 유형을 지정해야 합니다. 예를 들어 osm_id가 Int32 유형인 새 기능을 추가하지만 레이어에서 지정된 속성 유형이 Int64이면 이는 두 개의 다른 값으로 처리됩니다. `Equal`s 메서드가 `Int64.Equals(Int32)`와 같이 보이는 것을 찾지 않기 때문입니다. 향후 버전에서는 이 동작을 검토하고 가능한 경우 수정합니다. 세 번째 매개변수 유형은 데이터베이스 테이블의 대상 데이터 유형으로 저장 중에 적용됩니다.

다음으로 데이터베이스에 연결하고 테이블에서 데이터를 읽습니다:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
트랜잭션이 데이터베이스 수준에서 올바르게 작동하려면 현재 트랜잭션을 두 번째 매개변수로 읽기 작업에 전달하는 것이 중요합니다.

다음으로 변경 사항을 데이터베이스로 보내기 전에 일련의 변환을 수행해야 합니다:
```csharp
var transformer = SpatialReferenceSystem.Wgs84.CreateTransformationTo(SpatialReferenceSystem.WebMercator);

foreach (var feature in inputLayer)
{
    feature.Geometry = transformer.Transform(feature.Geometry);
    ((Geometry)feature.Geometry).HasZ = false;
}

foreach (var feature in inputLayer)
{
    var replacingId = feature.GetValue<long>("osm_id");
    var toReplaceIndex = editLayer.TakeWhile(x => x.GetValue<long>("osm_id") != replacingId).Count();
    editLayer.ReplaceAt(toReplaceIndex, feature);
}

await dataSource.SubmitChangesAsync(editLayer, conn, transaction);

transaction.Commit();
```
Leaflet은 WGS 84 좌표계에서 지오메트리를 생성하지만 데이터베이스 스키마는 Web Mercator에 저장해야 합니다. Web Mercator 시스템으로 변환하려면 특수 `transformer` 개체를 만들고 이를 변환하는 데 사용합니다.

또한 leaflet은 지오메트리 좌표의 세 번째 매개변수 Z를 0 값으로 채웁니다. 그러나 이 매개변수는 데이터베이스 스키마에서 고려되지 않으므로 `HasZ` 값을 false로 설정하여 해당 존재를 제거합니다.

최종 단계는 클라이언트에서 받은 기능으로 동일한 osm_id를 가진 기존 기능을 바꾸어 변경 사항을 적용하는 것입니다. 이 작업은 이전 인스턴스에 대한 변경 사항을 감지하여 데이터베이스로 명령 INSERT, DELETE 및 UPDATE를 보냅니다.

끝까지 읽어주셔서 감사합니다. 전체 코드는 다음 리포지토리에서 사용할 수 있습니다: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)