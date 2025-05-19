---
title: "Cara Menggambar Geometri pada Peta"
type: docs
url: /id/net/how-to-draw-geometry
weight: 70
---

Untuk membuat dan menampilkan objek geometri pada peta, Anda perlu memulai dengan **membuat objek geometri**. Ada dua metode yang dapat Anda gunakan:

- **Konstruktor untuk Setiap Jenis Fitur Geometri**
Metode ini melibatkan penggunaan konstruktor khusus untuk setiap jenis fitur geometri. Misalnya, untuk membuat titik, Anda akan menggunakan kode berikut:

```
Point point = new Point(40.7128, -74.006);
```

Namun, metode ini dapat menjadi rumit dan merepotkan untuk dikelola saat membuat objek kompleks seperti polylines atau koleksi. Akibatnya, pengembang mungkin perlu menambahkan banyak baris kode, menyebabkan keterbacaan kode menurun. Memastikan integritas data selama inisialisasi juga bisa jadi sulit. Misalnya, pertimbangkan contoh berikut yang membuat poligon dengan lubang di dalamnya:

```
Polygon polygon = new Polygon();

LinearRing ring = new LinearRing();
ring.AddPoint(50.02, 36.22);
ring.AddPoint(49.99, 36.26);
ring.AddPoint(49.97, 36.23);
ring.AddPoint(49.98, 36.17);
ring.AddPoint(50.02, 36.22);

LinearRing hole = new LinearRing();
hole.AddPoint(50.00, 36.22);
hole.AddPoint(49.99, 36.20);
hole.AddPoint(49.98, 36.23);
hole.AddPoint(50.00, 36.24);
hole.AddPoint(50.00, 36.22);

polygon.ExteriorRing = ring;
polygon.AddInteriorRing(hole);
```

Kerugian lain dari pendekatan ini adalah kurangnya keseragaman data untuk inisialisasi. Anda tidak dapat membuat repositori konstanta atau file dalam proyek Anda.

- **WKT (Well-Known Text)**
Metode ini melibatkan pembuatan geometri dari WKT (Well-Known Text), yang menawarkan cara standar untuk membuat geometri. Kode berikut menunjukkan cara membuat titik dan garis:

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

Meskipun pendekatan ini dapat sedikit mengurangi kinerja karena kebutuhan untuk mengurai string, ia menyederhanakan pembuatan objek yang lebih kompleks.

Anda dapat menemukan detail lebih lanjut tentang WKT di artikel berikut: "Exporting and Importing Data from/to WKT and WKB."

Menampilkan Objek Geometri pada Peta
Setelah Anda membuat objek geometri, langkah berikutnya adalah menampilkannya pada peta. Meskipun peta dapat menampilkan lapisan yang dimuat dari berbagai sumber dan format, InMemoryLayer adalah lapisan yang tidak memerlukan sumber.

**Untuk menampilkan objek geometri Anda**, Anda dapat membuat InMemoryLayer dan menambahkan objek ke dalamnya:

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

Sekarang Anda dapat **menampilkan lapisan ini pada peta dan membuat file dalam salah satu format yang didukung**, seperti SVG, dengan kode berikut:

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

Setelah Anda menambahkan lapisan dan menampilkannya pada peta, Anda dapat menyimpannya dalam salah satu format yang didukung. Dalam contoh ini, format SVG dipilih untuk menghindari potensi masalah dengan dukungan Bitmap. Penting untuk dicatat bahwa Net 6.0 memiliki dukungan Bitmap terbatas, yang dapat menghasilkan pembatasan seperti ketidakmampuan untuk merender gambar Bitmap menggunakan Blazor WebAsm di sisi klien. Oleh karena itu, saat memilih format untuk menyimpan peta Anda, penting untuk mempertimbangkan keterbatasan platform target dan memilih format yang kompatibel dengannya.

Artikel ini menjelaskan cara membuat dan menampilkan objek geometri pada peta dengan gaya default dan polos. Namun, perpustakaan Aspose menawarkan berbagai opsi penataan gaya yang dapat disesuaikan agar sesuai dengan kebutuhan Anda. Untuk menjelajahi opsi-opsi ini, kami merekomendasikan untuk berkonsultasi dengan [dokumentasi Aspose.MapRendering]( https://docs.aspose.com/gis/net/map-rendering/), yang memberikan informasi rinci tentang cara menggunakan teknik penataan gaya yang berbeda untuk meningkatkan daya tarik visual peta Anda.

**Singkatnya**, untuk membuat objek geometri pada peta, Anda dapat menggunakan konstruktor untuk setiap jenis fitur geometri atau menghasilkan geometri dari WKT. Untuk menampilkan objek, letakkan di lapisan dan tampilkan lapisan pada peta dengan gaya peta default. Simpan peta dalam format yang didukung, seperti SVG, dan gunakan perpustakaan kami untuk menjelajahi opsi penataan gaya. Selain itu, perpustakaan kami menyediakan kesempatan untuk melihat contoh selesai dengan mengklik [tautan]( https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer) yang disediakan dalam dokumentasi, yang dapat membantu Anda memahami cara menerapkan teknik ini di proyek Anda sendiri.
