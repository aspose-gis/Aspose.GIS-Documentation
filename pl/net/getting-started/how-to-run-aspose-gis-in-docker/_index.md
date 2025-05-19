---
title: Jak uruchomić Aspose.GIS w Dockerze
type: docs
description: "Uruchom Aspose.GIS w kontenerze Dockera dla systemów Linux, Windows Server i dowolnego systemu operacyjnego."
weight: 139
url: /pl/net/how-to-run-aspose-gis-in-docker/
---

## Wymagania wstępne

- Docker musi być zainstalowany w Twoim systemie. Aby uzyskać informacje o sposobie instalacji Dockera na Windows lub Mac, zapoznaj się z linkami w sekcji „Zobacz również”.

- Visual Studio 2022.

- NET Core 3.1 SDK jest używane w przykładzie.


## Aplikacja Hello World

W tym przykładzie tworzysz prostą aplikację konsolową Hello World, która tworzy krzywą złożoną i zapisuje ją w plikach. Następnie aplikację można skompilować i uruchomić w Dockerze.

### Tworzenie aplikacji konsolowej

Aby utworzyć program Hello World, wykonaj następujące kroki:
1. Po zainstalowaniu Dockera upewnij się, że używa on kontenerów Linux (domyślnie). W razie potrzeby wybierz opcję Przejdź do kontenerów Linux z menu Docker Desktop.
1. W Visual Studio utwórz aplikację konsolową NET Core 3.1.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. Zainstaluj najnowszą wersję Aspose.GIS z NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. Ponieważ aplikacja będzie uruchamiana na Linuxie, należy zainstalować odpowiednie natywne zasoby Linux. Zacznij od obrazu podstawowego dotnet core sdk 3.1 i zainstaluj libgdiplus libc6-dev.
1. Po dodaniu wszystkich wymaganych zależności napisz prosty program, który tworzy krzywą złożoną:<br>
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

Zwróć uwagę, że folder �TestOut� jest określony jako folder wyjściowy do zapisywania dokumentów wynikowych. Podczas uruchamiania aplikacji w Dockerze folder na maszynie hosta zostanie zamontowany do tego folderu w kontenerze. Umożliwi to łatwe przeglądanie wyników generowanych przez Aspose.GIS w kontenerze Dockera.

### Konfigurowanie pliku Dockerfile

Następnym krokiem jest utworzenie i skonfigurowanie pliku Dockerfile.

1. Utwórz plik Dockerfile i umieść go obok pliku rozwiązania aplikacji. Zachowaj tę nazwę pliku bez rozszerzenia (domyślnie).
1. W pliku Dockerfile określ:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

Powyższy to prosty plik Dockerfile, który zawiera następujące instrukcje:

- Obraz SDK do użycia. Tutaj jest to obraz Net 3.1. Docker pobierze go podczas uruchomienia kompilacji. Wersja SDK jest określona jako tag.
- Katalog roboczy, który jest określony w następnym wierszu.
- Komenda instalująca libgdiplus jest wykonywana w kontenerze. Jest to wymagane przez System.Drawing.Common.
- Komenda kopiująca wszystko do kontenera, publikująca aplikację i określająca punkt wejścia.

### Budowanie i uruchamianie aplikacji w Dockerze

Teraz aplikację można skompilować i uruchomić w Dockerze. Otwórz swoje ulubione okno poleceń, przejdź do folderu z aplikacją (folder, w którym znajdują się plik rozwiązania i plik Dockerfile) i uruchom następującą komendę:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

Pierwsze wykonanie tej komendy może potrwać dłużej, ponieważ Docker musi pobrać wymagane obrazy. Po zakończeniu poprzedniej komendy uruchom następującą komendę:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

Zwróć uwagę na argument mount, ponieważ, jak wspomniano wcześniej, folder na maszynie hosta jest zamontowany do folderu kontenera, aby łatwo zobaczyć wyniki wykonania aplikacji. Ścieżki w Linuxie są wrażliwe na wielkość liter.

{{% /alert %}}


## Więcej przykładów

Aby uzyskać więcej przykładów sposobu użycia Aspose.GIS w Dockerze, zobacz [przykłady](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## Zobacz również

- [Instalacja Dockera Desktop na Windows](https://docs.docker.com/docker-for-windows/install/)
- [Instalacja Dockera Desktop na Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- Opcja [Przejdź do kontenerów Linux](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)
- Dodatkowe informacje na temat [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
