---
title: "Aliran dan Penyimpanan Jarak Jauh"
type: docs
url: /id/net/streams-and-remote-storage/
weight: 70
---

## **Bekerja dengan Format Multi-File**
Beberapa format data GIS membagi konten menjadi beberapa file. Misalnya, shapefile harus memiliki setidaknya tiga file: *.shp, *.shx, dan *.dbf. Format ini memerlukan semua file disimpan dalam struktur direktori tertentu dengan pola yang telah ditentukan untuk nama file.

Pada saat yang sama, file dapat disimpan di server jarak jauh, atau lokasi lain yang hanya dapat diakses melalui aliran. Aliran tidak memiliki informasi tentang nama file dan struktur direktori, sehingga mustahil bagi driver format file untuk menentukan cara memproses data. Aspose.GIS menyelesaikan ini dengan menyediakan mekanisme jalur abstrak.

Jalur abstrak mewakili jalur ke file (atau direktori) dalam penyimpanan seperti sistem file. Penyimpanan dapat berupa apa saja yang memiliki konsep file dan direktori, dari arsip hingga server FTP. Ini mendefinisikan bagaimana melakukan operasi file tipikal, seperti membuka file atau mencantumkan direktori.

Anda dapat menentukan cara melakukan operasi file untuk penyimpanan Anda dengan mengimplementasikan kelas yang mewarisi [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) dan menyediakan implementasi untuk metode abstraknya.
## **Showcase: Penyimpanan Blob Azure**
Repositori Contoh Aspose.GIS berisi contoh implementasi jalur abstrak khusus lengkap untuk Penyimpanan Blob Azure. Showcase ini menunjukkan cara membaca shapefile langsung dari Penyimpanan Blob Azure. Anda dapat menemukannya di sini: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **Format file tunggal (GeoJSON, KML)**
Format data GIS seperti GeoJSON dan KML dapat menyimpan semua data untuk lapisan dalam satu file. Jika Anda dapat memperoleh aliran untuk file tersebut, Anda dapat melewati implementasi jalur abstrak khusus, dan menggunakan metode [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) untuk membuat instans jalur abstrak untuk aliran.
### **Baca file dari stream**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **Tulis file ke stream**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
