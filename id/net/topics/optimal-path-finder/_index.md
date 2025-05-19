---
title: "Optimal Path Finder"
type: docs
url: /id/net/optimal-path-finder
weight: 70
---

## Summary

Pencarian jalur terpendek pada jaringan jalan adalah proses analisis yang bertujuan untuk menentukan cara paling efisien untuk bepergian antar titik di peta. Alat ini dapat berguna untuk membuat rute optimal dengan beberapa perhentian atau mengukur jarak dan waktu tempuh antara lokasi yang berbeda. Dengan setiap panggilan, teknologi kami dapat menemukan rute optimal untuk satu atau beberapa kendaraan. Misalnya, ia dapat membantu pengemudi menemukan rute optimal untuk mengirimkan barang atau menentukan jarak perjalanan optimal dari rumah ke tempat kerja bagi penumpang yang berbeda.

## Algorithm Capabilities

Pustaka kami menyediakan kemampuan untuk membangun **rute paling optimal antara dua titik** di peta. Ia memiliki fitur utama berikut:

1. Pencarian jalur optimal di peta, dengan mempertimbangkan jejak dan rintangan: Kami memperhitungkan tidak hanya jalan tetapi juga jalur off-road seperti jejak, trotoar pejalan kaki, dan rintangan yang dapat memengaruhi pilihan jalur optimal.

2. Pencarian jalur optimal hanya di jalan: Jika Anda perlu menemukan rute secara eksklusif di jalan, kami menyediakan kemampuan ini. Ini berguna, misalnya, untuk kendaraan yang dibatasi untuk bepergian hanya di jalan.

3. Menetapkan kecepatan berbeda untuk jalan: Kami memiliki kemampuan untuk menetapkan kecepatan berbeda ke jalan yang berbeda. Misalnya, kecepatan lebih tinggi dapat ditetapkan untuk jalan raya utama dan kecepatan lebih rendah untuk jalur sempit.

4. Menetapkan rintangan persegi panjang: Anda dapat menentukan rintangan persegi panjang di peta yang perlu diperhitungkan saat membangun jalur optimal. Ini berguna ketika ada rintangan yang diketahui seperti bangunan atau danau (aproksimasinya).

5. Membatasi radius pencarian untuk jalan: Anda dapat membatasi radius pencarian untuk jalan guna mengurangi waktu pencarian dan hanya fokus pada area tertentu.

6. Kontrol kinerja dan akurasi: Kami menyediakan kemampuan untuk mengontrol kinerja dan akurasi algoritma. Anda dapat menyetelnya untuk mencapai keseimbangan yang diinginkan antara kecepatan pencarian dan akurasi konstruksi rute.

Selanjutnya, kami akan memberikan deskripsi lebih rinci tentang masing-masing fitur ini dan memeriksa contoh aplikasinya.

## Approach to Solution

Meskipun menemukan jalur adalah tugas yang tidak sepele, ada beberapa algoritma yang baik dan andal yang diakui dalam komunitas pengembangan.

Dalam implementasi kami, kami menggunakan algoritma Lee yang dimodifikasi. Kami memiliki grid sel pada bidang tersebut. Dari titik awal, gelombang menyebar ke 8 arah (termasuk diagonal) ke sel tetangga, menghitung waktu yang dibutuhkan untuk mencapai masing-masingnya. Sel tetangga mungkin berisi rintangan atau jalan. Jalan dapat memiliki koefisien kecepatan yang berbeda. Dengan demikian, kami "menandai" grid kami dengan waktu yang dibutuhkan untuk mencapai setiap sel dari sel awal dalam radius tertentu atau hingga mencapai titik tujuan. Jika kita mencapai titik tujuan, kita membangun jalur balik menggunakan grid kami.

