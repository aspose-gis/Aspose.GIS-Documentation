---
title: "Basit Etiketleme"
type: docs
url: /tr/net/simple-labeling/
weight: 10
---

## **Basit Etiketleme**
Basit Etiketleme, özelliklerin nasıl etiketlenmesi gerektiğini belirtir.

Desteklenen seçenekler şunlardır:

|**Özellik**|**Açıklama**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Etiketlerin kaynağı olarak kullanılacak özellik adını belirtir.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Etiket metnini özelleştirmek ve biçimlendirmek için bir yol sağlar. LabelAttribute'u geçersiz kılar|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Metni oluşturmak için kullanılacak yazı tipi ailesini belirtir. Varsayılan, sisteme bağlı bir değerdir.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Metne uygulanacak stil.</p><p>- FontStyle.Regular - normal metin.</p><p>- FontStyle.Bold - kalın metin.</p><p>- FontStyle.Italic - italik metin.</p><p>- FontStyle.Underine - altı çizili metin.</p><p>- FontStyle.StrikeOut - ortasından çizilmiş metin.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Metnin boyutunu belirtir.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Metnin rengini belirler.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Metnin etrafındaki halonun (veya ana hattın) boyutunu belirler.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Metnin etrafındaki halonun rengini belirler.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Etiketleme motoruna geçirmeden önce geometrileri dönüştürmek için kullanılacak geometri ifadesi.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Çok parçalı geometriler için oluşturma davranışını belirtir.</p><p>- MultipartMode.All - geometri her parçasının yakınına bir etiket yerleştirin.</p><p>- MultipartMode.Any - geometrinin herhangi bir parçasına yakın bir etiket yerleştirin.</p><p>- MultipartMode.Largest - geometrinin en büyük parçası yakınında bir etiket yerleştirin.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Etiketlerin geometriye göre nasıl konumlandırıldığını belirtir.</p><p>- PointLabelPlacement - etiketi geometrinin ortasına yakın yerleştirir.</p><p>- LineLabelPlacement - etiketi geometri boyunca veya çevresine yerleştirir.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Diğer etiketlerle çakışması durumunda etiketin önceliğini belirtir.<br>Daha düşük öncelikli etiket oluşturulmaz. Varsayılan 1000'dir.|

## **Örnekler**
### **Nokta Etiketleme Örnekleri**
Varsayılan olarak Basit Etiketleme, metni noktaların üzerine çizer:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
Yazı tipi stilini şu şekilde ayarlayabilirsiniz:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
Metnin konumunu nokta özelliğine göre kontrol etmek için, yerleştirme özelliği ayarlanmalıdır:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
Daha gelişmiş senaryolar için, özellikler için farklı etiketlemeleri seçmek isteyebilirsiniz. İşte nasıl yapacağınız:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **Çizgi Etiketleme Örnekleri**
Varsayılan olarak Basit Etiketleme, etiketi çizginin ortasına yakın çizer:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
Etiketleri çizgilere paralel olacak şekilde döndürmek için LineLabelPlacement ile LineLabelAlignment.Parallel kullanılabilir:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
Metinlerin çizgiyi tam olarak takip etmesini istiyorsanız, LineLabelPlacement ile LineLabelAlignment.Curved kullanılabilir:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
Metinlerin çizgiyle çakışmasını istemiyorsanız, LineLabelPlacement.Offset kullanın:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
Daha gelişmiş senaryolar için, etiket stilini özellik nitelik değerlerine göre dinamik olarak ayarlamak isteyebilirsiniz. İşte nasıl yapacağınız:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
