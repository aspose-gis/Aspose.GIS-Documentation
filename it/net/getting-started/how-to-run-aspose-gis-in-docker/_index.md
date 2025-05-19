---
title: Come Eseguire Aspose.GIS in Docker
type: docs
description: "Esegui Aspose.GIS in un container Docker per Linux, Windows Server e qualsiasi sistema operativo."
weight: 139
url: /it/net/how-to-run-aspose-gis-in-docker/
---

## Prerequisiti

- Docker deve essere installato sul tuo sistema. Per informazioni su come installare Docker su Windows o Mac, consulta i link nella sezione "Vedi anche".

- Visual Studio 2022.

- NET Core 3.1 SDK è utilizzato nell'esempio.


## Applicazione Hello World

In questo esempio, crei una semplice applicazione console Hello World che crea una curva composta e la salva in file. L'applicazione può quindi essere compilata ed eseguita in Docker.

### Creazione dell'Applicazione Console

Per creare il programma Hello World, segui i passaggi seguenti:
1. Una volta installato Docker, assicurati che utilizzi Container Linux (predefinito). Se necessario, seleziona l'opzione Passa a container Linux dal menu Docker Desktops.
1. In Visual Studio, crea un'applicazione console NET Core 3.1.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. Installa l'ultima versione di Aspose.GIS da NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. Poiché l'applicazione verrà eseguita su Linux, è necessario installare le risorse native Linux appropriate. Inizia con l'immagine base dotnet core sdk 3.1 e installa libgdiplus libc6-dev.
1. Quando tutte le dipendenze richieste sono state aggiunte, scrivi un programma semplice che crea una curva composta:<br>
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
                // crea una lettera 'S' (inizia in basso a sinistra)
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

Nota che la cartella �TestOut� è specificata come cartella di output per il salvataggio dei documenti di output. Quando si esegue l'applicazione in Docker, una cartella sulla macchina host verrà montata in questa cartella nel container. Ciò ti consentirà di visualizzare facilmente l'output generato da Aspose.GIS nel container Docker.

### Configurazione di un Dockerfile

Il passo successivo è creare e configurare il Dockerfile.

1. Crea il Dockerfile e posizionalo accanto al file della soluzione della tua applicazione. Mantieni questo nome file senza estensione (il valore predefinito).
1. Nel Dockerfile, specifica:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

Quanto sopra è un Dockerfile semplice, che contiene le seguenti istruzioni:

- L'immagine SDK da utilizzare. Qui si tratta dell'immagine Net 3.1. Docker la scaricherà quando verrà eseguita la build. La versione dell'SDK è specificata come tag.
- La directory di lavoro, che è specificata nella riga successiva.
- Il comando per installare libgdiplus viene eseguito nel container. Questo è richiesto da System.Drawing.Common.
- Il comando per copiare tutto nel container, pubblicare l'applicazione e specificare il punto di ingresso.

### Compilazione ed Esecuzione dell'Applicazione in Docker

Ora l'applicazione può essere compilata ed eseguita in Docker. Apri il tuo prompt dei comandi preferito, cambia directory nella cartella con l'applicazione (cartella in cui si trovano il file della soluzione e il Dockerfile) ed esegui il comando seguente:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

La prima volta che questo comando viene eseguito potrebbe richiedere più tempo, poiché Docker deve scaricare le immagini richieste. Una volta completato il comando precedente, esegui il comando seguente:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

Presta attenzione all'argomento mount, perché, come menzionato in precedenza, una cartella sulla macchina host viene montata nella cartella del container, per vedere facilmente i risultati dell'esecuzione dell'applicazione. I percorsi in Linux sono sensibili alle maiuscole e minuscole.

{{% /alert %}}


## Altri Esempi

Per altri esempi di come puoi utilizzare Aspose.GIS in Docker, consulta [gli esempi](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## Vedi Anche

- [Installa Docker Desktop su Windows](https://docs.docker.com/docker-for-windows/install/)
- [Installa Docker Desktop su Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [Passa a container Linux](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) opzione
- Ulteriori informazioni su [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
