---
title: "Katmanları Geometri veya Özellik Kullanarak Birleştirme"
type: docs
url: /tr/net/how-to-join-layers
weight: 70
---

## Özet

CBS'de (Coğrafi Bilgi Sistemleri) birleştirmeler, farklı katmanlardan gelen bilgileri ortak bir özellik veya mekânsal ilişkiye dayalı olarak birleştirmenin güçlü bir mekanizmasıdır. Birleştirmeler, bir katmanın (kaynak katman) öznitelik verilerini başka bir katmana (hedef katman) ortak bir alan veya mekânsal konum kullanarak birleştirmenizi sağlar. İlk yöntem, tabloda bulunan özelliğe göre veri birleştirmesidir (öznitelik). Ortak bir alan kullanarak, örneğin benzersiz bir anahtar, bir tablodaki kayıtları başka bir tablodaki kayıtlara bağlayabilirsiniz. İkinci yaklaşım ise konuma göre veri birleştirmesidir (mekânsal olarak). Her iki yaklaşımı da destekliyor ve ihtiyaçlarınıza bağlı olarak bunları kullanma fırsatı sunuyoruz.

Diyelim ki farklı bölgeler için nüfus değişimini açıklayan veriler aldınız ve bu bilgilere dayanarak çeşitli nüfus artışı haritaları oluşturmak istiyorsunuz. Nüfus verileriniz veritabanınızdaki bir tabloda depolanıyor ve katmanınızla ortak bir alanı paylaşıyorsa, bu verileri coğrafi nesnelerinizle birleştirebilir ve katman nesnelerini etiketlemek, kategorize etmek, sorgulamak veya analiz etmek için ek alanlar kullanabilirsiniz.

Tipik olarak, veri birleştirmesini her iki tabloda da bulunan bir alan değerine göre gerçekleştirirsiniz. Alan adlarının mutlaka eşleşmesi gerekmez, ancak veri türleri aynı olmalıdır - sayılarla sayılar, dizelerle dizeler ve benzeri. Veri birleştirmesini "Birleştirme Ekle" jeo-işlem aracı kullanılarak gerçekleştirebilirsiniz. Öznitelikleri birleştirirken, birleştirilen alanlar mevcut tabloya dinamik olarak eklenir. Birleştirmeyi eklerken veya kaldırırken takma adlar, görünürlük ve sayı biçimlendirme gibi alan özellikleri korunur.

## Anahtar Alanla Birleştirmek için Yetenekler

- Bu yaklaşım, ortak bir anahtar alana dayalı olarak **farklı tablolardaki kayıtları bağlamanıza** olanak tanır. Kayıtlar arasındaki ilişkiyi kurmak için karşılaştırma için kullanılacak anahtar alanı belirtebilirsiniz. Özellikle bir tanımlayıcı veya başka benzersiz bir özniteliğe dayalı olarak verileri birleştirmek istediğinizde bu kullanışlıdır.

Anahtar alana göre veri karşılaştırması için yöntemi belirtme:

- Verileri birleştirirken **farklı karşılaştırma yöntemleri** tanımlayabilirsiniz. Örneğin, tam eşleşmeyi seçebilir, bir kalıba göre karşılaştırabilir veya değerler aralığında karşılaştırabilirsiniz. Bu, kayıtlar arasındaki ilişkilerin daha hassas bir şekilde belirlenmesini sağlar ve veri birleştirme sürecini kontrol etmenizi sağlar.

Birleştirilecek öznitelik adlarının listesini belirtme:

- Verileri birleştirirken **birleştirmek için belirli öznitelikleri** belirtebilirsiniz. Bu, yalnızca gerekli öznitelikleri birleştirmeyi seçmenize ve sonuç tablosunun yapısını yönetmenize olanak tanır.

## Geometri Kullanarak Birleştirmek için Yetenekler

- Bu yaklaşım, verileri **mekânsal konumlarına** göre bağlamanıza olanak tanır. En yakın geometrik nesnelerin birleştirme için aranacağı bir arama yarıçapı tanımlayabilirsiniz. Verileri coğrafi konumlarına göre birleştirmek istediğinizde bu kullanışlıdır.

En yakın geometrik nesneleri bulmak için arama yarıçapını kontrol etme:

