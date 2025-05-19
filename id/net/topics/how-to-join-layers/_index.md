---
title: "Cara Menggabungkan Layer menggunakan Geometri atau Atribut"
type: docs
url: /id/net/how-to-join-layers
weight: 70
---

## Ringkasan

Dalam SIG, penggabungan adalah mekanisme yang ampuh untuk menggabungkan informasi dari layer yang berbeda berdasarkan atribut umum atau hubungan spasial. Penggabungan memungkinkan Anda untuk menggabungkan data atribut dari satu layer (layer sumber) dengan layer lain (layer target) menggunakan bidang umum atau lokasi spasial. Yang pertama adalah penggabungan data berdasarkan kunci (atribut dalam tabel). Dengan menggunakan bidang umum, seperti kunci unik, Anda dapat menautkan catatan dalam satu tabel dengan catatan dalam tabel lain. Pendekatan kedua adalah penggabungan data berdasarkan lokasi (secara spasial). Kami mendukung kedua pendekatan dan menawarkan Anda kesempatan untuk menggunakannya tergantung pada kebutuhan Anda.

Mari kita asumsikan Anda telah menerima data yang menjelaskan persentase perubahan populasi untuk distrik yang berbeda, dan Anda ingin menghasilkan beberapa peta pertumbuhan populasi berdasarkan informasi ini. Sementara data populasi Anda disimpan dalam tabel di database Anda dan berbagi bidang umum dengan layer Anda, Anda dapat menggabungkan data ini ke objek geografis Anda dan memanfaatkan bidang tambahan untuk pelabelan, kategorisasi, kueri, atau menganalisis objek layer.

Biasanya, Anda melakukan penggabungan data berdasarkan nilai bidang yang ada di kedua tabel. Nama bidang tidak harus sama, tetapi jenis datanya harus sama - angka dengan angka, string dengan string, dan seterusnya. Anda dapat menjalankan penggabungan data menggunakan alat geoprocessing "Add Join". Saat menggabungkan atribut, bidang yang digabungkan ditambahkan secara dinamis ke tabel yang ada. Properti bidang seperti alias, visibilitas, dan format nomor dipertahankan saat menambahkan atau menghapus penggabungan.

## Kemampuan untuk bergabung berdasarkan bidang kunci

- Pendekatan ini memungkinkan Anda untuk **menautkan catatan dari tabel yang berbeda** berdasarkan bidang kunci umum. Anda dapat menentukan bidang kunci yang akan digunakan untuk perbandingan untuk membangun hubungan antara catatan. Ini sangat berguna ketika Anda perlu menggabungkan data berdasarkan pengenal atau atribut unik lainnya.

Menentukan metode untuk membandingkan data berdasarkan bidang kunci:

- Anda dapat mendefinisikan **metode perbandingan yang berbeda** untuk bidang kunci saat menggabungkan data. Misalnya, Anda dapat memilih untuk memiliki kecocokan persis, membandingkan berdasarkan pola, atau dalam rentang nilai. Ini memungkinkan penentuan hubungan antara catatan yang lebih tepat dan memberikan kontrol atas proses penggabungan data.

Menentukan daftar nama atribut yang akan digabungkan:

- Saat menggabungkan data, Anda dapat menentukan **atribut tertentu** yang harus digabungkan. Ini memungkinkan Anda untuk memilih hanya atribut yang diperlukan untuk penggabungan dan mengelola struktur tabel yang dihasilkan.

## Kemampuan untuk bergabung menggunakan geometri

- Pendekatan ini memungkinkan Anda untuk menautkan data berdasarkan **lokasi spasialnya**. Anda dapat mendefinisikan radius pencarian di mana objek geometris terdekat akan dicari untuk penggabungan. Ini berguna ketika Anda perlu menggabungkan data berdasarkan posisi geografisnya.

Mengontrol radius pencarian untuk menemukan objek geometris terdekat:

