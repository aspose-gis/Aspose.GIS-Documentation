---
title: Hoe Aspose.GIS in Docker te draaien
type: docs
description: "Draai Aspose.GIS in een Docker container voor Linux, Windows Server en elk besturingssysteem."
weight: 139
url: /nl/net/how-to-run-aspose-gis-in-docker/
---

## Vereisten

- Docker moet op uw systeem geïnstalleerd zijn. Raadpleeg de links in de sectie "Zie ook" voor informatie over het installeren van Docker op Windows of Mac.

- Visual Studio 2022.

- NET Core 3.1 SDK wordt gebruikt in het voorbeeld.


## Hello World Applicatie

In dit voorbeeld maakt u een eenvoudige Hello World console applicatie die een compound curve creëert en opslaat in bestanden. De applicatie kan vervolgens worden gebouwd en uitgevoerd in Docker.

### Het maken van de Console Applicatie

Volg de onderstaande stappen om het Hello World programma te maken:
1. Zorg ervoor dat Docker is geïnstalleerd en Linux Containers gebruikt (standaard). Selecteer indien nodig de optie Switch to Linux containers vanuit het menu Docker Desktops.
1. Maak in Visual Studio een NET Core 3.1 console applicatie.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. Installeer de nieuwste Aspose.GIS versie van NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. Aangezien de applicatie op Linux zal draaien, moeten de juiste native Linux assets worden geïnstalleerd. Begin met het dotnet core sdk 3.1 basis image en installeer libgdiplus libc6-dev.
1. Wanneer alle vereiste afhankelijkheden zijn toegevoegd, schrijft u een eenvoudig programma dat een compound curve creëert:<br>
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

Merk op dat de �TestOut� map is gespecificeerd als een uitvoermap voor het opslaan van uitvoerdocumenten. Wanneer u de applicatie in Docker draait, wordt een map op de hostmachine gemount naar deze map in de container. Dit maakt het gemakkelijk om de output te bekijken die door Aspose.GIS in de Docker container is gegenereerd.

### Het configureren van een Dockerfile

De volgende stap is het maken en configureren van de Dockerfile.

1. Maak de Dockerfile en plaats deze naast het oplossingsbestand van uw applicatie. Houd deze bestandsnaam zonder extensie (de standaard).
1. In de Dockerfile, specificeer:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

Het bovenstaande is een eenvoudige Dockerfile, die de volgende instructies bevat:

- Het SDK image dat moet worden gebruikt. Hier is het Net 3.1 image. Docker downloadt dit wanneer de build wordt uitgevoerd. De versie van SDK wordt gespecificeerd als een tag.
- De werkmap, die in de volgende regel wordt gespecificeerd.
- De opdracht om libgdiplus te installeren wordt uitgevoerd in de container. Dit is vereist door System.Drawing.Common.
- De opdracht om alles naar container te kopiëren, de applicatie te publiceren en het entry point te specificeren.

### Het bouwen en uitvoeren van de Applicatie in Docker

Nu kan de applicatie worden gebouwd en uitgevoerd in Docker. Open uw favoriete commandoprompt, verander directory naar de map met de applicatie (map waar het oplossingsbestand en de Dockerfile zich bevinden) en voer de volgende opdracht uit:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

De eerste keer dat deze opdracht wordt uitgevoerd kan langer duren, omdat Docker de vereiste images moet downloaden. Zodra de vorige opdracht is voltooid, voert u de volgende opdracht uit:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

Let op het mount argument, want zoals eerder vermeld, wordt een map op de hostmachine gemount naar de map van de container, om gemakkelijk de resultaten van de applicatieuitvoering te zien. Paden in Linux zijn hoofdlettergevoelig.

{{% /alert %}}


## Meer voorbeelden

Voor meer voorbeelden van hoe u Aspose.GIS in Docker kunt gebruiken, zie de [voorbeelden](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## Zie ook

- [Installeer Docker Desktop op Windows](https://docs.docker.com/docker-for-windows/install/)
- [Installeer Docker Desktop op Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [Schakel over naar Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) optie
- Extra informatie over [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
