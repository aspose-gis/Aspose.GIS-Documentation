---
title: Semboloji - C# GIS API'si
linktitle: "Semboloji"
type: docs
url: /tr/symbology/
weight: 10
description: GIS C# Kütüphanesi veya API'si, özellik geometrisini Çizim için sembolleştiricileri destekler. İşaretleyici, Çizgi, Doldurma ve daha karmaşık görselleştirmeler oluşturmak için sembolleştiricilerin birleştirilmesi gibi.
---

Bir sembolleştirici, bir harita üzerinde özellik geometrisini çizmenin bir yoludur.

|** **|**Sembolleştirici**|**API Sınıfı**|**Açıklama**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**İşaretleyici**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Özelleştirilebilir dolgu ve ana hat ile önceden tanımlanmış bir şekil çizer.|
|![todo:image_alt_text](symbology_2.png)|**Çizgi**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Özelleştirilebilir stil ile bir çizgi çizer.|
|![todo:image_alt_text](symbology_3.png)|**Doldurma**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Bir çizgiyle sınırlanan bir çokgeni veya alanı özelleştirilebilir dolgu ve vuruşla doldurur.|
Çizim yapan sembolleştiricilere ek olarak, daha karmaşık görselleştirmeler oluşturmak için diğer sembolleştiricileri birleştirmeye olanak tanıyan başka birçok sembolleştirici vardır.

|**Sembolleştirici**|**API Sınıfı**|**Açıklama**|
| :- | :- | :- |
|**Katmanlı Sembolleştirici**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Bir özelliği birbirinin üzerine birkaç sembolleştirici ile çizer|
|**Karışık Geometri Sembolleştirici**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Karışık türlerde geometrilere sahip katmanlardan gelen özellikleri, her geometri türü için belirli bir sembolleştirici ile çizer|
|**Kural Tabanlı Sembolleştirici**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Kullanıcı tarafından belirtilen kurallara göre bir özelliğe uygulamak için bir sembolleştirici seçer.|
|**İşaretleyici Kümesi Sembolleştirici**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|İşaretleyicilerin kümelenmesini, bu öğelerin gruplandırılmasını çizer.|
|**Geometri Üretici Sembolleştirici**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Renderlemeden önce özellik geometrisinin değiştirilmesine izin verir.|
|**Boş Sembolleştirici**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|Hiçbir şey çizmez. Kural tabanlı sembolleştirici gibi diğer sembolleştiricilerle birleştirildiğinde kullanışlıdır.|
