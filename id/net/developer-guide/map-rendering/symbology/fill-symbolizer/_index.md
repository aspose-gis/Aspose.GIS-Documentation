---
title: "Simbolizer Isi"
type: docs
url: /id/net/fill-symbolizer/
weight: 30
description: Pustaka API GIS C# mendukung simbolizer Isi Sederhana untuk mengisi gaya dan guratan untuk geometri 2 dimensi poligon dari jenis apa pun seperti Titik, Garis, Permukaan.
---

## **Simbolizer Isi**
Simbolizer Isi Sederhana mengisi area dengan gaya isi dan guratan yang dapat disesuaikan. Ini adalah simbolizer default untuk geometri 2 dimensi (poligon). 

Jika poligon memiliki “lubang,” mereka tidak diisi, tetapi batas di sekitar lubang digurat dengan cara biasa. “Pulau” dalam lubang diisi dan digurat, dan seterusnya.

Opsi gaya yang didukung:

|**Properti**|**Deskripsi**|
| :- | :- |
|[WarnaIsi](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Menentukan warna dan transparansi yang diberikan pada isi.|
|[GayaIsi](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Padat - Isi padat</p><p>- Tidak Ada - Jangan mengisi poligon</p><p>- Garis Horizontal - Pola garis horizontal.</p><p>- Garis Vertikal - Pola garis vertikal.</p><p>- Garis Silang - Menentukan garis horizontal dan vertikal yang bersilangan.</p><p>- Garis Diagonal Maju - Pola garis pada diagonal dari kiri atas ke kanan bawah.</p><p>- Garis Diagonal Mundur - Pola garis pada diagonal dari kanan atas ke kiri bawah.</p><p>- Garis Silang Diagonal - Pola garis diagonal menyilang.</p>|
|[WarnaGuratan](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Menentukan warna dan transparansi yang diberikan pada garis guratan.|
|[GayaGuratan](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Menentukan bagaimana linework simbol harus digambar.|
|[LebarGuratan](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Menentukan lebar garis guratan.|
|[PolaGuratan](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Menentukan array jarak yang menentukan panjang dash dan spasi bergantian dalam garis putus-putus.|
|[OffsetGuratan](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Menentukan jarak dari awal garis ke awal pola dash.|
|[SambunganGarisGuratan](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Menentukan bagaimana garis dirender pada persimpangan segmen garis.</p><p>- Miter - sudut tajam</p><p>- Bulat - sudut bulat</p><p>- Bevel - sudut diagonal</p>|
|[OffsetHorizontal](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Menentukan offset horizontal dari lokasi titik ke titik jangkar bentuk.|
|[OffsetVertikal](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Menentukan offset vertikal dari lokasi titik ke titik jangkar bentuk.|

### **Jenis Geometri**
` `Simbolizer dapat diterapkan pada geometri dari jenis apa pun.

|**Dimensi Geometri**|**Jenis Geometri**|**Perilaku Rendering**|
| :-: | :-: | :-: |
|**Titik**|Titik, MultiPoint|Menggambar persegi kecil orthogonal poligon.|
|**Garis**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Garis ditutup untuk mengisi dengan menghubungkan titik akhir ke titik awal. Hanya garis asli yang digurat.|
|**Permukaan**|Poligon, CurvePolygon, MultiPolygon, MultiSurface|Menggambar poligon.|

Untuk GeometryCollections, perilaku rendering ditentukan secara terpisah untuk setiap geometri di dalam koleksi. Layer dengan jenis geometri Campuran mengikuti logika untuk GeometryCollections.

Gunakan MixedGeometrySymbolizer untuk membatasi simbolizer ke jenis geometri tertentu.

### **Contoh**
Secara default simbolizer Isi Sederhana menggambar garis guratan hitam dan isi putih padat:



Berikut cara mengubah gaya:




|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

Anda mungkin juga ingin menambahkan label ke poligon Anda. Kunjungi [Contoh Pelabelan Garis](/gis/id/net/simple-labeling/#simplelabeling-lineslabelingexamples) untuk contoh tentang cara memberi label batas poligon atau [Contoh Pelabelan Titik](/gis/id/net/simple-labeling/#simplelabeling-pointslabelingexamples) pada contoh tentang cara memberi label pusat poligon.