- Anda dapat mengontrol **radius pencarian** saat menggabungkan data berdasarkan lokasi. Dengan menentukan nilai radius, Anda menentukan jarak di mana objek terdekat akan dicari untuk penggabungan. Ini memberikan kontrol atas objek mana yang akan berpartisipasi dalam proses penggabungan data berdasarkan hubungan spasialnya.

## Proyek Demo

Untuk lebih memahami fungsionalitas pustaka kami, mari kita pertimbangkan [contoh penggunaannya](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Layers.Join). Kode ini menggambarkan cara menggabungkan layer vektor berdasarkan atribut atau geometri.

Kode yang disediakan terdiri dari dua metode, JoinByIndex() dan JoinByCoords(), yang mendemonstrasikan operasi penggabungan data menggunakan kelas LayerConstructor.

Dalam metode JoinByIndex():

- Daftar geometri dengan atribut terkait dibuat.

- Objek LayerConstructor diinisialisasi.

- Metode membuat layer vektor dan layer geometri menggunakan geometri yang disediakan.

- Layer geometri digabungkan berdasarkan pengenal unik ("Id") menggunakan metode JoinLayersById().

- Layer vektor gabungan yang dihasilkan dikembalikan.

Dalam metode JoinByCoords():

- Daftar geometri dengan atribut terkait dibuat.

- Objek LayerConstructor diinisialisasi.

- Layer geometri dibuat menggunakan geometri yang disediakan.

- Layer geometri digabungkan berdasarkan koordinat yang cocok menggunakan metode JoinLayersByCoords().

- Layer vektor gabungan yang dihasilkan dikembalikan.

Singkatnya, metode ini menunjukkan dua pendekatan berbeda untuk menggabungkan data: satu berdasarkan pengenal unik dan yang lainnya berdasarkan koordinat yang cocok. Kelas LayerConstructor memfasilitasi operasi penggabungan data ini.

## Opsi Penggabungan untuk Indeks

Kelas JoinOptions menyediakan serangkaian opsi untuk mengkonfigurasi layer bergabung. Mari selami lebih dalam setiap opsi:

- **JoinAttributeName**: Opsi ini memungkinkan Anda untuk menentukan nama atribut dari layer yang digabungkan yang nilainya akan digunakan dalam perbandingan kondisi. Ini membangun koneksi antara dua layer berdasarkan atribut ini.

- **TargetAttributeName**: Dengan opsi ini, Anda dapat menentukan nama atribut dari layer utama yang akan dibandingkan dengan atribut dari layer yang digabungkan. Ini membantu menentukan fitur yang cocok di antara layer.

- **JoinAttributeNames**: Opsi ini memungkinkan Anda untuk menentukan daftar nama atribut yang ingin Anda gabungkan. Jika daftar ini dibiarkan kosong atau disetel ke null, semua atribut dari layer yang digabungkan akan disertakan dalam operasi penggabungan. Namun, dengan memilih nama atribut tertentu, Anda dapat mengontrol atribut yang digabungkan, yang dapat berguna untuk mengoptimalkan penggunaan memori dan waktu pemrosesan.

- **ConditionComparer**: Opsi ini memungkinkan Anda untuk mendefinisikan logika khusus untuk membandingkan nilai atribut antara fitur dari dua layer. Secara default, ia menggunakan pembanding EqualityComparer.Default, yang memeriksa kesetaraan. Namun, Anda dapat memberikan pembanding khusus Anda sendiri yang mengimplementasikan IEqualityComparer untuk persyaratan perbandingan yang lebih terspesialisasi.

- **JoinedAttributesPrefix**: Opsi ini memungkinkan Anda untuk menentukan string awalan untuk nama atribut layer yang digabungkan. Nilai defaultnya adalah "joined_", yang berarti bahwa atribut yang digabungkan akan diawali dengan "joined_" di layer gabungan yang dihasilkan. Awalan ini membantu membedakan atribut yang digabungkan dari atribut asli layer utama.

