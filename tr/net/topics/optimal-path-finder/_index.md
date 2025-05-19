---
title: "Optimal Yol Bulucu"
type: docs
url: /tr/net/optimal-path-finder
weight: 70
---

## Özet

Bir yol ağında en kısa yolu bulmak, harita üzerindeki noktalar arasında seyahat etmenin en verimli yolunu belirlemeyi amaçlayan bir analiz sürecidir. Bu araç, birden fazla duraklı optimal rotalar oluşturmak veya farklı konumlar arasındaki mesafeyi ve seyahat süresini ölçmek için faydalı olabilir. Her çağrı ile teknolojimiz tek veya çoklu araçlar için optimal rotaları bulabilir. Örneğin, sürücülere mal teslimatı için en uygun rotaları bulmalarına veya farklı yolcular için evden işe optimum ulaşım mesafesini belirlemelerine yardımcı olabilir.

## Algoritma Yetenekleri

Kütüphanemiz, bir harita üzerinde **iki nokta arasındaki en optimal rotayı** oluşturma yeteneği sağlar. Aşağıdaki ana özelliklere sahiptir:

1. Yollar ve engeller dikkate alınarak haritada optimal yol araması: Sadece yolları değil, aynı zamanda parkurlar, yaya geçitleri ve optimal yolu etkileyebilecek engeller gibi arazi yollarını da dikkate alıyoruz.

2. Sadece yollarda optimal yol araması: Yalnızca yollarda bir rota bulmanız gerekiyorsa, bu yeteneği sağlıyoruz. Bu, örneğin sadece yolda seyahat etmekle sınırlı araçlar için kullanışlıdır.

3. Farklı yollar için farklı hızların ayarlanması: Farklı yollara farklı hızlar atama yeteneğine sahibiz. Örneğin, ana otoyollarda daha yüksek hızlar ve dar şeritlerde daha düşük hızlar belirlenebilir.

4. Dikdörtgen engellerin ayarlanması: Optimal yol oluşturulurken dikkate alınması gereken harita üzerinde dikdörtgen engeller tanımlayabilirsiniz. Bu, binalar veya göller gibi bilinen engellerin (yaklaşımları) olduğunda kullanışlıdır.

5. Yollar için arama yarıçapının sınırlandırılması: Arama süresini azaltmak ve yalnızca belirli bir alana odaklanmak için yollar için arama yarıçapını kısıtlayabilirsiniz.

6. Performans ve doğruluk kontrolü: Algoritmanın performansını ve doğruluğunu kontrol etme yeteneği sağlıyoruz. İstenen dengeyi elde etmek için ince ayar yapabilirsiniz.

Daha sonra bu özelliklerin her birinin daha ayrıntılı bir açıklamasını sağlayacak ve uygulamalarının örneklerini inceleyeceğiz.

## Çözüm Yaklaşımı

Yol bulma önemsiz olmasa da, geliştirme topluluğunda tanınan birkaç iyi ve güvenilir algoritma vardır.

Uygulamamızda, değiştirilmiş Lee algoritmasını kullandık. Düzlemde hücrelerden oluşan bir ızgaraya sahibiz. Başlangıç noktasından başlayarak, dalga 8 yönde (diyagonaller dahil) komşu hücrelere yayılır ve her birine ulaşmak için gereken süreyi hesaplar. Komşu hücrede bir engel veya yol olabilir. Yollar farklı hız katsayılarına sahip olabilir. Böylece, başlangıç hücresinden her hücreye ulaşmanın ne kadar sürdüğünü belirli bir yarıçap içinde veya hedefe ulaşana kadar "işaretliyoruz". Hedefe ulaştıysak, ızgaramızı kullanarak ters yolu oluşturuyoruz.

Yol ağında optimal rotayı belirlemek için birkaç adım atılması gerekir. Öncelikle yolları tanımlamanız ve her biri üzerindeki hareket hızını belirtmeniz gerekir. Ayrıca yol geçişini etkileyebilecek yapay ve doğal engelleri de göz önünde bulundurmalısınız. Bundan sonra, arama başlangıç ve hedef noktalarını belirtmelisiniz. Bu ön adımlar tamamlandıktan sonra gerçek yol bulmaya başlayabilirsiniz. Sonuç, örneğin nokta koordinatları listesi olarak temsil edilen bir yol olacaktır.