Untuk menentukan rute optimal di jaringan jalan, beberapa langkah perlu diambil. Pertama, Anda perlu mendefinisikan jalan dan menentukan kecepatan gerakan pada masing-masingnya. Anda juga harus mempertimbangkan keberadaan rintangan buatan dan alami yang dapat memengaruhi lintasan jalur. Setelah itu, Anda perlu menentukan titik awal dan tujuan pencarian. Setelah langkah-langkah persiapan ini selesai, Anda dapat melanjutkan ke penemuan jalur sebenarnya. Hasilnya akan berupa jalur yang direpresentasikan, misalnya, sebagai daftar koordinat titik.

Penting untuk dicatat bahwa jalur optimal dapat bergantung pada moda transportasi yang dipilih, karena kecepatan gerakan dan set rintangan dapat bervariasi. Oleh karena itu, set jalan dan rintangan yang berbeda harus digunakan untuk setiap jenis transportasi saat mencari jalur optimal.

## Demo Project on GitHub

Untuk lebih memahami fungsionalitas pustaka kami, mari kita pertimbangkan [contoh penggunaannya](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths). Kode ini mengilustrasikan cara menyiapkan jalan dan rintangan dalam algoritma penemuan jalur dan menemukan rute optimal.

Contohnya terdiri dari langkah-langkah berikut:

1. Membuat daftar informasi jalan (RoadInfo), yang mencakup informasi tentang segmen jalan (Segment) dan kecepatan gerakan (Velocity).
2. Menambahkan jalan cepat ke daftar.
3. Menambahkan jalan lingkar lambat ke daftar.
4. Membuat generator lapisan jalur (WayLayerGenerator) dan menambahkan jalan ke generator.
5. Mencari beberapa jalur dari titik awal (startPoint) ke titik tujuan (goalPoint01, goalPoint02, goalPoint03) menggunakan radius yang ditentukan (radius).
6. Menyiapkan lapisan jalan (roadsLayer) untuk ditampilkan di peta dan menambahkan objek jalan.
7. Menyiapkan lapisan jalur (wayLayer) untuk ditampilkan di peta dan membuat objek geometris untuk setiap jalur yang ditemukan.
8. [Menampilkan peta](https://docs.aspose.com/gis/net/how-to-draw-geometry/) menggunakan fungsi ShowMap, menyimpan peta di jalur yang ditentukan.

Kode ini membangun dan menampilkan jalur jalan di peta untuk titik tertentu menggunakan informasi jalan dan generator lapisan jalur.

## Search Options

Penemuan jalur dilakukan menggunakan kelas **WayLayerGenerator** yang terletak di namespace Aspose.Gis.GeoTools.WayAnalyzer.

Kelas WayLayerGenerator memiliki metode **FindTheWay** untuk menemukan jalur dari titik awal ke target. Untuk membuat instance kelas WayLayerGenerator, kita meneruskan WayOptions sebagai parameter (semua parameter bersifat opsional):

- StartPoint: Titik awal

- GoalPoint: Titik target

- Radius: Radius pencarian

- Scale: Skala grid

- IsMoveOnlyRoad: Apakah akan mencari jalur hanya di jalan

Fitur penting di sini adalah parameter Scale. Jika ditentukan dalam konstruktor, kita memperbaiki skala konstan untuk pencarian berikutnya. Jika parameter Scale tidak disetel tetapi StartPoint dan GoalPoint disetel, kita menghitung skala sebagai jarak antara titik awal dan tujuan dibagi 100. Dalam semua kasus lain, nilai default Scale adalah 1. Untuk pengguna berpengalaman, lebih baik menyetel Scale atau menyetel StartPoint dan GoalPoint secara langsung untuk merepresentasikan jalan dan rintangan pada grid dengan paling efisien (terutama jika ada banyak dari mereka).

Untuk menggunakan metode FindTheWay, kita perlu menentukan titik awal dan tujuan. Kita juga dapat mengatur radius pencarian (jarak ke mana gelombang menyebar). Secara default, radius dihitung sebagai jarak antara titik awal dan tujuan dikalikan 3. Titik awal dan tujuan dapat dekat atau sangat jauh satu sama lain, jadi berdasarkan jarak antar keduanya, kita menghitung skala grid kita. Jika skala saat ini tidak cocok dengan yang sebelumnya, kita menghitung ulang grid. Skala dapat diperbaiki menggunakan parameter Scale. Dalam hal ini, itu tidak dihitung, dan grid tidak dihitung ulang.

Sebelum memulai pencarian, kita perlu mendefinisikan peta jalan dan rintangan menggunakan metode AddRoad dan AddBlock yang sesuai dari kelas WayLayerGenerator.

Untuk **metode AddRoad**, kita perlu menentukan:

- startPoint: Titik awal jalan

- endPoint: Titik akhir jalan

- velocity: Kecepatan gerakan di jalan

Untuk **metode AddBlock**, kita perlu menentukan:

- x: Koordinat x sudut kiri atas blok

- y: Koordinat y sudut kiri atas blok

- sizeX: Ukuran pada sumbu x

- sizeY: Ukuran pada sumbu y

Metode ini memungkinkan kita untuk mendefinisikan peta jalan dan rintangan sebelum memulai proses penemuan jalur.

## Code examples

Berikut adalah beberapa contoh kode yang mengilustrasikan cara menyiapkan jalan dan rintangan dalam algoritma penemuan jalur dan menemukan rute optimal.

Contoh 1: Menemukan jalur antara titik awal dan tujuan.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Contoh 2**: Menyetel parameter skala dan memiliki koordinat negatif untuk titik tersebut.

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Contoh 3**: Menyetel parameter IsMoveOnlyRoad dan radius pencarian.

```
WayOptions mapGeneratorOptions = new WayOptions();
mapGeneratorOptions.IsMoveOnlyRoad = true;
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddRoad(new Point(100, 100), new Point(140, 150), 10);
generator.AddRoad(new Point(140, 150), new Point(190, 100), 10);
Point startPoint = new Point(100, 100);
Point goalPoint = new Point(190, 100);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 100);
```

**Contoh 4**: Menyetel parameter skala untuk pencarian yang lebih cepat.

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**Contoh 5**: Contoh pencarian berganda.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddBlock(200, 1700, 1500, 100, 0);
generator.AddBlock(1700, 200, 100, 1600, 0);
generator.AddBlock(200, 200, 1500, 100, 0);
generator.AddRoad(new Point(1000, 1150), new Point(200, 600), 10);
generator.AddRoad(new Point(50, 450), new Point(150, 1850), 10);

Point startPoint = new Point(1000, 1000);
Point goalPoint = new Point(1900, 1000);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 3500);

