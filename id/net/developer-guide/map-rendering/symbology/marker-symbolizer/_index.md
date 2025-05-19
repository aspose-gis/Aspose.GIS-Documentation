---
title: "Simbol Penanda"
type: docs
url: /id/net/marker-symbolizer/
weight: 10
description: Pustaka atau API GIS C# mendukung simbol penanda sederhana yang menggambar bentuk yang telah ditentukan sebelumnya dengan isian dan garis luar yang dapat disesuaikan pada geometri dari jenis apa pun seperti Titik, Garis, Permukaan.
---

## **Simbol Penanda**
Simbol penanda sederhana menggambar bentuk yang telah ditentukan sebelumnya dengan isian dan garis luar yang dapat disesuaikan. Ini adalah simbolizer default untuk geometri 0-dimensi (titik). 

Bentuk yang didukung adalah:

|![todo:image_alt_text](marker-symbolizer_1.png)|Lingkaran| |![todo:image_alt_text](marker-symbolizer_2.png)|Bintang|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Persegi| |![todo:image_alt_text](marker-symbolizer_4.png)|Silang|
|![todo:image_alt_text](marker-symbolizer_5.png)|Segitiga| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

Opsi penataan gaya yang didukung:

|**Properti**|**Deskripsi**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|Menentukan bentuk penanda.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|Menentukan ukuran bentuk penanda|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|Menentukan warna dan transparansi yang diberikan ke isian|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|Menentukan warna dan transparansi yang diberikan ke garis|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|Menentukan lebar garis|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|Menentukan cara garis dirender pada persimpangan segmen garis.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|Menentukan bagaimana pekerjaan linework simbol harus digambar.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|Menentukan array jarak yang menentukan panjang garis putus-putus dan spasi pada garis bergaris.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|Menentukan jarak dari awal garis ke awal pola garis putus-putus.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|Menentukan rotasi simbol di sekitar titik tengahnya, dalam derajat desimal. Nilai positif menunjukkan rotasi searah jarum jam, nilai negatif menunjukkan rotasi berlawanan arah jarum jam. Default adalah 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|Menentukan offset horizontal dari lokasi titik ke titik jangkar bentuk.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|Menentukan offset vertikal dari lokasi titik ke titik jangkar bentuk.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|Menentukan sisi mana dari bentuk penanda yang akan disejajarkan secara horizontal dengan lokasi titik.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|Menentukan sisi mana dari bentuk penanda yang akan disejajarkan secara vertikal dengan lokasi titik.|

### **Jenis Geometri**
` `Simbolizer dapat diterapkan ke geometri dari jenis apa pun.

|**Dimensi Geometri**|**Jenis Geometri**|**Perilaku Rendering**|
| :-: | :-: | :-: |
|**Titik**|Titik, MultiPoint|Menggambar bentuk yang berpusat di koordinat titik.|
|**Garis**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>Menggambar bentuk yang berpusat di centroid geometri</p><p> </p>|
|**Permukaan**|Poligon, CurvePolygon, MultiPolygon, MultiSurface||

Untuk GeometryCollections, perilaku rendering ditentukan secara terpisah untuk setiap geometri di dalam koleksi. Layer dengan jenis geometri Campuran mengikuti logika untuk GeometryCollections.

Gunakan MixedGeometrySymbolizer untuk membatasi simbolizer ke jenis geometri tertentu.

### **Contoh**
Secara default simbol penanda menggambar lingkaran hitam:



Berikut cara mengubah warna isian menjadi merah:



|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

Contoh lain penataan gaya dengan bentuk yang telah ditentukan sebelumnya (segitiga):



|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----
Untuk skenario yang lebih maju, Anda mungkin ingin menyesuaikan gaya penanda secara dinamis berdasarkan nilai atribut fitur. Berikut cara melakukannya:



|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
Anda mungkin juga ingin menambahkan label ke penanda Anda. Kunjungi [Contoh Pelabelan Titik](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) untuk contohnya.
