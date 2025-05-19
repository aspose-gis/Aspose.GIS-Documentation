---
title: Docker'da Aspose.GIS Nasıl Çalıştırılır
type: docs
description: "Linux, Windows Server ve herhangi bir işletim sistemi için bir Docker kapsayıcısında Aspose.GIS çalıştırın."
weight: 139
url: /tr/net/how-to-run-aspose-gis-in-docker/
---

## Ön Koşullar

- Docker sisteminizde kurulu olmalıdır. Windows veya Mac'te Docker'ı nasıl kuracağınız hakkında bilgi için "Ayrıca Bkz." bölümündeki bağlantılara bakın.

- Visual Studio 2022.

- Örnekte NET Core 3.1 SDK kullanılmaktadır.


## Merhaba Dünya Uygulaması

Bu örnekte, bir bileşik eğri oluşturan ve dosyaya kaydeden basit bir Merhaba Dünya konsol uygulaması oluşturursunuz. Uygulama daha sonra Docker içinde derlenebilir ve çalıştırılabilir.

### Konsol Uygulaması Oluşturma

Merhaba Dünya programını oluşturmak için aşağıdaki adımları izleyin:
1. Docker yüklendikten sonra Linux Kapsayıcılarını (varsayılan) kullandığından emin olun. Gerekirse, Docker Masaüstü menüsünden Linux kapsayıcısına geçiş yapma seçeneğini belirleyin.
1. Visual Studio'da NET Core 3.1 konsol uygulaması oluşturun.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. NuGet'ten en son Aspose.GIS sürümünü yükleyin.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. Uygulama Linux üzerinde çalışacak olduğundan, uygun yerel Linux varlıkları kurulmalıdır. dotnet core sdk 3.1 temel görüntüsüyle başlayın ve libgdiplus libc6-dev'i kurun.
1. Gerekli tüm bağımlılıklar eklendiğinde, bir bileşik eğri oluşturan basit bir program yazın:<br>
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
                // alt köşeden başlar 'S' harfi oluşturun
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

Not edin ki �TestOut� klasörü, çıktı belgelerini kaydetmek için bir çıktı klasörü olarak belirtilmiştir. Uygulamayı Docker içinde çalıştırırken, ana bilgisayar makinesindeki bir klasör bu kapsayıcıdaki klasöre monte edilecektir. Bu, Aspose.GIS tarafından Docker kapsayıcısında oluşturulan çıktıyı kolayca görüntülemenizi sağlayacaktır.

### Bir Dockerfile Yapılandırma

Bir sonraki adım Dockerfile'ı oluşturmak ve yapılandırmaktır.

1. Dockerfile'ı oluşturun ve uygulama çözüm dosyanızın yanına yerleştirin. Bu dosyayı uzantısız tutun (varsayılan).
1. Dockerfile'da şunu belirtin:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

Yukarıdaki basit bir Dockerfile'dır ve aşağıdaki talimatları içerir:

- Kullanılacak SDK görüntüsü. Burada Net 3.1 görüntüsüdür. Docker, derleme çalıştırıldığında bunu indirecektir. SDK sürümü etiket olarak belirtilir.
- Bir sonraki satırda belirtilen çalışma dizini.
- libgdiplus'ı yüklemek için komut kapsayıcı içinde çalıştırılır. Bu, System.Drawing.Common tarafından gereklidir.
- Her şeyi kapsayıcıya kopyalama, uygulamayı yayınlama ve giriş noktasını belirleme komutu.

### Docker'da Uygulamayı Derleme ve Çalıştırma

Artık uygulama Docker içinde derlenebilir ve çalıştırılabilir. Favori komut isteminizi açın, uygulamayla (çözüm dosyasının ve Dockerfile'ın bulunduğu klasör) aynı dizine gidin ve aşağıdaki komutu çalıştırın:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

Bu komut ilk kez yürütüldüğünde biraz daha uzun sürebilir, çünkü Docker gerekli görüntüleri indirmesi gerekir. Önceki komut tamamlandıktan sonra aşağıdaki komutu çalıştırın:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}


{{% alert color="primary" %}} 

Bağlantı argüsüne dikkat edin, çünkü daha önce belirtildiği gibi, uygulama yürütme sonuçlarını kolayca görmek için bir ana bilgisayar makinesi klasörünün kapsayıcının klasörüne monte edildiği. Linux'taki yollar büyük/küçük harfe duyarlıdır.

{{% /alert %}}


## Daha Fazla Örnek

Aspose.GIS'i Docker'da nasıl kullanabileceğinize dair daha fazla örnek için [examples](https://github.com/aspose-gis/Aspose.Gis-for-.NET) adresini ziyaret edin.


## Ayrıca Bkz.

- [Windows'ta Docker Desktop Kurulumu](https://docs.docker.com/docker-for-windows/install/)
- [Mac'te Docker Desktop Kurulumu](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [Linux kapsayıcılarına geçiş yapma](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) seçeneği
- [.NET Core SDK hakkında ek bilgi](https://hub.docker.com/_/microsoft-dotnet-sdk)
