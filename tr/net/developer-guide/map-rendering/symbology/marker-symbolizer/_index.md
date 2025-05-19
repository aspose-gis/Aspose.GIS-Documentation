---
title: "İşaret Sembolleştirici"
type: docs
url: /tr/net/marker-symbolizer/
weight: 10
description: GIS C# Kütüphanesi veya API'si, Nokta, Çizgi, Yüzey gibi her tür geometi üzerinde özelleştirilebilir dolgu ve kenarlık ile önceden tanımlanmış bir şekil çizen Basit İşaret sembolleştiricisini destekler.
---

## **İşaret Sembolleştirici**
Basit İşaret sembolleştirici, özelleştirilebilir dolgu ve kenarlık ile önceden tanımlanmış bir şekil çizer. Bu, 0 boyutlu geometriler (noktalar) için varsayılan sembolleştiricidir.

Desteklenen şekiller şunlardır:

|![todo:image_alt_text](marker-symbolizer_1.png)|Daire| |![todo:image_alt_text](marker-symbolizer_2.png)|Yıldız|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Kare| |![todo:image_alt_text](marker-symbolizer_4.png)|Çapraz|
|![todo:image_alt_text](marker-symbolizer_5.png)|Üçgen| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

Desteklenen stil seçenekleri:

|**Özellik**|**Açıklama**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|İşaretin şeklini belirtir.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|İşaret şeklinin boyutunu belirtir|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|Dolguya verilen rengi ve şeffaflığı belirtir|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|Çizgiye verilen rengi ve şeffaflığı belirtir|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|Çizginin genişliğini belirtir|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|Çizgi segmentlerinin kesişimlerinde çizgilerin nasıl oluşturulacağını belirler.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|Sembol çizgi çalışmasının nasıl çizilmesi gerektiğini belirtir.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|Kesikli çizgilerdeki alternatif tirelerin ve boşlukların uzunluğunu belirten bir dizi mesafe belirtir.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|Bir çizginin başlangıcından bir tire deseninin başlangıcına olan mesafeyi belirtir.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|Sembolün merkez noktası etrafında döndürülmesini, ondalık derece cinsinden belirtir. Pozitif değerler saat yönünde dönüşü, negatif değerler ise saat yönünün tersine dönüşü gösterir. Varsayılan 0'dır.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|Bir noktanın konumundan şekil çapa noktasına olan yatay mesafeyi belirtir.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|Bir noktanın konumundan şekil çapa noktasına olan dikey mesafeyi belirtir.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|İşaret şeklinin hangi tarafının noktanın konumuyla yatay olarak hizalanacağını belirtir.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|İşaret şeklinin hangi tarafının noktanın konumuyla dikey olarak hizalanacağını belirtir.|

### **Geometri Türleri**
` `Sembolleştirici, herhangi bir türdeki geometrilere uygulanabilir.

|**Geometri Boyutu**|**Geometri Türleri**|**Oluşturma Davranışı**|
| :-: | :-: | :-: |
|**Nokta**|Nokta, Çoklu Nokta|Şekli nokta koordinatının merkezine çizer.|
|**Çizgi**|ÇizgiDizesi, DaireselDize, Bileşik Eğri, ÇizgiHalkası, Çoklu Eğri, Çoklu ÇizgiDizesi|<p>Şekli geometrinin ağırlık merkezine çizer</p><p> </p>|
|**Yüzey**|Poligon, Eğri Poligonu, Çoklu Poligon, Çoklu Yüzey||

Geometri Koleksiyonları için oluşturma davranışı koleksiyondaki her geometri için ayrı ayrı belirlenir. Karışık geometri tipine sahip katmanlar Geometri Koleksiyonları için mantığı izler.

Belirli geometri tipleriyle sınırlamak için MixedGeometrySymbolizer kullanın.

### **Örnekler**
Varsayılan olarak işaret sembolleştirici siyah daireler çizer:



İşte dolgu rengini kırmızıya değiştirmek nasıl yapılır:




|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

Başka bir örnek olarak önceden tanımlanmış bir şekil (üçgen) ile stil oluşturma:




|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----

Daha gelişmiş senaryolar için işaret stilini özellik nitelik değerlerine göre dinamik olarak ayarlamak isteyebilirsiniz. İşte nasıl yapıldığı:




|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----

İşaretlerinize etiketler de eklemek isteyebilirsiniz. Örnekler için [Nokta Etiketleme Örnekleri](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) adresini ziyaret edin.
