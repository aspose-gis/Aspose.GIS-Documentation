---
title: "Haritaya Geometri Çizme"
type: docs
url: /tr/net/how-to-draw-geometry
weight: 70
---

Bir haritada geometrik nesneler oluşturmak ve görüntülemek için öncelikle bir **geometri nesnesi oluşturmanız** gerekir. Kullanabileceğiniz iki yöntem vardır:

- **Her Geometri Özellik Türü İçin Yapıcı**
Bu yöntem, her geometri özellik türü için özel bir yapıcı kullanmayı içerir. Örneğin, bir nokta oluşturmak için aşağıdaki kodu kullanırsınız:

```
Point point = new Point(40.7128, -74.006);
```

Ancak bu yöntem, karmaşık nesneler gibi çoklu hatlar veya koleksiyonlar oluştururken yönetilmesi zor ve zahmetli hale gelebilir. Sonuç olarak, geliştiricinin birçok kod satırı eklemesi gerekebilir ve bu da kodun okunabilirliğini düşürebilir. Başlangıçta veri bütünlüğünü sağlamak da zor olabilir. Örneğin, içinde bir deliği olan bir çokgen oluşturan aşağıdaki örneği düşünün:

```
Polygon polygon = new Polygon();

LinearRing ring = new LinearRing();
ring.AddPoint(50.02, 36.22);
ring.AddPoint(49.99, 36.26);
ring.AddPoint(49.97, 36.23);
ring.AddPoint(49.98, 36.17);
ring.AddPoint(50.02, 36.22);

LinearRing hole = new LinearRing();
hole.AddPoint(50.00, 36.22);
hole.AddPoint(49.99, 36.20);
hole.AddPoint(49.98, 36.23);
hole.AddPoint(50.00, 36.24);
hole.AddPoint(50.00, 36.22);

polygon.ExteriorRing = ring;
polygon.AddInteriorRing(hole);
```

Bu yaklaşımın bir başka dezavantajı da başlatma verilerinin tekdüzelik eksikliğidir. Projeniz içinde sabitlerin veya dosyaların bir deposunu oluşturamazsınız.

- **WKT (Well-Known Text)**
Bu yöntem, geometriyi WKT'den (Well-Known Text) üretmeyi içerir ve bu, geometri oluşturmanın standartlaştırılmış bir yolunu sunar. Aşağıdaki kod, bir nokta ve bir çizgi nasıl oluşturulacağını gösterir:

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

Bu yaklaşım dizeyi ayrıştırma ihtiyacı nedeniyle performansı biraz düşürebilirken, daha karmaşık nesnelerin oluşturulmasını basitleştirir.

WKT hakkında daha fazla ayrıntı için aşağıdaki makaleyi inceleyebilirsiniz: "Verileri WKT ve WKB'den/WKT ve WKB'ye Dışa Aktarma ve İçe Aktarma."

Haritaya Geometrik Nesneleri Görüntüleme
Bir geometrik nesne oluşturduktan sonraki adım, onu haritada görüntülemektir. Harita çeşitli kaynaklardan ve formatlardan yüklenen katmanları görüntüleyebilirken, InMemoryLayer bir kaynağa ihtiyaç duymayan bir katmandır.

**Geometrik nesnenizi görüntülemek** için bir InMemoryLayer oluşturabilir ve nesneyi ona ekleyebilirsiniz:

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

Şimdi bu **katmanı haritada görüntüleyebilir ve aşağıdaki kodla SVG gibi desteklenen formatlardan birinde bir dosya oluşturabilirsiniz**:

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

Katmanı ekledikten ve haritada görüntüledikten sonra, onu desteklenen formatlardan herhangi birinde kaydedebilirsiniz. Bu örnekte, potansiyel Bitmap desteği sorunlarından kaçınmak için SVG formatı seçilir. Net 6.0'ın sınırlı Bitmap desteğine sahip olduğunu ve bunun istemci tarafında Blazor WebAsm kullanılarak Bitmap görüntülerinin oluşturulamaması gibi kısıtlamalara neden olabileceğini belirtmek önemlidir. Bu nedenle, haritanızı kaydetmek için bir format seçerken hedef platformun sınırlamalarını göz önünde bulundurmak ve onunla uyumlu bir format seçmek önemlidir.

Makale, varsayılan, düz stil ile bir haritaya geometrik nesnelerin nasıl oluşturulacağı ve görüntüleneceği konusunda açıklama yapar. Ancak Aspose kitaplığı ihtiyaçlarınıza göre özelleştirilebilen geniş bir stil seçeneği yelpazesi sunar. Bu seçenekleri keşfetmek için [Aspose.MapRendering belgelerine]( https://docs.aspose.com/gis/net/map-rendering/) göz atmanızı öneririz ve bu, farklı stil tekniklerini kullanarak haritanızın görsel çekiciliğini nasıl artırabileceğiniz hakkında ayrıntılı bilgi sağlar.

**Özetle**, bir haritaya geometrik nesneler oluşturmak için her geometri özellik türü için bir yapıcı kullanabilir veya WKT'den geometri üretebilirsiniz. Nesneyi görüntülemek için onu bir katmana yerleştirin ve katmanı varsayılan harita stiliyle haritada görüntüleyin. Haritayı SVG gibi desteklenen bir formatta kaydedin ve stil seçeneklerini keşfetmek için kitaplığımızı kullanın. Ayrıca, kitaplığımız belgelerde sağlanan [bağlantıya]( https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer) tıklayarak bitmiş bir örneği görebilirsiniz ve bu da bu teknikleri kendi projelerinizde nasıl uygulayacağınızı anlamanıza yardımcı olabilir.