Optimal yolun seçilen ulaşım moduna bağlı olabileceğini unutmamak önemlidir, çünkü hareket hızı ve engel kümesi değişebilir. Bu nedenle, optimal yolu ararken her taşıma türü için farklı yol ve engel kümeleri kullanılmalıdır.

## GitHub'daki Demo Projesi

Kütüphanemizin işlevselliğini daha iyi anlamak için [kullanım örneğine](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths) bakalım. Bu kod, yol bulma algoritmasında yolları ve engelleri nasıl kuracağınızı ve optimal rotayı nasıl bulacağınızı göstermektedir.

Örnek aşağıdaki adımlardan oluşur:

1. Yol bilgisi (RoadInfo) listesi oluşturmak; bu liste yol segmenti (Segment) ve hareket hızı (Velocity) hakkında bilgi içerir.
2. Listeye hızlı yollar eklemek.
3. Listeye yavaş halka yolları eklemek.
4. Yol katmanı üreteci (WayLayerGenerator) oluşturmak ve yolları üreticiye eklemek.
5. Belirtilen yarıçap (radius) kullanarak başlangıç noktasından (startPoint) hedef noktalarına (goalPoint01, goalPoint02, goalPoint03) birden fazla yol aramak.
6. Haritada görüntülenecek bir yollar katmanı (roadsLayer) hazırlamak ve yol nesneleri eklemek.
7. Haritada görüntülenecek bir yol katmanı (wayLayer) hazırlamak ve bulunan her yol için geometrik nesneler oluşturmak.
8. Haritayı belirtilen yolda kaydetmek için [ShowMap fonksiyonunu](https://docs.aspose.com/gis/net/how-to-draw-geometry/) kullanarak görüntülemek.

Bu kod, yol bilgisi ve yol katmanı üretecisini kullanarak belirtilen noktalar için harita üzerinde yol rotaları oluşturur ve görüntüler.

## Arama Seçenekleri

Yol bulma işlemi, Aspose.Gis.GeoTools.WayAnalyzer ad alanında bulunan **WayLayerGenerator** sınıfı kullanılarak gerçekleştirilir.

WayLayerGenerator sınıfının başlangıç noktasından hedefe yolu bulmak için **FindTheWay yöntemi** vardır. WayLayerGenerator sınıfının bir örneğini oluşturmak için parametre olarak WayOptions geçirmemiz gerekir (tüm parametreler isteğe bağlıdır):

- StartPoint: Başlangıç noktası

- GoalPoint: Hedef noktası

- Radius: Arama yarıçapı

- Scale: Izgaranın ölçeği

- IsMoveOnlyRoad: Yalnızca yollarda yol aranıp aranmayacağı

Buradaki önemli özellik Scale parametresidir. Yapıcıda belirtilirse, sonraki aramalar için sabit bir ölçek belirleriz. Scale parametresi ayarlanmamış ancak StartPoint ve GoalPoint ayarlanmışsa, ölçeği başlangıç ve hedef noktaları arasındaki mesafe bölü 100 olarak hesaplarız. Diğer tüm durumlarda, Scale'in varsayılan değeri 1'dir. Deneyimli kullanıcılar için Scale'i ayarlamak veya StartPoint ve GoalPoint'i doğrudan en verimli şekilde yolları ve engelleri ızgarada temsil etmek (özellikle çok sayıda varsa) daha iyidir.

FindTheWay yöntemini kullanmak için başlangıç ve hedef noktalarını belirtmemiz gerekir. Ayrıca arama yarıçapını da ayarlayabiliriz (dalganın yayılacağı mesafe). Yarıçap varsayılan olarak başlangıç ve hedef noktaları arasındaki mesafenin 3 ile çarpılmasıyla hesaplanır. Başlangıç ve hedef noktaları birbirine yakın veya çok uzak olabilir, bu nedenle aralarındaki mesafeye göre ızgaramızın ölçeğini hesaplarız. Mevcut ölçek öncekiyle eşleşmiyorsa, ızgarayı yeniden hesaplarız. Ölçek Scale parametresi kullanılarak sabitlenebilir. Bu durumda hesaplanmaz ve ızgara yeniden hesaplanmaz.

Aramaya başlamadan önce ilgili AddRoad ve AddBlock yöntemleri aracılığıyla yol ve engel haritasını tanımlamamız gerekir.

**AddRoad yöntemi** için şunları belirtmemiz gerekir:

- startPoint: Yolun başlangıç noktası

- endPoint: Yolun bitiş noktası

- velocity: Yoldaki hareket hızı

**AddBlock yöntemi** için şunları belirtmemiz gerekir:

- x: Bloğun sol üst köşesinin x koordinatı

- y: Bloğun sol üst köşesinin y koordinatı

- sizeX: x eksenindeki boyut

- sizeY: y eksenindeki boyut

Bu yöntemler, yol bulma işlemine başlamadan önce yol ve engel haritasını tanımlamamıza olanak tanır.

## Kod örnekleri

Yol bulma algoritmasında yolları ve engelleri nasıl kuracağınızı ve optimal rotayı nasıl bulacağınızı gösteren bazı kod örnekleri aşağıdadır.

Örnek 1: Başlangıç ve hedef noktalar arasında bir yol bulmak.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Örnek 2**: Scale parametresini ayarlamak ve nokta için negatif koordinatlara sahip olmak.

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Örnek 3**: IsMoveOnlyRoad parametresini ayarlamak ve arama yarıçapını belirlemek.

```
WayOptions mapGeneratorOptions = new WayOptions();
mapGeneratorOptions.IsMoveOnlyRoad = true;
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddRoad(new Point(100, 100), new Point(140, 150), 10);
generator.AddRoad(new Point(140, 150), new Point(190, 100), 10);
Point startPoint = new Point(100, 100);
Point goalPoint = new Point(190, 100);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 100);
```

**Örnek 4**: Daha hızlı arama için Scale parametresini ayarlamak.

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**Örnek 5**: Çoklu arama örneği.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddBlock(200, 1700, 1500, 100, 0);
generator.AddBlock(1700, 200, 100, 1600, 0);
generator.AddBlock(200, 200, 1500, 100, 0);
generator.AddRoad(new Point(1000, 1150), new Point(200, 600), 10);
generator.AddRoad(new Point(50, 450), new Point(150, 1850), 10);

Point startPoint = new Point(1000, 1000);
Point goalPoint = new Point(1900, 1000);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 3500);

