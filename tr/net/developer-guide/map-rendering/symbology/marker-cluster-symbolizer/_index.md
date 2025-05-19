---
title: "İşaret Kümesi Sembolleştirici"
type: docs
url: /tr/net/marker-cluster-symbolizer/
weight: 65
description: İşaret Kümesi Sembolleştirici, GIS C# Kütüphanesinde veya API'sinde işaretlerin belirtilen mesafede kümelenmesini sağlar.
---

## **İşaret Kümesi Sembolleştirici**
İşaret Kümesi Sembolleştirici gelişmiş sembolleştiricilerden biridir. Belirtilen mesafedeki işaretlerin kümelenmesini sağlar.

Bu C# örneğinde, küme merkezlerini kırmızı daireler olarak çizdik. Ayrıca, her kümeye ait iç içe geçmiş tüm noktaları farklı renkler kullanarak çizdik. Bunu yapmak için, her küme için kendi stilini ayarlayan FeaturesBasedConfiguration fonksiyonunu kullandık.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterMarkerSymbolizer.cs" >}}

İşte sonuç:

![points cluster](points-cluster.png)

## **Toplam Öğrenci Sayısını Çizin**

Bu örnek, kümedeki toplam öğe sayısını görüntüler.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterTextSymbolizer.cs" >}}

İşte sonuç:

![digits cluster](digits-cluster.png)
