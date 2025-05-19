---
title: "Lisensi"
second_title: Aspose.GIS untuk .NET
type: docs
url: /id/net/licensing/
weight: 50
keywords: c# gis library, .net gis library
description: Evaluasi pustaka GIS C# .NET atau API dengan beberapa batasan. Terapkan Lisensi menggunakan Objek File atau Stream atau sebagai Sumber Daya Tertanam.
---

## **Evaluasi Aspose.GIS untuk .NET**
Anda dapat mengunduh Aspose.GIS untuk .NET secara gratis. Sebelum Anda menerapkan lisensi, komponen berfungsi dalam mode evaluasi. Ketika Anda membeli lisensi dan menambahkan beberapa baris kode untuk menerapkan lisensi, batasan evaluasi dihilangkan.

{{% alert color="primary" %}} Jika Anda ingin menguji Aspose.GIS tanpa batasan mode evaluasi, Anda dapat meminta Lisensi Sementara 30 hari. Silakan lihat [Dapatkan Lisensi Sementara](https://purchase.aspose.com/temporary-license). {{% /alert %}} 
### **Batasan Mode Evaluasi**
Saat dijalankan dalam mode evaluasi (tanpa lisensi diterapkan), Aspose.GIS menyediakan fungsionalitas produk penuh kecuali beberapa batasan evaluasi.

1. Tidak lebih dari **15 dokumen** dapat dibuka dan/atau dibuat **per jam**
2. Tidak lebih dari **100 fitur** dapat diakses di setiap dokumen (membaca atau menulis)
3. Tidak lebih dari **10 000 data raster** dapat diakses di setiap dokumen (membaca atau menulis).
4. Jumlah fitur maksimum yang diperbolehkan dalam dokumen untuk operasi konversi adalah **50**

Saat dijalankan dalam mode berlisensi, Anda dapat memproses jumlah dokumen dan fitur tanpa batas.
## **Menerapkan Lisensi**
Lisensi adalah file XML teks biasa yang berisi detail seperti nama produk, jumlah pengembang yang dilisensikan, tanggal kedaluwarsa berlangganan dan sebagainya. File tersebut ditandatangani secara digital, jadi jangan ubah file tersebut. Bahkan penambahan jeda baris tambahan ke dalam file akan membuatnya tidak valid.

Anda perlu mengatur lisensi sebelum menggunakan Aspose.GIS jika Anda ingin menghindari batasan evaluasinya. Hanya diperlukan untuk mengatur lisensi sekali per aplikasi (atau proses).
### **Mengatur Lisensi di Aspose.GIS untuk .NET**
Di Aspose.GIS, lisensi dapat dimuat dari file, stream atau sumber daya tertanam. Aspose.GIS mencoba menemukan lisensi di lokasi berikut:

- Jalur eksplisit
- Folder yang berisi Aspose.GIS.dll
- Folder yang berisi assembly yang memanggil Aspose.GIS.dll
- Folder yang berisi assembly entri (file .exe Anda)
- Sumber daya tertanam dalam assembly yang memanggil Aspose.GIS.dll. Ada dua metode umum untuk mengatur lisensi, yang dibahas di bawah ini:
### **Terapkan Lisensi menggunakan Objek File atau Stream**
Cara termudah untuk mengatur lisensi adalah dengan menempatkan file lisensi di folder yang sama dengan Aspose.GIS.dll dan menentukan hanya nama file tanpa jalurnya.

{{< highlight java >}}

 // Instansiasi instance lisensi dan atur file lisensi melalui jalurnya

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // Instansiasi instance lisensi dan atur lisensi melalui stream

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}

Ketika Anda memanggil metode SetLicense, nama lisensi harus sama dengan nama file lisensi Anda. Misalnya, Anda dapat mengubah nama file lisensi menjadi "Aspose.GIS.lic.xml". Kemudian dalam kode Anda, Anda harus menggunakan nama lisensi yang dimodifikasi (yaitu Aspose.GIS.lic.xml) untuk metode SetLicense.

## **Menyertakan File Lisensi sebagai Sumber Daya Tertanam**
Cara rapi lainnya untuk mengemas lisensi dengan aplikasi Anda dan memastikan bahwa itu tidak akan hilang adalah dengan menyertakannya sebagai sumber daya tertanam ke dalam salah satu assembly yang memanggil dll komponen (termasuk dalam Aspose.GIS). Untuk menyertakan file lisensi sebagai sumber daya tertanam, lakukan langkah-langkah berikut:

- Di Visual Studio, sertakan file lisensi (.lic) ke dalam proyek menggunakan menu File | Tambahkan Item Yang Ada...
- Pilih file di Solution Explorer dan atur Build Action menjadi Embedded Resource di jendela Properties
- Untuk mengakses lisensi yang disematkan dalam assembly (sebagai sumber daya tertanam), tidak perlu memanggil metode GetExecutingAssembly dan GetManifestResourceStream dari kelas System.Reflection.Assembly dari Microsoft .NET Framework. Semua yang perlu dilakukan adalah menambahkan file lisensi sebagai sumber daya tertanam ke proyek Anda dan meneruskan nama file lisensi ke metode License.SetLicense. Kelas Lisensi akan secara otomatis menemukan file lisensi dalam sumber daya tertanam.

Silakan tinjau contoh di bawah ini untuk memahami metode pengaturan lisensi (tertanam) ini dalam aplikasi Anda.

{{< highlight java >}}

 // Instansiasi kelas Lisensi

Aspose.Gis.License license = new Aspose.Gis.License();

// Lewatkan hanya nama file lisensi yang disematkan dalam assembly

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **Menerapkan Kunci Terukur**
[Aspose.Gis untuk .NET API](/gis/net/) memungkinkan pengembang menerapkan kunci terukur. Ini adalah mekanisme lisensi baru. Mekanisme lisensi baru akan digunakan bersama dengan metode lisensi yang ada. Pelanggan yang ingin ditagih berdasarkan penggunaan fitur API dapat menggunakan lisensi terukur. Untuk detail lebih lanjut, silakan lihat bagian [FAQ Lisensi Terukur](https://purchase.aspose.com/faqs/licensing/metered).

Kelas **Metered** baru telah diperkenalkan untuk menerapkan kunci terukur. Berikut adalah contoh kode yang menunjukkan cara mengatur kunci publik dan pribadi terukur.

**[C#]**

{{< highlight csharp >}}

 // atur kunci publik dan pribadi terukur
 
Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();
 
// Akses properti setMeteredKey dan lewati kunci publik dan pribadi sebagai parameter
 
metered.SetMeteredKey("*****", "*****");
 
// LAKUKAN PEMROSESAN
 
// dapatkan jumlah data terukur
 
decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();
 
// Tampilkan informasi
 
Console.WriteLine("Jumlah Terkonsumsi : " + amount.ToString());

{{< /highlight >}}
