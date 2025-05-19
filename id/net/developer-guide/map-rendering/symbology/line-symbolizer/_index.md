---
title: "Simbol Garis"
type: docs
url: /id/net/line-symbolizer/
weight: 20
description: Pustaka atau API GIS C# mendukung simbol Garis Sederhana untuk geometri 1 dimensi garis dan dapat diterapkan pada geometri dari jenis apa pun seperti Titik, Garis, Permukaan.
---

## **Simbol Garis**
Simbol Garis Sederhana menggambar garis dengan gaya yang dapat disesuaikan. Ini adalah symbolizer default untuk geometri 1 dimensi (garis). 

Opsi penataan gaya yang didukung:

|**Properti**|**Deskripsi**|
| :- | :- |
|[Warna](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|Menentukan warna dan transparansi yang diberikan ke garis.|
|[Lebar](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|Menentukan lebar garis|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|Menentukan bagaimana garis dirender di persimpangan segmen garis.|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|Menentukan bagaimana linework simbol harus digambar.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|Menentukan array jarak yang menentukan panjang garis putus-putus dan spasi pada garis bergaris.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|Menentukan jarak dari awal garis ke awal pola dash.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>Menentukan bagaimana garis dirender di ujungnya.</p><p>- Butt - tepi persegi tajam</p><p>- Round - tepi bulat</p><p>- Square - tepi persegi panjang sedikit memanjang</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|Menentukan offset dari garis asli. Untuk jarak positif, offset akan berada di sisi kiri garis input (relatif terhadap arah garis). Untuk jarak negatif, itu akan berada di sisi kanan.|

### **Jenis Geometri**
` `Symbolizer dapat diterapkan ke geometri dari jenis apa pun.

|**Dimensi Geometri**|**Jenis Geometri**|**Perilaku Rendering**|
| :-: | :-: | :-: |
|**Titik**|Titik, MultiPoint|Menggambar garis dengan panjang kecil dengan orientasi horizontal yang dipusatkan pada titik, dengan dua ujung tutup.|
|**Garis**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Menggambar garis.|
|**Permukaan**|Poligon, CurvePolygon, MultiPolygon, MultiSurface|Garis luar geometri digunakan sebagai string garis (tanpa penutup ujung)|

Untuk GeometryCollections, perilaku rendering ditentukan secara terpisah untuk setiap geometri di dalam koleksi. Layer dengan jenis geometri Campuran mengikuti logika untuk GeometryCollections.

Gunakan MixedGeometrySymbolizer untuk membatasi symbolizer ke jenis geometri tertentu.

### **Contoh**
Secara default, symbolizer garis menggambar garis hitam:



Berikut cara mengubah warna garis menjadi biru:



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

Untuk skenario yang lebih maju, Anda mungkin ingin menyesuaikan gaya garis secara dinamis berdasarkan nilai atribut fitur. Berikut cara melakukannya:



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |



Anda mungkin juga ingin menambahkan label ke garis Anda. Kunjungi [Contoh Pelabelan Garis](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) untuk contohnya.
