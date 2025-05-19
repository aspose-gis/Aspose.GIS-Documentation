---
title: Simbologi - API GIS C#
linktitle: "Simbologi"
type: docs
url: /id/symbology/
weight: 10
description: Pustaka atau API GIS C# mendukung simbolisasi untuk menggambar geometri fitur seperti Marker, Garis, Isi dan menggabungkan simbolisasi untuk membuat visualisasi yang lebih kompleks.
---

Simbolisasi adalah cara untuk menggambar geometri fitur pada peta.

|** **|**Simbolisasi**|**Kelas API**|**Deskripsi**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**Marker**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Menggambar bentuk yang telah ditentukan sebelumnya dengan isi dan garis luar yang dapat disesuaikan.|
|![todo:image_alt_text](symbology_2.png)|**Garis**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Menggambar garis dengan gaya yang dapat disesuaikan.|
|![todo:image_alt_text](symbology_3.png)|**Isi**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Mengisi poligon atau area yang dibatasi oleh garis dengan isi dan guratan yang dapat disesuaikan.|
Selain simbolisasi yang melakukan penggambaran aktual, ada sejumlah simbolisasi lain yang memungkinkan penggabungan simbolisasi lain untuk membuat visualisasi yang lebih kompleks.

|**Simbolisasi**|**Kelas API**|**Deskripsi**|
| :- | :- | :- |
|**Simbolisasi Berlapis**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Menggambar fitur dengan beberapa simbolisasi di atas satu sama lain|
|**Simbolisasi Geometri Campuran**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Menggambar fitur dari lapisan yang berisi geometri jenis campuran dengan simbolisasi tertentu untuk setiap jenis geometri|
|**Simbolisasi Berbasis Aturan**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Memilih simbolisasi untuk diterapkan ke fitur berdasarkan aturan yang ditentukan oleh pengguna.|
|**Simbolisasi Klaster Marker**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|Menggambar pengelompokan marker, pengelompokan item ini.|
|**Simbolisasi Generator Geometri**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Memungkinkan untuk mengganti geometri fitur sebelum rendering.|
|**Simbolisasi Null**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|Tidak menggambar apa pun. Berguna saat dikombinasikan dengan simbolisasi lain, seperti simbolisasi berbasis aturan.|
