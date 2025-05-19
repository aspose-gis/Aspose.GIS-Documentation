---
title: "Çizgi Sembollendirici"
type: docs
url: /tr/net/line-symbolizer/
weight: 20
description: GIS C# Kütüphanesi veya API'si, 1 boyutlu geometriler olan çizgiler için Basit Çizgi sembollendiricisini destekler ve Nokta, Çizgi, Yüzey gibi her tür geometri üzerinde uygulanabilir.
---

## **Çizgi Sembollendirici**
Basit Çizgi sembollendiricisi, özelleştirilebilir stile sahip bir çizgi çizer. Bu, 1 boyutlu geometriler (çizgiler) için varsayılan sembollendiricidir. 

Desteklenen stil seçenekleri:

|**Özellik**|**Açıklama**|
| :- | :- |
|[Renk](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|Çizgiye verilen rengi ve şeffaflığı belirtir.|
|[Genişlik](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|Çizginin genişliğini belirtir|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|Çizgi segmentlerinin kesişimlerinde çizgilerin nasıl oluşturulacağını belirler.|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|Sembol çizgi çalışmasının nasıl çizilmesi gerektiğini belirtir.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|Dashed çizgilerde alternatif tireler ve boşlukların uzunluklarını belirten bir dizi mesafe belirtir.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|Bir çizginin başlangıcından bir tire deseninin başlangıcına olan mesafeyi belirtir.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>Çizgilerin uçlarında nasıl oluşturulacağını belirtir.</p><p>- Butt - keskin kare kenar</p><p>- Round - yuvarlatılmış kenar</p><p>- Square - hafifçe uzatılmış kare kenar</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|Orijinal çizgiden uzaklığı belirtir. Pozitif mesafe için ofset, giriş çizgisinin sol tarafında (çizgi yönüne göre) olacaktır. Negatif bir mesafe için sağ tarafta olacaktır.|

### **Geometri Türleri**
` `Sembollendirici herhangi bir türdeki geometrilere uygulanabilir.

|**Geometri Boyutu**|**Geometri Türleri**|**Oluşturma Davranışı**|
| :-: | :-: | :-: |
|**Nokta**|Nokta, Çoklu Nokta|Küçük bir uzunluktaki yatay yönlü bir çizgi çizer ve noktanın merkezinde iki uç kapağı vardır.|
|**Çizgi**|ÇizgiDizesi, DaireselDize, Bileşik Eğri, ÇizgiHalkası, Çoklu Eğri, Çoklu ÇizgiDizesi|Çizgiyi çizer.|
|**Yüzey**|Poligon, Eğri Poligonu, Çoklu Poligon, Çoklu Yüzey|Geometrinin kapalı ana hattı çizgi dizesi olarak kullanılır (uç kapakları yok)|

GeometryCollection'lar için oluşturma davranışı koleksiyondaki her geometri için ayrı ayrı belirlenir. Karışık geometri tipine sahip katmanlar GeometryCollection'lar için mantığı izler.

Bir sembollendiriciyi belirli geometri türleriyle sınırlamak için MixedGeometrySymbolizer kullanın.

### **Örnekler**
Varsayılan olarak çizgi sembollendiricisi siyah çizgiler çizer:



İşte çizgi rengini maviye nasıl değiştireceğiniz:




|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

Daha gelişmiş senaryolar için, özellik öznitelik değerlerine göre çizgi stilini dinamik olarak ayarlamak isteyebilirsiniz. İşte nasıl yapacağınız:




|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |




Çizgilere etiketler de eklemek isteyebilirsiniz. Örnekler için [Çizgi Etiketleme Örnekleri](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) adresini ziyaret edin.
