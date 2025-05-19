---
title: "Harita Çizin. Fayanslarla kayan bir harita."
type: docs
url: /tr/net/showcases/sliding-map-with-tiles/
description: "Fayansları çizmek ve bunlardan kayan bir harita oluşturmak nasıl yapılır."
weight: 80
aliases:
 - /tr/net/showcases/tiles/
---
# Harita Çizin. Fayanslarla kayan bir harita.
Bu makalede, [Aspose.GIS](https://www.nuget.org/packages/Aspose.GIS/) kütüphanesi ve kamuya açık veriler kullanarak gerçek zamanlı olarak oluşturulacak kayan bir haritanın nasıl oluşturulacağını göstermek istiyoruz. Yeni kütüphane özelliği sayesinde artık GIS verilerini SQL sorgusu aracılığıyla veritabanından sorgulayabiliriz. Sonuç olarak elde etmemiz gereken şudur:

![Sonuç](result.png)

Depo kaynak kodu [burada](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest).

## Veri hazırlığı.

Öncelikle, veritabanına yükleyebileceğimiz coğrafi bilgilere ihtiyacımız olacak. Bu tür bilgilerin popüler kaynaklarından biri `OpenStreetMap`'tir, bu yüzden onu kullanalım. Bence en uygun yol, https://download.geofabrik.de/ adresinden pbf formatında veri çıkarmaktır. Örneğin, [Macaristan](https://download.geofabrik.de/europe/hungary-latest.osm.pbf) indirelim.

Bir sonraki aşamada, çalışan bir `PostGIS` örneğine ihtiyacımız var. Elbette yerel olarak yüklenmiş bir `PostgreSQL` sürümünü kullanabilirsiniz, ancak Docker kapsayıcılarını kullanmanın çok uygun olduğunu düşünüyorum. Docker compose dosyası kullanarak PostGIS'i kuralım:

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

`d:\local_folder:/usr/share/gisdata` birimi, GIS verilerini yerel makineden yüklemek için gereklidir.

Şimdi kapsayıcımızı çalıştıralım:

```bash
docker compose up
```

Veritabanı örneğine `pgAdmin` kullanarak bağlanın ve orada Macaristan veritabanını oluşturun:

![DB Oluştur](create_db.png)

veya SQL komutu aracılığıyla:

```sql
CREATE DATABASE Hungary;
```

Bu veritabanına gerekli uzantıları ekleyin:

![Uzantılar](add_extention.png)

Bunlar `postgis` ve `hstore` uzantıları olacaktır. hstore, anahtar-değer veri tipini kullanmanıza olanak tanıyan bir uzantıdır. OpenStreetMap yaygın olarak bu türü, ana kategorilere düşmeyen özelliklerin tanımlanması için kullanır ve bu nedenle bunlar için ayrı alanlar oluşturulmaz, ancak etiketler alanında saklanır.

SQL benzeri komutların da vardır:

```sql
CREATE EXTENSION IF NOT EXISTS hstore;
CREATE EXTENSION IF NOT EXISTS postgis;
```

Şimdi kabağa bağlanalım, benim durumumda `local_folder-postgis-1`:

```bash
docker exec -it local_folder-postgis-1 sh
```

Ve verileri `pbf` dosyasından veritabanına aktaracak programı yükleyelim:

```bash
apt-get update && apt-get install -y osm2pgsql
```

`hungary-latest.osm.pbf` dosyasının yerel klasörünüzde olduğundan emin olun ve ardından içe aktarma komutunu çalıştırın:

```bash
osm2pgsql --create --database=Hungary --user=gis --password --host=localhost --port=5432 --hstore /usr/share/gisdata/hungary-latest.osm.pbf
```

Macaristan durumunda, bu komutu tamamlamak bir buçuk dakika sürdü. `--create` seçeneği yeni bir veritabanının basit oluşturma modunu ifade eder. Bu arada, her şeyden önce `--append` modu da vardır ve bu, veriler değişmişse güncellenmelerine olanak tanır:

```bash
osm2pgsql --append --slim OSMFILE
```

`--hstore` seçeneği uygulamasına ek olarak özelliklerin ve geometrilerin ek bilgilerini depolamak için `tags` tipinde bir alan oluşturmasını söyler.

## Arka Uç

Yani verilerimiz kullanıma hazır. Harita oluşturma yolundaki bir sonraki adım, arka ucunu oluşturmaktır. Arka ucumuzun amacı, genellikle `256*256` boyutunda olan özel `fayanslar` üretmek ve bunların tarayıcıda mozaik gibi bir haritaya monte edilmesidir. Her fayans benzersiz bir şekilde Z'nin haritanın yakınlaştırma/uzaklaştırma derecesi, X'in fayans dizisindeki satır ve Y'nin sütun kombinasyonuyla tanımlanır. Fayansların doğası hakkında daha fazla bilgiyi [burada](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames) okuyabilirsiniz.

Arka ucumuz buna göre ASP.NET Core üzerinde olacak, bu yüzden projeyi oluşturmaya başlayalım. Yani `Visual Studio`'da önceden yüklenmiş `ASP.NET Core MVC` şablonuna dayalı bir proje oluşturalım.

Ardından, fayansları üretecek projeye `Aspose.GIS` NuGet paketini yükleyin:

```cmd
dotnet add package Aspose.GIS --version 24.6.0
```

Projeyi gereksiz dosyalardan temizleyin. Böylece yapı aşağıdaki gibi görünür:

![Çözüm Gezgini](project.png)

Ardından wwwroot/lib klasörünün içeriğini silin, çünkü bağımlılıklarımızı `libman` aracılığıyla kuracağız. İşte `libman.json` dosyasının yapısı:
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


Bağımlılıkları `_Layout.cshtml` dosyasına ekleyin:

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

Ve ayrıca `Index.cshtml`'yi düzenleyin:

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

Bu durumda, `bootstrap-reboot.min.css` varsayılan stil ayarlarını sıfırlar ve `leaflet.min.js`, fayanslardan haritayı bir araya getirerek haritanın oluşturulmasından sorumludur. Harita bloğunun yüksekliğini görünür alanın tam yüksekliğine ayarlayalım `map.css` dosyasında:

```css
#map {
    min-height: 100vh;
}
```

`map.js` dosyasının içeriği de oldukça basit, ancak biraz daha ilginç:

```javascript
var map = L.map('map').setView([47.59995, 19.36623], 13);
const tiles = L.tileLayer('/tiles/{z}/{x}/{y}.png', {
    maxZoom: 19,
    minZoom: 11
}).addTo(map);
```

Burada harita bloğunun kimliğini `'map'` olarak belirtiyoruz, ardından `setView` yönteminde başlangıç harita yüklemesinin başlayacağı yerin koordinatlarını ve ayrıca örneğin 13 ölçeğini ayarlıyoruz. Dikkat edin `tileLayer` yöntemi, sunucuya fayans isteği için bir desen dizesi kabul eder. Bu adres ya üçüncü taraf fayans sunucularına erişmek için mutlak ya da bizim durumumuzda göreli olabilir. `/tiles/{z}/{x}/{y}.png` rotası henüz bizim tarafından uygulanmadı ve bu anlatımızın en önemli parçasıdır ki henüz uygulamamız gerekiyor.

Fayans oluşturma isteği işleyicisini uygulamak için öncelikle `Program.cs` dosyasında ayrı bir rota tanımlayalım:

```csharp
app.MapControllerRoute(name: "tiles",
  pattern: "tiles/{z}/{x}/{y}.png",
  defaults: new { controller = "Tiles", action = "Index" });

app.MapControllerRoute(
  name: "default",
  pattern: "{controller=Home}/{action=Index}/{id?}");
```

Burada iki rota tanımlanır, ilki fayanslar için ve ikincisi standart olandır. `MapControllerRoute` durumunda sıra önemlidir, bu nedenle beklenmedik davranışlardan kaçınmak için fayans rotasını standart rottan önce yerleştirmek değerdir.

Ardından arka ucunu oluşturalım. İşte örnek bir kod:

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

Umarız temel fikirleri ve harita oluşturma tekniklerini size aktarabildik. Deneylerinizde bol şans diliyoruz.