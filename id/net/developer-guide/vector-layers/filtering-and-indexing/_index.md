---
title: Memfilter dan Mengindeks Lapisan Vektor GIS di C#
linktitle: Memfilter dan Mengindeks
second_title: Aspose.GIS untuk .NET
type: docs
url: /id/net/filtering-and-indexing/
weight: 30
description: Dengan Pustaka atau API GIS C# .NET, Anda dapat memfilter lapisan vektor GIS berdasarkan nilai atribut atau batas spasial. Anda juga dapat menggunakan indeks untuk mempercepat pemfilteran dan kueri spasial.
---

Dengan Aspose.GIS untuk .NET Anda dapat memfilter lapisan berdasarkan nilai atribut atau batas spasial. Anda juga dapat menggunakan indeks untuk mempercepat pemfilteran dan kueri spasial.
## **Indeks Atribut**
### **Filter Tanpa Indeks**
Berikut cara memfilter lapisan berdasarkan nilai atribut:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **Filter Dengan Indeks**
Kode di atas baik-baik saja selama lapisan hanya difilter sekali. Tetapi, jika lapisan kemungkinan akan dikueri beberapa kali, kita dapat memperoleh manfaat dari indeks atribut. Dibutuhkan waktu untuk membangun indeks atribut, tetapi itu dapat digunakan kembali berkali-kali untuk mempercepat pemfilteran.

Contoh berikut menggunakan file indeks atribut untuk mempercepat pemfilteran lapisan berdasarkan nilai atribut:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **Simpan Fitur yang Difilter**
Fitur yang difilter dapat disimpan ke dalam lapisan:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **Render Fitur yang Difilter**
Dimungkinkan juga untuk merender fitur yang difilter. Contoh berikut menggunakan indeks atribut untuk dengan cepat memilih semua fitur dengan populasi lebih besar dari 2000 dan menambahkannya ke peta:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **Indeks Spasial**
Indeks spasial digunakan untuk mempercepat kueri spasial. Sama seperti indeks atribut, indeks spasial digunakan kembali setelah dibuat.
### **Temukan Fitur Terdekat ke Titik**
Berikut cara menggunakan indeks spasial untuk mempercepat pencarian fitur terdekat dengan titik tertentu:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **Pilih Fitur yang Berpotongan Dengan Geometri**
Contoh berikut menggunakan indeks spasial untuk mempercepat pemilihan fitur yang berpotongan dengan geometri:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
