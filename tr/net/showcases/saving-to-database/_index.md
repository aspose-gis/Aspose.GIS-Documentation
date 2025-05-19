---
title: "Aspose.GIS Güncellemeleri: Özellikleri ve Geometrileri Düzenleme ve Değişiklikleri Veritabanına Kaydetme."
type: docs
url: /tr/net/showcases/saving-changes-to-database/
description: "Bu makale, Aspose.GIS kitaplığındaki son geliştirmeleri ele almaktadır ve haritalama uygulamasında geometri ve özelliklerdeki değişiklikleri algılama ve kaydetme yeteneklerine odaklanmaktadır."
weight: 80
---
# Aspose.GIS Güncellemeleri: Özellikleri ve Geometrileri Düzenleme ve Değişiklikleri Veritabanına Kaydetme.

## Giriş

[Aspose.GIS](https://www.nuget.org/packages/Aspose.gis) kitaplığındaki son değişiklikler gözden kaçmamak için vurgulanması önemlidir. Bu makalede, veritabanındaki geometri ve özelliklerdeki değişiklikleri algılama ve kaydetme yeteneği yeni yeteneğini tartışacağız.

Bir gösteri örneği olarak, ["Harita Çizin. Kaydırılabilir Harita Karolarla"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) makalesinde açıklanan uygulamayı kullanmaya devam edeceğiz ve haritadaki nesne düzenleme işlevselliği ekleyerek onu biraz genişleteceğiz. Veri kümesi önceki makaledekiyle aynı kalır.

## Ön Uç

Geometri değiştirme yeteneklerinin gösterimi için, [leaflet](https://leafletjs.com/) için popüler bir açık kaynaklı uzantı olan [leaflet-geoman](https://geoman.io/) seçtik.

Bu kitaplığı libman.json dosyası aracılığıyla ekliyoruz:
![Libman](libman.png)

Ardından, stilleri ve komut dosyalarını sayfaya bağlarız:
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

Görselleştirme amacıyla, düzenleme yeteneklerini yalnızca binalarla sınırlayacağız. Kullanıcı haritanın sol fare düğmesine tıklar ve o konumda bir bina varsa, vurgulanır ve düzenlenebilir hale gelir. Bu, karoların üzerine ek bir katman bindirilerek elde edilir.

Kullanıcı haritaya tıkladığında, Leaflet kitaplığı tıklamanın coğrafi koordinatlarını hesaplar. Bu koordinatları arka uca göndeririz ve tıklanan noktayla kesişen geometrileri veritabanında ararız. Bu geometriler arasında binalar varsa, bunları döndürürüz.

Binalar, arka uçtan `GeoJSON` formatında döndürülür ve düzenleme için ayrı bir katman olarak haritaya eklenir. İşte tıklamayı nasıl işlediğimiz:
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
                    console.log('Özellik eklendi.');
                } else {
                    console.log('Eklenecek özellik yok.');
                }
            });
    }

    featureFound = false;
});
```

Düzenlenebilir geometriler için kalıcı bir katman grubumuz, `featuresLayer` haritaya eklenmiştir. Tıklamanın zaten yüklenmiş bir geometri üzerinde yapılıp yapılmadığını kontrol ediyoruz ve değilse, binaları temsil eden çokgenleri yüklemek için arka uca bir istek gönderiyoruz. Yüklenen özellik katmanları featuresLayer'a eklenir ve düzenleme modu etkinleştirilir.

İşte özellikleri yükleme ve `GeoJSON`'dan dönüştürme işlevi:
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
        .catch(error => console.error('Özellik yüklenirken hata:', error));
}
```

Düzenleme oturumu tamamlandıktan sonra, kullanıcı özel bir `Kaydet` düğmesine tıklar:

![Kaydet](save-btn.png)

Sayfayı yenileyin ve değişiklikleri görün:

![Değişiklikler](changes.png)

Ne yazık ki, önceden yüklenen karoların önbelleğe alınması nedeniyle `tiles.redraw()` işlevi düzgün çalışmıyor ve haritanın `Ctrl + F5` ile zorla yenilenmesini gerektiriyor.

İşte kaydet düğmesine basma işlemcisini:
```javascript
function saveResult() {
    if (featuresLayer.getLayers().length === 0) {
        console.log('Sunucuya gönderilecek katman yok.');
        return;
    }
    sendGeoJSONToServer()
        .then(() => {
            console.log('haritayı temizle ve güncelle');
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
            console.log('Veriler başarıyla sunucuya gönderildi.');
        })
        .catch(error => {
            console.error('GeoJSON gönderilirken hata:', error);
        });
}
```

## Arka Uç

Burada yeni bir denetleyici, `FeaturesController` ekliyoruz ve gönderilen koordinatlara göre evleri/özellikleri çıkarmak için bir işleyici oluşturuyoruz.

SQL isteği şu şekilde görünmektedir:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