Point startPoint = new Point(50, 50);
Point goalPoint = new Point(70, 70);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

Contoh kode ini membangun dan menampilkan jalur jalan di peta untuk titik tertentu, menggunakan informasi jalan dan generator lapisan jalur.

**Singkatnya**, pencari jalur optimal adalah alat yang ampuh untuk menganalisis jaringan jalan dan menentukan rute paling efisien antar titik di peta. Ia memperhitungkan berbagai faktor seperti jenis jalan, rintangan, dan kecepatan berbeda untuk menghitung jalur optimal. Dengan kemampuan untuk mencari jalur di jalan dan jalur off-road, serta mengontrol radius pencarian dan menyesuaikan kinerja dan akurasi, algoritma ini menyediakan solusi serbaguna untuk optimisasi rute. Dengan mempertimbangkan moda transportasi yang berbeda dan menyesuaikan set jalan dan rintangan sesuai dengan itu, ia dapat digunakan dalam berbagai skenario seperti perencanaan pengiriman atau optimisasi perjalanan. Contoh kode dan penjelasan yang diberikan menunjukkan kemampuan algoritma dan langkah-langkah yang terlibat dalam menggunakannya. Pada akhirnya, pencari jalur optimal menawarkan cara yang kuat untuk menemukan rute paling efisien dan meningkatkan navigasi di jaringan jalan.