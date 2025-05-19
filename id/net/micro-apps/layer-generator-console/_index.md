---
title: "Aplikasi Konsol Pembuat Layer"
type: docs
url: /id/net/layer-generator-console
weight: 50
---

## Ringkasan

Aplikasi konsol ini dirancang untuk menghasilkan objek geometris dari berbagai jenis dan menyimpannya dalam format yang dipilih. Aplikasi ini memungkinkan Anda membuat titik, poligon, dan polyline, menentukan jumlah objek yang akan dibuat, dan memilih format output untuk penyimpanan.

## Penggunaan

Sintaks perintah:

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

Argumen:

```
-t, --type: Jenis geometri. Salah satu dari berikut: Point, Polygon, Polyline.

-c, --count: Wajib. Jumlah objek yang akan dibuat. Contoh: 15.

-f, --fileName: Wajib. Nama file untuk penyimpanan. Tentukan nama file dan ekstensi. Contoh: test.json.

-o, --outputFormat: Format output. Lihat format file yang didukung di sini.

--help: Menampilkan informasi bantuan untuk perintah tersebut.

--version: Menampilkan informasi versi aplikasi.
```

Contoh perintah untuk membuat 15 titik acak dan menyimpannya ke file dengan format "test.json":

```
app.exe -t Point -c 15 -f test.json -o json
```

## Instalasi dan Lisensi

Jika Anda ingin menggunakan aplikasi ini, Anda perlu mengunduh arsipnya dan mengekstraknya. Silakan ikuti tautan di bawah ini.

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

Meskipun Aplikasi Konsol Pembuat Layer Aspose.GIS gratis, Aspose.GIS .NET dilisensikan seperti biasa, jadi Anda dapat menggunakan kembali lisensi Anda melalui aplikasi atau mengevaluasi aplikasi menggunakan Aspose.GIS .NET dalam mode percobaan atau meminta Lisensi Sementara.

## Kesimpulan

Generator Objek Geometris adalah aplikasi konsol yang nyaman yang membantu Anda membuat sampel geometri dari berbagai jenis dan menyimpannya dalam format yang diinginkan. Ini adalah alat yang berguna untuk bekerja dengan data geospasial dan mengembangkan sistem informasi geografis.
