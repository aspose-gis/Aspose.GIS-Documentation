---
title: "Katman Üretici Konsol Uygulaması"
type: docs
url: /tr/net/layer-generator-console
weight: 50
---

## Özet

Bu konsol uygulaması, çeşitli türlerde geometrik nesneler oluşturmak ve bunları seçilen formatta kaydetmek için tasarlanmıştır. Noktalar, çokgenler ve polilinler oluşturmanıza, üretilecek nesne sayısını belirtmenize ve çıktı formatını seçmenize olanak tanır.

## Kullanım

Komut sözdizimi:

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

Argümanlar:

```
-t, --type: Geometri türü. Aşağıdakilerden biri: Point, Polygon, Polyline.

-c, --count: Gerekli. Üretilecek nesne sayısı. Örneğin: 15.

-f, --fileName: Gerekli. Kaydetmek için dosya adı. Dosya adını ve uzantısını belirtin. Örneğin: test.json.

-o, --outputFormat: Çıktı formatı. Desteklenen dosya formatlarını burada inceleyin.

--help: Komut için yardım bilgilerini görüntüleyin.

--version: Uygulama sürüm bilgilerini görüntüleyin.
```

"test.json" formatında 15 rastgele nokta oluşturmak ve kaydetmek için bir örnek komut:

```
app.exe -t Point -c 15 -f test.json -o json
```

## Kurulum ve Lisanslama

Uygulamayı kullanmak istiyorsanız, arşivi indirmeniz ve çıkarmanız gerekir. Lütfen aşağıdaki bağlantıyı takip edin.

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

Aspose.GIS Katman Üretici Konsol Uygulaması ücretsiz olsa da, Aspose.GIS .NET normal şekilde lisanslanmıştır, bu nedenle uygulamanız aracılığıyla lisansınızı yeniden kullanabilir veya uygulamayı deneme modunda Aspose.GIS .NET kullanarak değerlendirebilir veya Geçici Lisans talep edebilirsiniz.

## Sonuç

Geometrik Nesne Üreticisi, çeşitli türlerde geometri örnekleri oluşturmanıza ve bunları istediğiniz formatta kaydetmenize yardımcı olan kullanışlı bir konsol uygulamasıdır. Coğrafi verilerle çalışmak ve coğrafi bilgi sistemleri geliştirmek için faydalı bir araçtır.
