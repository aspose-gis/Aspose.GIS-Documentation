---
title: Wie man Aspose.GIS in Docker ausführt
type: docs
description: "Führen Sie Aspose.GIS in einem Docker-Container für Linux, Windows Server und jedes Betriebssystem aus."
weight: 139
url: /de/net/how-to-run-aspose-gis-in-docker/
---

## Voraussetzungen

- Docker muss auf Ihrem System installiert sein. Informationen zur Installation von Docker unter Windows oder Mac finden Sie in den Links im Abschnitt "Siehe auch".

- Visual Studio 2022.

- NET Core 3.1 SDK wird im Beispiel verwendet.


## Hello World Anwendung

In diesem Beispiel erstellen Sie eine einfache Hello World Konsolenanwendung, die eine zusammengesetzte Kurve erstellt und in Dateien speichert. Die Anwendung kann dann in Docker erstellt und ausgeführt werden.

### Erstellen der Konsolenanwendung

Um das Hello World Programm zu erstellen, folgen Sie den Schritten unten:
1. Stellen Sie sicher, dass Docker installiert ist und Linux-Container verwendet (Standard). Wählen Sie gegebenenfalls die Option "Wechseln zu Linux-Containern" aus dem Menü von Docker Desktop.
1. Erstellen Sie in Visual Studio eine NET Core 3.1 Konsolenanwendung.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. Installieren Sie die neueste Aspose.GIS Version aus NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. Da die Anwendung unter Linux ausgeführt wird, müssen die entsprechenden nativen Linux Assets installiert werden. Beginnen Sie mit dem dotnet core sdk 3.1 Basisimage und installieren Sie libgdiplus libc6-dev.
1. Wenn alle erforderlichen Abhängigkeiten hinzugefügt wurden, schreiben Sie ein einfaches Programm, das eine zusammengesetzte Kurve erstellt:<br>
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

Beachten Sie, dass der Ordner �TestOut� als Ausgabeordner für das Speichern von Ausgabedokumenten angegeben ist. Wenn die Anwendung in Docker ausgeführt wird, wird ein Ordner auf der Hostmaschine in diesen Ordner im Container gemountet. Dies ermöglicht Ihnen, die von Aspose.GIS im Docker-Container generierte Ausgabe einfach anzuzeigen.

### Konfigurieren einer Dockerfile

Der nächste Schritt besteht darin, die Dockerfile zu erstellen und zu konfigurieren.

1. Erstellen Sie die Dockerfile und platzieren Sie sie neben der Projektdatei Ihrer Anwendung. Behalten Sie diesen Dateinamen ohne Erweiterung (Standard).
1. Geben Sie in der Dockerfile Folgendes an:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

Das Obige ist eine einfache Dockerfile, die folgende Anweisungen enthält:

- Das zu verwendende SDK-Image. Hier ist es das Net 3.1 Image. Docker lädt dies herunter, wenn der Build ausgeführt wird. Die Version des SDK wird als Tag angegeben.
- Das Arbeitsverzeichnis, das in der nächsten Zeile angegeben wird.
- Der Befehl zum Installieren von libgdiplus wird im Container ausgeführt. Dies ist erforderlich für System.Drawing.Common.
- Der Befehl zum Kopieren aller Dateien in den Container, zum Veröffentlichen der Anwendung und zum Angeben des Einstiegspunkts.

### Erstellen und Ausführen der Anwendung in Docker

Jetzt kann die Anwendung in Docker erstellt und ausgeführt werden. Öffnen Sie Ihre bevorzugte Eingabeaufforderung, wechseln Sie in den Ordner mit der Anwendung (Ordner, in dem sich die Projektdatei und die Dockerfile befinden), und führen Sie den folgenden Befehl aus:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

Das erste Mal, wenn dieser Befehl ausgeführt wird, kann es länger dauern, da Docker die erforderlichen Images herunterladen muss. Sobald der vorherige Befehl abgeschlossen ist, führen Sie den folgenden Befehl aus:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

Achten Sie auf das Mount-Argument, denn wie bereits erwähnt wird ein Ordner auf der Hostmaschine in den Ordner des Containers gemountet, um die Ergebnisse der Anwendungsausführung einfach sehen zu können. Pfade unter Linux sind Groß- und Kleinschreibungsempfindlich.

{{% /alert %}}


## Weitere Beispiele

Weitere Beispiele für die Verwendung von Aspose.GIS in Docker finden Sie unter [examples](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## Siehe auch

- [Installieren Sie Docker Desktop unter Windows](https://docs.docker.com/docker-for-windows/install/)
- [Installieren Sie Docker Desktop unter Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [Wechseln zu Linux-Containern](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) Option
- Zusätzliche Informationen zum [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
