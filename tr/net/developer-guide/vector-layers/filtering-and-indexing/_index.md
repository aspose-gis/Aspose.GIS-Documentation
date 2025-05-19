---
title: C# Dilinde GIS Vektör Katmanlarını Filtreleme ve Dizinleme
linktitle: Filtreleme ve Dizinleme
second_title: Aspose.GIS for .NET
type: docs
url: /tr/net/filtering-and-indexing/
weight: 30
description: GIS C# .NET Kütüphanesi veya API'si ile, GIS vektör katmanlarını öznitelik değerlerine veya mekansal sınırlara göre filtreleyebilirsiniz. Ayrıca, filtrelemeyi ve mekansal sorguları hızlandırmak için dizinleri kullanabilirsiniz.
---

Aspose.GIS for .NET ile katmanları öznitelik değerlerine veya mekansal sınırlara göre filtreleyebilirsiniz. Ayrıca, filtrelemeyi ve mekansal sorguları hızlandırmak için dizinleri kullanabilirsiniz.
## **Öznitelik indeksi**
### **İndeks Olmadan Filtreleme**
Bir katmanı bir özniteliğin değerlerine göre nasıl filtreleyeceğiniz aşağıda açıklanmıştır:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **İndeksle Filtreleme**
Yukarıdaki kod, katman yalnızca bir kez filtrelendiği sürece iyidir. Ancak, katmanın birden çok kez sorgulanması olasıysa, öznitelik indekslerinden faydalanabiliriz. Öznitelik indeksi oluşturmak biraz zaman alır, ancak filtrelemeyi hızlandırmak için birçok kez yeniden kullanılabilir.

Aşağıdaki örnek, bir öznitelik indeksi dosyası kullanarak katman filtrelemesini özniteliğin değerlerine göre hızlandırır:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **Filtrelenmiş Öznitelikleri Kaydetme**
Filtrelenmiş öznitelikler katmanlara kaydedilebilir:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **Filtrelenmiş Öznitelikleri Görüntüleme**
Filtrelenmiş öznitelikleri görüntülemek de mümkündür. Aşağıdaki örnekler, öznitelik indeksini kullanarak 2000'den büyük nüfusa sahip tüm öznitelikleri hızlı bir şekilde seçer ve bunları haritaya ekler:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **Mekansal İndeks**
Mekansal indeksler, mekansal sorguları hızlandırmak için kullanılır. Öznitelik indeksleri gibi, mekansal indeksler de oluşturulduktan sonra yeniden kullanılır.
### **Noktaya En Yakın Öznitelikleri Bulma**
Mekansal indeksi kullanarak belirli bir noktaya en yakın özniteliği arama işlemini hızlandırmanın yolu aşağıda açıklanmıştır:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **Geometriyle Kesişen Öznitelikleri Seçme**
Aşağıdaki örnekler, geometriyle kesişen özniteliklerin seçimini hızlandırmak için mekansal indeksi kullanır:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
