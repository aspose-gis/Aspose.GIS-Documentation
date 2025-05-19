---
title: "Pembaruan Aspose.GIS: Mengedit Fitur dan Geometri serta menyimpan perubahan ke database."
type: docs
url: /id/net/showcases/saving-changes-to-database/
description: "Artikel ini membahas peningkatan terbaru di pustaka Aspose.GIS, dengan fokus pada kemampuan baru untuk mendeteksi dan menyimpan perubahan geometri dalam aplikasi pemetaan."
weight: 80
---
# Pembaruan Aspose.GIS: Mengedit Fitur dan Geometri serta menyimpan perubahan ke database.

## Pendahuluan

Mengingat perubahan terbaru di pustaka [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis), penting untuk menyoroti beberapa di antaranya agar tidak luput dari perhatian. Dalam artikel ini, kita akan membahas kemampuan baru untuk mendeteksi dan menyimpan perubahan pada geometri dan fitur dalam database.

Sebagai contoh demonstrasi, kita akan melanjutkan pengerjaan aplikasi yang dijelaskan dalam artikel ["Draw a map. A sliding map with tiles"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) dan sedikit memperluasnya dengan menambahkan fungsionalitas pengeditan objek pada peta. Dataset tetap sama seperti di artikel sebelumnya.

## Front-end

Untuk demonstrasi kemampuan modifikasi geometri, kami memilih ekstensi open-source populer untuk [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/).

Kami menambahkan pustaka ini melalui file libman.json:
![Libman](libman.png)

Selanjutnya, kita hubungkan gaya dan skrip ke halaman:
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

Untuk tujuan demonstrasi, kita akan membatasi kemampuan pengeditan hanya untuk bangunan saja. Pengguna mengklik tombol mouse kiri pada peta, dan jika ada bangunan di lokasi tersebut, bangunan itu disorot dan tersedia untuk diedit. Ini dicapai dengan melapisi lapisan tambahan di atas ubin.

Ketika pengguna mengeklik peta, pustaka Leaflet menghitung koordinat spasial dari klik tersebut. Kami mengirim koordinat ini ke back-end dan mencari database untuk geometri yang berpotongan dengan titik yang diklik. Jika ada bangunan di antara geometri ini, kami mengembalikannya.

Bangunan dikembalikan dari back-end dalam format `GeoJSON` dan ditambahkan ke peta sebagai lapisan terpisah untuk pengeditan. Begini cara kita menangani klik:
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
                    console.log('Fitur ditambahkan.');
                } else {
                    console.log('Tidak ada fitur untuk ditambahkan.');
                }
            });
    }

    featureFound = false;
});
```

Kita memiliki grup lapisan persisten untuk geometri yang dapat diedit, `featuresLayer`, yang telah ditambahkan ke peta. Kita memeriksa apakah klik dilakukan pada geometri yang sudah dimuat, dan jika tidak, kita membuat permintaan ke back-end untuk memuat poligon yang mewakili bangunan. Lapisan fitur yang dimuat ditambahkan ke featuresLayer, dan mode pengeditan diaktifkan.

Berikut adalah fungsi untuk memuat fitur dan mengonversi dari `GeoJSON`:
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

Setelah sesi pengeditan, pengguna mengeklik tombol `Save` khusus:

![Save](save-btn.png)

Segarkan halaman dan lihat perubahannya:

![Changes](changes.png)

Sayangnya, fungsi `tiles.redraw()` tidak berfungsi dengan benar karena ubin yang dimuat sebelumnya di-cache, sehingga memerlukan penyegaran peta secara paksa melalui `Ctrl + F5`.

Berikut adalah penanganan untuk menekan tombol simpan:
```javascript
function saveResult() {
    if (featuresLayer.getLayers().length === 0) {
        console.log('Tidak ada lapisan yang akan dikirim ke server.');
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
            console.log('Data berhasil dikirim ke server.');
        })
        .catch(error => {
            console.error('Error saat mengirim GeoJSON:', error);
        });
}
```

## Back-end

Di sini kita menambahkan pengontrol baru, `FeaturesController`, di mana kita membuat penangan untuk mengekstrak rumah/fitur sesuai dengan koordinat yang dikirim.

Permintaan SQL terlihat seperti ini:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

Koordinat diubah menjadi titik, yang menunjukkan sistem koordinat permintaan klien asli (WGS 84), dan kemudian diterjemahkan ke dalam sistem tempat data database disajikan (Web Mercator). Kita mencari perpotongan dengan titik ini untuk geometri yang ditandai sebagai bangunan.

Eksekusi permintaan dan pengiriman data ke klien terjadi mirip dengan apa yang kita diskusikan di artikel sebelumnya:
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
Dengan sedikit perbedaan: kita menyimpan lapisan InMemory kita sebagai GeoJSON dalam memori sebagai stream, lalu mengubahnya menjadi string dan mengirimkannya ke klien.

Sekarang kita sampai pada inti pembaruan di Aspose.GIS — menyimpan perubahan ke database. Metode `Edit()` menangani ini. Kita membaca isi permintaan untuk memuatnya sepenuhnya ke dalam memori dan membacanya sebagai stream:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// hanya buffer body.
await reader.ReadToEndAsync(); 
Request.Body.Position = 0;
```
Selanjutnya, kita membaca fitur yang diedit dalam format GeoJSON:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
Langkah berikutnya, dari set fitur yang dikirim, kita mengekstrak atribut yang mewakili pengidentifikasi unik dari fitur terkait dalam database. Kita membentuk permintaan untuk mengisi lapisan khusus untuk pengeditan dan membangun sumber data yang sesuai:
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
Perhatikan metode konfigurasi `AsTrackableForChanges`. Ini adalah metode khusus yang menunjukkan kebutuhan untuk membuat sumber data khusus yang mampu melacak perubahan. Parameter pertama menentukan tabel tempat permintaan perubahan harus dikirim. Yang kedua menunjukkan atribut mana yang akan dianggap sebagai pengidentifikasi untuk melakukan perubahan pada database. Bagian paling menarik adalah parameter ketiga. Ketika diatur ke True, ini menunjukkan bahwa lapisan akan melacak munculnya duplikat sesuai dengan parameter kedua dan "menimpa" fitur yang dimuat sebelumnya dengan yang baru. Namun, dalam kasus hasil pengeditan, yaitu menambahkan fitur baru dengan pengidentifikasi yang sama, perintah `UPDATE` akan dihasilkan sesuai dengan perubahan dibandingkan dengan nilai lama. Jika duplikat muncul selama inisialisasi lapisan dari database, lapisan akan diam-diam menimpanya dengan nilai terakhir. Jika parameter ketiga diatur ke false, pengecualian akan dilemparkan saat duplikat muncul, baik selama inisialisasi atau pengeditan.