Kelas JoinOptions menyediakan fleksibilitas dan kontrol atas berbagai aspek proses penggabungan layer. Anda dapat menentukan atribut untuk digabungkan, menyesuaikan logika perbandingan, dan mendefinisikan awalan untuk atribut gabungan yang dihasilkan. Opsi ini memungkinkan Anda untuk menyesuaikan operasi penggabungan sesuai dengan kebutuhan spesifik Anda dan mencapai wawasan bermakna dari layer yang digabungkan.

## Opsi Penggabungan untuk Geometri

Kelas **JoinByGeometryOptions** mewakili opsi untuk menggabungkan layer berdasarkan geometri. Mari jelajahi fungsionalitas setiap opsi:

- **Radius**: Opsi ini menentukan radius di mana geometri yang digabungkan akan dicari. Ini menentukan kedekatan di mana fitur dari layer utama akan cocok dengan fitur dari layer yang digabungkan berdasarkan hubungan spasialnya.

- **ConditionComparer**: Opsi ini memungkinkan Anda untuk mendefinisikan logika khusus untuk membandingkan nilai atribut dari fitur kedua layer. Secara default, ia menggunakan EqualityComparer. Default, yang memeriksa kesetaraan. Namun, Anda dapat memberikan pembanding khusus Anda sendiri yang mengimplementasikan IEqualityComparer untuk persyaratan perbandingan yang lebih spesifik.

- **JoinedAttributesPrefix**: Opsi ini memungkinkan Anda untuk menentukan string awalan untuk nama atribut layer yang digabungkan. Nilai defaultnya adalah "joined_", yang berarti bahwa atribut yang digabungkan akan diawali dengan "joined_" di layer gabungan yang dihasilkan. Awalan ini membantu membedakan atribut yang digabungkan dari atribut asli layer utama.

Kelas JoinByGeometryOptions menyediakan sarana untuk menyesuaikan proses menggabungkan layer berdasarkan hubungan spasialnya. Dengan menentukan radius pencarian, Anda dapat mengontrol sejauh mana geometri akan cocok. Ini memungkinkan penyetelan penggabungan berdasarkan kedekatan yang diinginkan antara fitur. Opsi untuk memberikan pembanding khusus memberi Anda fleksibilitas dalam membandingkan nilai atribut, dan opsi untuk menambahkan awalan ke atribut gabungan membantu membedakannya di layer gabungan yang dihasilkan.

Menggunakan opsi ini, Anda dapat melakukan penggabungan data sadar spasial dan memperoleh wawasan dari layer yang digabungkan yang didasarkan pada kedekatan spasial dan nilai atributnya.

## Ringkasan

Mekanisme penggabungan data dalam SIG memungkinkan untuk menggabungkan objek geometris dengan atribut masing-masing dari layer yang berbeda. Ini memberikan kemampuan untuk menganalisis dan mengekstrak informasi berdasarkan hubungan spasial dan atribut dalam data. Opsi yang tersedia memungkinkan penyesuaian proses penggabungan agar sesuai dengan kebutuhan spesifik dan analisis dalam data SIG.

Penggabungan data memfasilitasi berbagai tugas, termasuk:

- Menemukan objek yang memenuhi kriteria spasial tertentu, seperti mengidentifikasi semua bangunan dalam radius 500 meter dari titik tertentu.

- Menggabungkan data geografis untuk membuat gambaran umum yang lebih komprehensif dan informatif tentang suatu situasi.

- Menganalisis nilai atribut objek berdasarkan kondisi spasial tertentu untuk mengidentifikasi tren dan pola.

Opsi penggabungan data memungkinkan konfigurasi yang tepat dari proses pencocokan objek. Opsi ini termasuk memilih atribut untuk digabungkan, mendefinisikan logika khusus untuk membandingkan nilai atribut, dan menambahkan awalan ke nama atribut data yang digabungkan. Opsi ini memberikan fleksibilitas dan kemampuan beradaptasi pada proses penggabungan, melayani kebutuhan spesifik dan tujuan analisis data dalam SIG.

Mekanisme penggabungan data memainkan peran penting dalam mengintegrasikan dan menganalisis data geografis, menghasilkan pemahaman yang lebih komprehensif tentang sifat spasial dan atribut objek yang diselidiki.