- Konuma dayalı veri birleştirirken **arama yarıçapını** kontrol edebilirsiniz. Bir yarıçap değeri belirleyerek, en yakın nesnelerin birleştirme için aranacağı mesafeyi belirlersiniz. Bu, mekânsal ilişkilerine göre hangi nesnelerin veri birleştirme sürecine katılacağını kontrol etmenizi sağlar.

## Demo Projesi

Kütüphanemizin işlevselliğini daha iyi anlamak için [kullanım örneğine](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Layers.Join) göz atalım. Bu kod, özniteliklere veya geometriye göre vektör katmanlarını birleştirmenin nasıl yapılacağını göstermektedir.

Sağlanan kod, veri birleştirme işlemlerini gerçekleştirmek için LayerConstructor sınıfını kullanan JoinByIndex() ve JoinByCoords() olmak üzere iki yöntemden oluşur.

JoinByIndex() yönteminde:

- İlişkili özniteliklere sahip geometrilerin listeleri oluşturulur.

- Bir LayerConstructor nesnesi başlatılır.

- Yöntem, sağlanan geometrilere göre bir vektör katmanı ve bir geometri katmanı oluşturur.

- Geometri katmanı, "Id" benzersiz tanımlayıcısı kullanılarak JoinLayersById() yöntemiyle birleştirilir.

- Sonuçta elde edilen birleştirilmiş vektör katmanı döndürülür.

JoinByCoords() yönteminde:

- İlişkili özniteliklere sahip geometrilerin listeleri oluşturulur.

- Bir LayerConstructor nesnesi başlatılır.

- Geometri katmanları, sağlanan geometrilere göre oluşturulur.

- Geometri katmanları, eşleşen koordinatlara göre JoinLayersByCoords() yöntemi kullanılarak birleştirilir.

- Sonuçta elde edilen birleştirilmiş vektör katmanı döndürülür.

Özetle, bu yöntemler iki farklı veri birleştirme yaklaşımını göstermektedir: biri benzersiz bir tanımlayıcıya dayalı ve diğeri eşleşen koordinatlara dayalı. LayerConstructor sınıfı bu veri birleştirme işlemlerini kolaylaştırır.

## Dizin için Birleştirme Seçenekleri

JoinOptions sınıfı, katmanları yapılandırmak için bir dizi seçenek sunar. Her seçeneğe daha yakından bakalım:

- **JoinAttributeName**: Bu seçenek, karşılaştırma koşulunda kullanılacak birleştirilmiş katmandan öznitelik adını belirtmenize olanak tanır. İki katman arasındaki bağlantıyı kurar.

- **TargetAttributeName**: Bu seçenekle, ana katmandan birleştirilmiş katmanın özniteliğiyle karşılaştırılacak öznitelik adını belirtebilirsiniz. Katmanlar arasındaki eşleşen özellikleri belirlemeye yardımcı olur.

- **JoinAttributeNames**: Bu seçenek, birleştirmek istediğiniz öznitelik adlarının listesini belirtmenizi sağlar. Bu liste boş bırakılırsa veya null olarak ayarlanırsa, birleştirilmiş katmandan tüm öznitelikler birleştirme işlemine dahil edilir. Ancak belirli öznitelik adları seçerek, birleştirilen tablonun yapısını yönetebilir ve yalnızca gerekli öznitelikleri birleştirebilirsiniz.

- **ConditionComparer**: Bu seçenek, iki katmanın özelliklerindeki öznitelik değerlerini karşılaştırmak için özel bir mantık tanımlamanıza olanak tanır. Varsayılan olarak, eşitliği kontrol eden EqualityComparer.Default karşılaştırıcıyı kullanır. Ancak daha uzmanlaşmış karşılaştırma gereksinimleri için kendi özel karşılaştırıcınızı uygulayabilirsiniz.

- **JoinedAttributesPrefix**: Bu seçenek, birleştirilmiş katmanın öznitelik adları için bir ön ek dize belirtmenizi sağlar. Varsayılan değer "joined_", yani birleştirilen öznitelikler sonuçta elde edilen birleştirilmiş katmanda "joined_" ile öneklenir. Bu ön ek, birleştirilmiş öznitelikleri ana katmanın orijinal özniteliklerinden ayırmaya yardımcı olur.

JoinOptions sınıfı, katmanları birleştirme sürecinin çeşitli yönleri üzerinde esneklik ve kontrol sağlar. Birleştirmek için öznitelikleri belirtebilir, karşılaştırma mantığını özelleştirebilir ve sonuçta elde edilen birleştirilmiş öznitelikler için bir ön ek tanımlayabilirsiniz. Bu seçenekler, birleştirme işlemini belirli ihtiyaçlarınıza göre uyarlamanıza ve birleştirilmiş katmanlardan anlamlı içgörüler elde etmenize olanak tanır.

