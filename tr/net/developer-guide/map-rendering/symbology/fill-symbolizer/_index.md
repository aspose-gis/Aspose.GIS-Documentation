---
title: "Doldurma Sembollendiricisi"
type: docs
url: /tr/net/fill-symbolizer/
weight: 30
description: GIS C# Kütüphanesi API'si, Nokta, Çizgi, Yüzey gibi her türlü çokgenin 2 boyutlu geometrileri için stil ve çizgi sağlamak üzere Basit Doldurma sembollendiricisi destekler.
---

## **Doldurma Sembollendiricisi**
Basit Doldurma sembollendiricisi, özelleştirilebilir bir dolgu stili ve çizgisi ile bir alanı doldurur. Bu, 2 boyutlu geometriler (çokgenler) için varsayılan sembollendiricidir.

Bir çokgenin "delikleri" varsa, bunlar doldurulmaz, ancak deliklerin etrafındaki sınırlar normal şekilde çizilir. Delikler içindeki “adalar” doldurulur ve çizilir ve bu böyle devam eder.

Desteklenen stil seçenekleri:

|**Özellik**|**Açıklama**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Dolguya verilen rengi ve şeffaflığı belirtir.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - Katı dolgu</p><p>- None - Çokgeni doldurma</p><p>- Horizontal Hatch - Yatay çizgilerden oluşan bir desen.</p><p>- Vertical Hatch - Dikey çizgilerden oluşan bir desen.</p><p>- Cross Hatch - Yatay ve dikey çizgilerin kesiştiği belirtir.</p><p>- Forward Diagonal Hatch - Üst sol köşeden alt sağ köşeye doğru olan diyagonal çizgilerden oluşan bir desen.</p><p>- Backward Diagonal Hatch - Üst sağ köşeden alt sol köşeye doğru olan diyagonal çizgilerden oluşan bir desen.</p><p>- Diagonal Cross Hatch - Çapraz diyagonal çizgilerden oluşan bir desen.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Çizgiya verilen rengi ve şeffaflığı belirtir.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Sembol çizgisinin nasıl çizilmesi gerektiğini belirtir.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Çizgi genişliğini belirtir.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Kesikli çizgilerdeki alternatif tirelerin ve boşlukların uzunluğunu belirten bir dizi mesafe belirtir.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Bir çizginin başlangıcından bir tire deseninin başlangıcına olan mesafeyi belirtir.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Çizgi segmentlerinin kesişimlerinde çizgilerin nasıl oluşturulacağını belirler.</p><p>- Miter - keskin köşe</p><p>- Round - yuvarlatılmış köşe</p><p>- Bevel - diyagonal köşe</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Bir noktadan şekil çapa noktasına yatay mesafeyi belirtir.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Bir noktadan şekil çapa noktasına dikey mesafeyi belirtir.|

### **Geometri Türleri**
` `Sembollendirici, herhangi bir türdeki geometrilere uygulanabilir.

|**Geometri Boyutu**|**Geometri Türleri**|**Oluşturma Davranışı**|
| :-: | :-: | :-: |
|**Nokta**|Nokta, Çoklu Nokta|Küçük bir kare ortogonal çokgen çizer.|
|**Çizgi**|ÇizgiDizesi, DaireselDize, Bileşik Eğri, ÇizgiHalkası, Çoklu Eğri, Çoklu ÇizgiDizesi|Çizginin başını sonuna bağlayarak doldurma için kapatılır. Yalnızca orijinal çizgi çizilir.|
|**Yüzey**|Çokgen, EğriÇokgen, ÇokluÇokgen, ÇokluYüzey|Çokgen çizer.|

Geometri Koleksiyonları için oluşturma davranışı koleksiyondaki her geometri için ayrı ayrı belirlenir. Karışık geometri tipine sahip katmanlar Geometri Koleksiyonları mantığını izler.

Sembollendiriciyi belirli geometri türleriyle sınırlamak için MixedGeometrySymbolizer kullanın.

### **Örnekler**
Varsayılan olarak Basit Doldurma sembollendiricisi siyah bir çizgi çizer ve katı beyaz dolgu yapar:



Burada stili değiştirebilirsiniz:


|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

Poligonlarınıza etiketler de eklemek isteyebilirsiniz. Poligon sınırını nasıl etiketleyeceğinize dair örneklere ulaşmak için [Çizgi Etiketleme Örnekleri](/gis/tr/simple-labeling/#simplelabeling-lineslabelingexamples) adresini ziyaret edin veya çokgen merkezlerini nasıl etiketleyeceğinize dair örneklere ulaşmak için [Nokta Etiketleme Örnekleri](/gis/tr/simple-labeling/#simplelabeling-pointslabelingexamples) adresini ziyaret edin.
