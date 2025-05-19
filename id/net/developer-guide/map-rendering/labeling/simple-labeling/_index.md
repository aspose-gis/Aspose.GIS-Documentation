---
title: "Pelabelan Sederhana"
type: docs
url: /id/net/simple-labeling/
weight: 10
---

## **Pelabelan Sederhana**
Pelabelan Sederhana menentukan bagaimana fitur harus diberi label.

Opsi yang didukung adalah:

|**Properti**|**Deskripsi**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Menentukan nama atribut yang akan digunakan sebagai sumber label.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Memberikan cara untuk menyesuaikan dan memformat teks label. Menggantikan LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Menentukan keluarga font yang akan digunakan untuk merender teks. Defaultnya adalah nilai yang bergantung pada sistem.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Gaya yang diterapkan ke teks.</p><p>- FontStyle.Regular - teks biasa.</p><p>- FontStyle.Bold - teks tebal.</p><p>- FontStyle.Italic - teks miring.</p><p>- FontStyle.Underine - teks bergaris bawah.</p><p>- FontStyle.StrikeOut - teks dengan garis tengah.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Menentukan ukuran teks.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Menentukan warna teks.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Menentukan ukuran halo (atau garis luar) di sekitar teks.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Menentukan warna halo di sekitar teks.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Ekspresi geometri yang akan digunakan untuk mengubah geometri sebelum meneruskannya ke mesin pelabelan.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Menentukan perilaku rendering untuk geometri multipart.</p><p>- MultipartMode.All - tempatkan label di dekat setiap bagian dari geometri.</p><p>- MultipartMode.Any - tempatkan satu label di dekat bagian mana pun dari geometri.</p><p>- MultipartMode.Largest - tempatkan label di dekat bagian terbesar dari geometri.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Menentukan bagaimana label ditempatkan relatif terhadap geometri.</p><p>- PointLabelPlacement - menempatkan label di dekat tengah geometri.</p><p>- LineLabelPlacement - menempatkan label di sepanjang geometri atau perimeternya.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Menentukan prioritas label jika terjadi tumpang tindih dengan label lain.<br>Label dengan prioritas lebih rendah tidak dirender. Defaultnya adalah 1000.|

## **Contoh**
### **Contoh Pelabelan Titik**
Secara default, SimpleLabeling menggambar teks di atas titik:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
Berikut cara menata gaya font:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
Untuk mengontrol posisi teks relatif terhadap fitur titik, properti penempatan harus diatur:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
Untuk skenario yang lebih maju, Anda mungkin ingin memilih pelabelan yang berbeda untuk fitur. Berikut cara melakukannya:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **Contoh Pelabelan Garis**
Secara default, SimpleLabeling menggambar label di dekat tengah garis:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
Untuk memutar label agar sejajar dengan garis, LineLabelPlacement dengan LineLabelAlignment.Parallel dapat digunakan:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
Jika Anda ingin teks mengikuti garis secara tepat, LineLabelPlacement dengan LineLabelAlignment.Curved dapat digunakan:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
Jika Anda tidak ingin teks tumpang tindih dengan garis, gunakan LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
Untuk skenario yang lebih maju, Anda mungkin ingin menyesuaikan gaya label secara dinamis berdasarkan nilai atribut fitur. Berikut cara melakukannya:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