## Geometri için Birleştirme Seçenekleri

**JoinByGeometryOptions** sınıfı, geometriye dayalı olarak katmanları birleştirmek için seçenekleri temsil eder. Her seçeneğin işlevselliğini keşfedelim:

- **Radius**: Bu seçenek, birleştirilmiş geometrinin aranacağı yarıçapı belirtir. Ana katmandaki özelliklerin, mekânsal ilişkilerine göre birleştirilmiş katmandaki özelliklerle eşleşeceği yakınlığı belirler.

- **ConditionComparer**: Bu seçenek, iki katmanın özelliklerinden öznitelik değerlerini karşılaştırmak için özel bir mantık tanımlamanıza olanak tanır. Varsayılan olarak, eşitliği kontrol eden EqualityComparer.Default kullanılır. Ancak daha belirli karşılaştırma gereksinimleri için kendi özel karşılaştırıcınızı uygulayabilirsiniz.

- **JoinedAttributesPrefix**: Bu seçenek, birleştirilmiş katmanın öznitelik adları için bir ön ek dize belirtmenizi sağlar. Varsayılan değer "joined_", yani birleştirilen öznitelikler sonuçta elde edilen birleştirilmiş katmanda "joined_" ile öneklenir. Bu ön ek, birleştirilmiş öznitelikleri ana katmanın orijinal özniteliklerinden ayırmaya yardımcı olur.

JoinByGeometryOptions sınıfı, mekânsal ilişkilerine dayalı olarak katmanları birleştirme sürecini özelleştirmenin araçlarını sağlar. Bir arama yarıçapı belirterek, geometrilerin hangi yakınlıkta eşleşeceğini kontrol edebilirsiniz. Bu, özellikler arasındaki mekânsal ilişkiye göre birleştirme işlemini ince ayar yapmanızı sağlar. Özel bir karşılaştırıcı sağlama seçeneği, karşılaştırma konusunda esneklik sağlar ve birleştirilmiş özniteliklere ön ek ekleme seçeneği, sonuçta elde edilen birleştirilmiş katmanda bunları ayırtmaya yardımcı olur.

Bu seçenekleri kullanarak mekânsal olarak farkında olan veri birleştirmeleri gerçekleştirebilir ve mekânsal yakınlıklarına ve öznitelik değerlerine dayalı içgörüler elde edebilirsiniz.

## Özet

CBS'deki veri birleştirme mekanizması, geometrik nesnelerin ilgili öznitelikleriyle farklı katmanlardan birleştirilmesini sağlar. Bu, verilerdeki mekânsal ve özniteliksel ilişkiler temelinde analiz yapma ve bilgi çıkarma olanağı sağlar. Mevcut seçenekler, belirli gereksinimleri karşılamak ve CBS veri analizinde anlamlı içgörüler elde etmek için birleştirme sürecini özelleştirmeyi mümkün kılar.

Veri birleştirmesi çeşitli görevleri kolaylaştırır:

- Belirli mekânsal kriterleri karşılayan nesneleri bulma, örneğin belirli bir noktadan 500 metre yarıçapındaki tüm binaları belirleme.

- Daha kapsamlı ve bilgilendirici bir genel bakış oluşturmak için coğrafi verileri birleştirme.

- Eğilimleri ve kalıpları belirlemek için belirli mekânsal koşullara göre nesnelerin öznitelik değerlerini analiz etme.

Veri birleştirme seçenekleri, nesne eşleştirme sürecini hassas bir şekilde yapılandırmanıza olanak tanır. Bu seçenekler arasında birleştirmek için öznitelikleri seçmek, öznitelik değerlerini karşılaştırmak için özel mantık tanımlamak ve birleştirilmiş verilere bir ön ek eklemek yer alır. Bu seçenekler, CBS veri analizinin hedeflerine ve gereksinimlerine uyum sağlayarak esneklik ve uyarlanabilirlik sağlar.

Veri birleştirme mekanizması, coğrafi verilerin entegrasyonunda ve analizinde önemli bir rol oynar ve incelenen nesnelerin mekânsal ve özniteliksel doğası hakkında daha kapsamlı bir anlayış sağlar.