Nama atribut akan digunakan sebagai nama bidang dalam tabel yang dapat diedit. Penting untuk dicatat poin penting mengenai deteksi perubahan. Sangat penting untuk menentukan jenis data yang tepat dari atribut yang akan disimpan di lapisan untuk melacak perubahan, itu harus akurat terkait dengan jenis yang baru ditambahkan atau dimodifikasi. Misalnya, jika kita menambahkan fitur baru dengan `osm_id` bertipe `Int32`, sementara tipe atribut yang ditentukan dalam lapisan adalah `Int64`, ini akan diperlakukan sebagai dua nilai berbeda karena tidak ada kelebihan metode `Equal`s yang terlihat seperti `Int64.Equals(Int32)`. Dalam versi mendatang, perilaku ini akan ditinjau dan diperbaiki jika memungkinkan. Tipe parameter ketiga akan diterapkan selama penyimpanan data sebagai tipe data target dari tabel database.

Selanjutnya, kita terhubung ke database dan membaca data dari tabel:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
Poin penting adalah bahwa agar transaksi berfungsi dengan benar di tingkat database, perlu untuk meneruskan transaksi saat ini sebagai parameter kedua selama operasi baca.

Selanjutnya, kita perlu melakukan serangkaian transformasi sebelum mengirim perubahan ke database:
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
Leaflet menghasilkan geometri dalam sistem koordinat WGS 84, namun skema database memerlukan penyimpanan di Web Mercator. Untuk mengubah ke sistem Web Mercator, kita membuat objek `transformer` khusus dan menggunakannya untuk konversi.

Selain itu, leaflet mengisi parameter ketiga dari koordinat geometri Z dengan nilai 0. Namun, parameter ini tidak diperhitungkan dalam skema database kita, jadi kita menghapus kehadirannya dengan mengatur nilai `HasZ` menjadi false.

Poin terakhir adalah menerapkan perubahan dengan mengganti fitur yang ada dengan yang diterima dari klien yang memiliki osm_id yang sama. Operasi ini akan menyebabkan deteksi perubahan relatif terhadap instance fitur yang lebih lama. Pada saat memanggil `SubmitChangesAsync`, proses deteksi perubahan akan terjadi, dan perintah INSERT, DELETE, dan UPDATE akan dikirim ke database sesuai dengan perubahan Anda.

Terima kasih telah membaca sampai akhir. Seluruh kode akan tersedia di repositori berikut: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)
---