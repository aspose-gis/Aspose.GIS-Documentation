---
title: Comment exécuter Aspose.GIS dans Docker
type: docs
description: "Exécuter Aspose.GIS dans un conteneur Docker pour Linux, Windows Server et tout OS."
weight: 139
url: /fr/net/how-to-run-aspose-gis-in-docker/
---

## Prérequis

- Docker doit être installé sur votre système. Pour plus d'informations sur l'installation de Docker sous Windows ou Mac, reportez-vous aux liens dans la section "Voir également".

- Visual Studio 2022.

- Le SDK NET Core 3.1 est utilisé dans l'exemple.


## Application Hello World

Dans cet exemple, vous créez une simple application console Hello World qui crée une courbe composée et l'enregistre dans des fichiers. L'application peut ensuite être construite et exécutée dans Docker.

### Création de l'application Console

Pour créer le programme Hello World, suivez les étapes ci-dessous :
1. Une fois Docker installé, assurez-vous qu'il utilise des conteneurs Linux (par défaut). Si nécessaire, sélectionnez l'option Basculer vers les conteneurs Linux dans le menu Docker Desktops.
1. Dans Visual Studio, créez une application console NET Core 3.1.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. Installez la dernière version d'Aspose.GIS à partir de NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. Étant donné que l'application sera exécutée sur Linux, les actifs natifs Linux appropriés doivent être installés. Commencez par l'image de base du sdk dotnet core 3.1 et installez libgdiplus libc6-dev.
1. Lorsque toutes les dépendances requises sont ajoutées, écrivez un programme simple qui crée une courbe composée :<br>
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

Notez que le dossier �TestOut� est spécifié comme dossier de sortie pour l'enregistrement des documents de sortie. Lors de l'exécution de l'application dans Docker, un dossier sur la machine hôte sera monté vers ce dossier dans le conteneur. Cela vous permettra de visualiser facilement la sortie générée par Aspose.GIS dans le conteneur Docker.

### Configuration d'un fichier Dockerfile

La prochaine étape consiste à créer et configurer le fichier Dockerfile.

1. Créez le fichier Dockerfile et placez-le à côté du fichier solution de votre application. Conservez ce nom de fichier sans extension (par défaut).
1. Dans le fichier Dockerfile, spécifiez :

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

Ce qui précède est un fichier Dockerfile simple, qui contient les instructions suivantes :

- L'image SDK à utiliser. Ici, c'est l'image Net 3.1. Docker la téléchargera lorsque la construction sera exécutée. La version du SDK est spécifiée sous forme d'étiquette.
- Le répertoire de travail, qui est spécifié dans la ligne suivante.
- La commande pour installer libgdiplus est exécutée dans le conteneur. Ceci est requis par System.Drawing.Common.
- La commande pour copier tout dans le conteneur, publier l'application et spécifier le point d'entrée.

### Construction et exécution de l'application dans Docker

Maintenant, l'application peut être construite et exécutée dans Docker. Ouvrez votre invite de commandes préférée, changez de répertoire vers le dossier avec l'application (dossier où se trouvent le fichier solution et le fichier Dockerfile) et exécutez la commande suivante :

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

La première fois que cette commande est exécutée, elle peut prendre plus de temps, car Docker doit télécharger les images requises. Une fois la commande précédente terminée, exécutez la commande suivante :

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

Faites attention à l'argument de montage, car, comme mentionné précédemment, un dossier sur la machine hôte est monté dans le dossier du conteneur, afin de voir facilement les résultats de l'exécution de l'application. Les chemins sous Linux sont sensibles à la casse.

{{% /alert %}}


## Plus d'exemples

Pour plus d'exemples de la façon dont vous pouvez utiliser Aspose.GIS dans Docker, consultez le [examples](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## Voir également

- [Installer Docker Desktop sur Windows](https://docs.docker.com/docker-for-windows/install/)
- [Installer Docker Desktop sur Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, SDK NET 3.1](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [Basculer vers les conteneurs Linux](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) option
- Informations supplémentaires sur le [SDK .NET Core](https://hub.docker.com/_/microsoft-dotnet-sdk)