Point startPoint = new Point(50, 50);
Point goalPoint = new Point(70, 70);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

Bu kod örnekleri, yol bilgisi ve yol katmanı üretecisini kullanarak belirtilen noktalar için harita üzerinde yol rotaları oluşturur ve görüntüler.

**Özetle**, optimal yol bulucu, yol ağlarını analiz etmek ve harita üzerindeki noktalar arasında en verimli rotaları belirlemek için güçlü bir araçtır. Yol türleri, engeller ve farklı hızlar gibi çeşitli faktörleri dikkate alarak optimal yolu hesaplar. Hem yollarda hem de arazi yollarında yol arama yeteneği, arama yarıçapını kontrol etme ve performansı ve doğruluğu ayarlama özelliği ile bu algoritma çok yönlü bir rota optimizasyonu çözümü sunar. Farklı ulaşım modlarını dikkate alarak ve buna göre yol ve engel kümelerini ayarlayarak teslimat planlaması veya işe gidip gelme optimizasyonu gibi çeşitli senaryolarda kullanılabilir. Sağlanan kod örnekleri ve açıklamalar, algoritmanın yeteneklerini ve kullanımına dahil olan adımları gösterir. Sonuç olarak optimal yol bulucu, bir yol ağında en verimli rotaları bulmak ve navigasyonu iyileştirmek için sağlam bir yoldur.