---
title: "Aspose.GIS の更新：フィーチャーとジオメトリの編集、および変更内容をデータベースに保存。"
type: docs
url: /ja/net/showcases/saving-changes-to-database/
description: "この記事では、Aspose.GIS ライブラリの最近の拡張について説明し、特にマッピング アプリケーションにおけるジオメトリとフィーチャーの変更を検出して保存する新しい機能に焦点を当てています。"
weight: 80
---
# Aspose.GIS の更新：フィーチャーとジオメトリの編集、および変更内容をデータベースに保存。

## はじめに

[Aspose.GIS](https://www.nuget.org/packages/Aspose.gis) ライブラリの最近の変更点について説明し、見過ごされないように強調します。この記事では、データベース内のジオメトリとフィーチャーへの変更を検出して保存する新しい機能について説明します。

デモンストレーションの例として、記事["Draw a map. A sliding map with tiles"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/)で説明されているアプリケーションを継続的に使用し、マップ上のオブジェクト編集機能を追加してわずかに拡張します。データセットは前の記事と同じです。

## フロントエンド

ジオメトリの変更機能をデモンストレーションするために、[leaflet](https://leafletjs.com/) の人気のあるオープンソース拡張機能である [leaflet-geoman](https://geoman.io/) を選択しました。

このライブラリを libman.json ファイル経由で追加します。
![Libman](libman.png)

次に、スタイルとスクリプトをページに接続します。
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

デモンストレーションのために、編集機能を建物のみに制限します。ユーザーがマップ上の左マウスボタンをクリックすると、その場所に建物がある場合、建物が強調表示され、編集可能になります。これは、タイルの上に別のレイヤーを重ねることで実現されます。

ユーザーがマップをクリックすると、Leaflet ライブラリはクリックの地理空間座標を計算します。これらの座標をバックエンドに送信し、クリックしたポイントと交差するジオメトリについてデータベースを検索します。これらのジオメトリの中に建物がある場合、それらを返します。

建物はバックエンドから `GeoJSON` 形式で返され、編集用の別のレイヤーとしてマップに追加されます。これがクリックの処理方法です。
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

編集可能なジオメトリ用の永続レイヤーグループ `featuresLayer` をマップに追加しました。すでにロードされているジオメトリをクリックしたかどうかを確認し、そうでない場合はバックエンドにリクエストを送信して建物を表すポリゴンをロードします。ロードされたフィーチャーレイヤーは featuresLayer に追加され、編集モードがアクティブになります。

機能のロードと `GeoJSON` からの変換を行う関数の例を以下に示します。
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

編集セッション後、ユーザーはカスタムの `Save` ボタンをクリックします。

![Save](save-btn.png)

ページを更新して変更を確認します。

![Changes](changes.png)

残念ながら、以前にロードされたタイルがキャッシュされているため、`tiles.redraw()` 関数は正しく機能しません。マップを `Ctrl + F5` で強制的に更新する必要があります。

保存ボタンを押すハンドラーを以下に示します。
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

## バックエンド

新しいコントローラー `FeaturesController` を追加し、送信された座標に応じてハウス/フィーチャーを抽出するハンドラーを作成します。

SQL リクエストは次のようになります。

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

座標は、クライアントリクエストの座標系 (WGS 84) を示すポイントに変換され、次にデータベースデータが提示されているシステム (Web Mercator) に翻訳されます。建物としてマークされたジオメトリとの交差を検索します。

リクエストの実行とクライアントへのデータの送信は、以前の記事で説明した方法と同様に行われます。
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
わずかな違いがあります。InMemory レイヤーを GeoJSON としてメモリに保存し、それを文字列に変換してクライアントに送信します。

次に、Aspose.GIS の更新の本質である変更内容をデータベースに保存することに移ります。`Edit()` メソッドがこれを処理します。リクエストボディ全体を完全にメモリにロードし、ストリームとして読み取ります。
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync(); 
Request.Body.Position = 0;
```
次に、編集されたフィーチャーを GeoJSON 形式で読み取ります。
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```

次のステップでは、送信されたフィーチャーセットから、データベース内の対応するフィーチャーを表す一意の識別子を抽出します。特別な編集レイヤーを作成するためのクエリを構築し、対応するデータソースを構築します。
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

`AsTrackableForChanges` メソッドの設定に注意してください。これは、変更を追跡できる特別なメソッドです。最初のパラメーターは、変更リクエストを送信する必要があるテーブルを指定します。2 番目のパラメーターは、データベースの変更を行うための識別子と見なされる属性を示します。最も興味深い部分は 3 番目のパラメーターです。True に設定すると、レイヤーは 2 番目のパラメーターに従って重複を追跡し、「上書き」により以前にロードされたフィーチャーを新しいものに変更します。ただし、編集結果の場合、つまり同じ識別子を持つ新しいフィーチャーを追加する場合、古い値と比較して変更が検出される `UPDATE` コマンドが生成されます。3 番目のパラメーターが false に設定されている場合、初期化中または編集中に重複が発生すると例外がスローされます。

属性名は、編集可能なテーブルのフィールド名として使用されます。変更検出に関して重要な点を注意する必要があります。追加または変更されたタイプを正確に反映するように、レイヤーに保存される属性の正確なデータ型を指定することが不可欠です。たとえば、`osm_id` のタイプが `Int32` である新しいフィーチャーを追加し、レイヤーで指定された属性タイプが `Int64` の場合、これは 2 つの異なる値として扱われます。`Int64.Equals(Int32)` のようなオーバーロードはありません。将来のバージョンでは、この動作を見直し、可能であれば修正します。3 番目のパラメータータイプは、データベーステーブルのターゲットデータ型として保存時に適用されます。

次に、データベースに接続し、テーブルからデータを読み取ります。
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```

トランザクションがデータベースレベルで正しく機能するためには、現在のトランザクションを 2 番目のパラメーターとして `ReadAsync` 操作に渡すことが重要です。

次に、変更をデータベースに送信する前に一連の変換を実行する必要があります。
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
Leaflet は WGS 84 座標系でジオメトリを生成しますが、データベーススキーマは Web Mercator での保存が必要です。Web Mercator システムに変換するには、特別な `transformer` オブジェクトを作成し、それを使用して変換します。

さらに、leaflet はジオメトリ座標の 3 番目のパラメーター Z を値 0 で埋めます。ただし、このパラメーターはデータベーススキーマで考慮されていないため、`HasZ` の値を false に設定してその存在を削除します。

最後のポイントは、既存のフィーチャーを同じ osm_id を持つクライアントから受信したもので置き換えることです。この操作により、古いインスタンスに対する変更が検出されます。`SubmitChangesAsync` を呼び出すと、変更検出プロセスが発生し、INSERT、DELETE、および UPDATE コマンドが変更に応じてデータベースに送信されます。

最後までお読みいただきありがとうございます。すべてのコードは次のリポジトリで入手できます。[Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)