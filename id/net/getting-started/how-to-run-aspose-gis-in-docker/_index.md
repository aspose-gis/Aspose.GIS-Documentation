---
title: Cara Menjalankan Aspose.GIS di Docker
type: docs
description: "Jalankan Aspose.GIS dalam container Docker untuk Linux, Windows Server dan sistem operasi apa pun."
weight: 139
url: /id/net/how-to-run-aspose-gis-in-docker/
---

## Prasyarat

- Docker harus terinstal di sistem Anda. Untuk informasi tentang cara menginstal Docker di Windows atau Mac, lihat tautan di bagian "Lihat Juga".

- Visual Studio 2022.

- NET Core 3.1 SDK digunakan dalam contoh ini.


## Aplikasi Hello World

Dalam contoh ini, Anda membuat aplikasi konsol Hello World sederhana yang membuat kurva gabungan dan menyimpannya ke file. Aplikasi kemudian dapat dibangun dan dijalankan di Docker.

### Membuat Aplikasi Konsol

Untuk membuat program Hello World, ikuti langkah-langkah berikut:
1. Setelah Docker terinstal, pastikan bahwa ia menggunakan Container Linux (default). Jika perlu, pilih opsi Switch to Linux containers dari menu Docker Desktops.
1. Di Visual Studio, buat aplikasi konsol NET Core 3.1.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. Instal versi Aspose.GIS terbaru dari NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. Karena aplikasi akan dijalankan di Linux, aset native Linux yang sesuai harus terinstal. Mulai dengan image dasar dotnet core sdk 3.1 dan instal libgdiplus libc6-dev.
1. Setelah semua dependensi yang diperlukan ditambahkan, tulis program sederhana yang membuat kurva gabungan:<br>
**.NET**<br>
{{< highlight csharp >}}
using System.IO;
using Aspose.Gis.Geometries;
using Aspose.Gis;

namespace Aspose.GIS.Docker.Sample
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string path = Path.Combine("TestOut", "CreateCompoundCurve_out.shp");
            using (VectorLayer layer = VectorLayer.Create(path, Drivers.Shapefile))
            {
                var feature = layer.ConstructFeature();
                // create an 'S' letter (starts at bottom left end)
                var compoundCurve = new CompoundCurve();

                var bottom = (ILineString)Geometry.FromText("LineString (0 0, 3 0)");
                var firstArc = (ICircularString)Geometry.FromText("CircularString (3 0, 4 1, 3 2)");
                var middle = (ILineString)Geometry.FromText("LineString (3 2, 1 2)");
                var secondArc = (ICircularString)Geometry.FromText("CircularString (1 2, 0 3, 1 4)");
                var top = (ILineString)Geometry.FromText("LineString (1 4, 4 4)");

                compoundCurve.AddCurve(bottom);
                compoundCurve.AddCurve(firstArc);
                compoundCurve.AddCurve(middle);
                compoundCurve.AddCurve(secondArc);
                compoundCurve.AddCurve(top);
                feature.Geometry = compoundCurve;

                layer.Add(feature);
            }
        }
    }
}
{{< /highlight >}}

Perhatikan bahwa folder �TestOut� ditentukan sebagai folder output untuk menyimpan dokumen output. Saat menjalankan aplikasi di Docker, folder pada mesin host akan dipasang ke folder ini di container. Ini akan memungkinkan Anda untuk dengan mudah melihat output yang dihasilkan oleh Aspose.GIS di container Docker.

### Mengonfigurasi Dockerfile

Langkah selanjutnya adalah membuat dan mengonfigurasi Dockerfile.

1. Buat Dockerfile dan letakkan di samping file solusi aplikasi Anda. Pertahankan nama file ini tanpa ekstensi (default).
1. Di Dockerfile, tentukan:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

Di atas adalah Dockerfile sederhana, yang berisi instruksi berikut:

- Image SDK yang akan digunakan. Di sini itu adalah image Net 3.1. Docker akan mengunduhnya saat build dijalankan. Versi SDK ditentukan sebagai tag.
- Direktori kerja, yang ditentukan pada baris berikutnya.
- Perintah untuk menginstal libgdiplus dijalankan di container. Ini diperlukan oleh System.Drawing.Common.
- Perintah untuk menyalin semuanya ke container, menerbitkan aplikasi, dan menentukan titik masuk.

### Membangun dan Menjalankan Aplikasi di Docker

Sekarang aplikasi dapat dibangun dan dijalankan di Docker. Buka command prompt favorit Anda, ubah direktori ke folder dengan aplikasi (folder tempat file solusi dan Dockerfile ditempatkan) dan jalankan perintah berikut:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

Pertama kali perintah ini dijalankan mungkin membutuhkan waktu lebih lama, karena Docker perlu mengunduh image yang diperlukan. Setelah perintah sebelumnya selesai, jalankan perintah berikut:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

Perhatikan argumen mount, karena, seperti disebutkan sebelumnya, folder pada mesin host dipasang ke folder container, untuk dengan mudah melihat hasil eksekusi aplikasi. Jalur di Linux peka huruf besar/kecil.

{{% /alert %}}


## Contoh Lainnya

Untuk lebih banyak contoh tentang cara Anda dapat menggunakan Aspose.GIS di Docker, lihat [contoh](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## Lihat Juga

- [Instal Docker Desktop di Windows](https://docs.docker.com/docker-for-windows/install/)
- [Instal Docker Desktop di Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [Switch to Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) opsi
- Informasi tambahan tentang [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