Koordinatlar bir noktaya dönüştürülür ve istemcinin orijinal isteğinin koordinat sistemini (WGS 84) belirtir, ardından veritabanı verilerinin sunulduğu sisteme (Web Mercator) çevrilir. Binalar olarak işaretlenmiş geometrilerle bu nokta ile kesişimleri arıyoruz.

İsteğin yürütülmesi ve verilerin istemciye gönderilmesi daha önceki makalede tartıştıklarımıza benzer şekilde gerçekleşir:
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
Küçük bir farkla: InMemory katmanımızı GeoJSON olarak bellekte bir akışa kaydediyoruz, ardından onu bir dizeye dönüştürüyoruz ve istemciye gönderiyoruz.

Şimdi Aspose.GIS'deki güncellemelerin özüne geliyoruz — değişiklikleri veritabanına kaydetme. `Edit()` yöntemi bunu işler. İstek gövdesini tamamen belleğe yüklemek için okuyarak başlıyoruz ve onu bir akış olarak okuyoruz:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// sadece gövdeyi tamponla.
await reader.ReadToEndAsync();
Request.Body.Position = 0;
```
Ardından, GeoJSON formatındaki düzenlenmiş özellikleri okuyoruz:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
Bir sonraki adım, gönderilen özellik kümesinden veritabanındaki karşılık gelen özellikleri temsil eden benzersiz tanımlayıcıları çıkarmaktır. Düzenleme için özel bir katman oluşturmak ve ilgili veri kaynağını oluşturmak için bir istek oluşturuyoruz:
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
`AsTrackableForChanges` yöntemini yapılandırmak dikkat çekici bir noktadır. Bu, değişiklikleri izlemek için özel bir veri kaynağı oluşturulması gerektiğini gösteren özel bir yöntemdir. İlk parametre, değişiklik isteklerinin gönderileceği tabloyu belirtir. İkinci, veritabanındaki değişiklikler için tanımlayıcı olarak kabul edilecek niteliği belirtir. En ilginç kısım ise üçüncü parametredir. True olarak ayarlandığında, katmanın ikinci parametreye göre çoğaltmaları izleyeceğini ve yeni olanlarla eski özellikleri "üzerine yazacağını" gösterir. Ancak, düzenleme sonuçları durumunda, yani aynı tanımlayıcıya sahip yeni bir özellik eklenmesi durumunda, eski değere kıyasla değişikliklere göre bir `UPDATE` komutu oluşturulacaktır. Başlangıç sırasında çoğaltmalar görünürse, katman sessizce son değerle üzerine yazacaktır. Üçüncü parametre false olarak ayarlandığında, başlatma veya düzenleme sırasında ortaya çıkan çoğaltmalardan bağımsız olarak bir istisna atılacaktır.

Nitelik adları, düzenlenebilir tabloda alan adları olarak kullanılacaktır. Değişiklik algılamasıyla ilgili önemli bir nokta belirtmek önemlidir. Depolama için yeni eklenen veya değiştirilen türler konusunda doğru olan tam veri türünü belirtmek çok önemlidir. Örneğin, `osm_id`'nin `Int32` tipiyle bir özellik ekliyorsak, katmanda belirtilen nitelik tipi `Int64` ise, bu iki farklı değer olarak kabul edilecektir çünkü `Int64.Equals(Int32)` gibi bir eşit yöntemi araması yoktur. Gelecek sürümlerde bu davranış gözden geçirilecek ve mümkünse düzeltilecektir. Üçüncü parametre türü, veritabanı tablosunun hedef veri türü olarak kaydedilirken uygulanacaktır.

Ardından, veritabanına bağlanırız ve tablodan veri okuruz:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
İşlemin veritabanı düzeyinde doğru çalışması için geçerli işlemi ikinci parametre olarak okuma işlemine geçirmek önemlidir.

Sonraki adım, değişiklikleri veritabanına göndermeden önce bir dizi dönüşüm gerçekleştirmektir:
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
Leaflet geometrileri WGS 84 koordinat sisteminde oluşturur, ancak veritabanı şeması Web Mercator'da depolanmasını gerektirir. Web Mercator sistemine dönüştürmek için özel bir `transformer` nesnesi oluşturuyoruz ve onu dönüşüm için kullanıyoruz.

Ek olarak, leaflet geometri koordinatlarının üçüncü parametresi Z'yi 0 değeriyle doldurur. Ancak bu parametre veritabanı şemamızda hesaba katılmıyor, bu nedenle varlığını `HasZ` değerini false olarak ayarlayarak kaldırıyoruz.

Son nokta, istemciden alınan düzenlenmiş özelliği aynı osm_id'ye sahip mevcut özellik yerine koyarak değişiklikleri uygulamaktır. Bu işlem eski örneklere göre değişikliklerin algılanmasına yol açacaktır. `SubmitChangesAsync` çağrısı anında, değişiklik algılama işlemi gerçekleşecek ve INSERT, DELETE ve UPDATE komutları veritabanına gönderilecektir.

Okuduğunuz için teşekkür ederim. Tüm kod aşağıdaki depoda bulunabilir: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)
---