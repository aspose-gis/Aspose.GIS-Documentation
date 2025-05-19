---
title: Pemetaan Render ke Gambar SVG, PNG, JPG menggunakan Pustaka GIS C#
linktitle: "Pemetaan Render"
type: docs
url: /id/net/map-rendering/
weight: 50
description: Dengan API GIS C# Anda dapat merender peta dari Shapefile, FileGDB, GeoJSON, format KML, melakukan penataan gaya lanjutan dan menggambar peta dari format raster.
---

## **Ikhtisar Pemetaan Render**
Dengan Aspose.GIS untuk API C# .NET Anda dapat merender peta dari Shapefile, FileGDB, GeoJSON, KML atau [format file yang didukung lainnya](/gis/net/supported-file-formats/) ke SVG, PNG, JPEG, atau BMP.

Berikut adalah kode C# yang menggambarkan cara merender peta dari shapefile ke SVG menggunakan pengaturan default:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



Berikut adalah hasilnya:



![pemetaan render](map_rendering.png)

Mari kita lihat lebih dekat kodenya.

Pertama, kita membuat instans objek [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map). Ini mewakili kumpulan lapisan dari berbagai sumber yang dapat dirender. Peta memiliki ukuran di mana ia dimaksudkan untuk ditampilkan. Di sini kita mengatur peta menjadi lebar 800 piksel dan tinggi 400 piksel.

Perhatikan bahwa Map tertutup dalam pernyataan using. Ini diperlukan karena peta melacak semua sumber daya yang ditambahkan ke dalamnya, dan membuangnya saat kita selesai dengan rendering dan objek Peta dibuang.

Selanjutnya, kita menambahkan lapisan dari file ke peta. Setiap lapisan dirender di atas lapisan sebelumnya, sesuai urutan penambahan ke peta. Lihat detail lebih lanjut tentang cara membuka lapisan vektor [di sini](/gis/net/working-with-vector-layers/).

Terakhir, kita memanggil [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) untuk merender peta ke file. Kita menentukan jalur ke tempat menyimpan file hasil dan renderer yang akan digunakan. Kelas [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) berisi referensi ke semua renderer yang disertakan dengan Aspose.GIS. Misalnya, Anda dapat menentukan Renderers.Png alih-alih Renderers.Svg dalam contoh di atas untuk merender peta ke file PNG

## **Penataan Gaya Lanjutan**
Dengan API Aspose.GIS, Anda dapat menyesuaikan rendering dan gaya fitur untuk mencapai tampilan yang Anda inginkan. 

![penataan gaya lanjutan](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **Gambar raster di peta**
Dengan Aspose.GIS untuk .NET Anda dapat merender peta dari format raster.
### **Render dengan pengaturan default**
Berikut cara merender peta dari GeoTIFF ke SVG menggunakan pengaturan default:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![raster default](default_raster.png)
### **Render raster miring**
Dengan Aspose.GIS Anda dapat merender raster dengan sel raster miring.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![raster miring](skew_raster.png)
### **Render dalam referensi spasial polar**
Aspose.GIS memungkinkan Anda menggunakan referensi spasial polar pada proses rendering peta.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![negara gnomonik](gnomonic_countries.png)
