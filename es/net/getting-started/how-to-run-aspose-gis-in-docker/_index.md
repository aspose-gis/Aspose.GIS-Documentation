---
title: Cómo Ejecutar Aspose.GIS en Docker
type: docs
description: "Ejecute Aspose.GIS en un contenedor de Docker para Linux, Windows Server y cualquier sistema operativo."
weight: 139
url: /es/net/how-to-run-aspose-gis-in-docker/
---

## Prerrequisitos

- Docker debe estar instalado en su sistema. Para obtener información sobre cómo instalar Docker en Windows o Mac, consulte los enlaces en la sección "Ver También".

- Visual Studio 2022.

- Se utiliza el SDK de NET Core 3.1 en el ejemplo.


## Aplicación Hello World

En este ejemplo, crea una aplicación de consola simple Hello World que crea una curva compuesta y la guarda en archivos. Luego, la aplicación se puede compilar y ejecutar en Docker.

### Creando la Aplicación de Consola

Para crear el programa Hello World, siga los siguientes pasos:
1. Una vez que Docker esté instalado, asegúrese de que utilice contenedores Linux (predeterminado). Si es necesario, seleccione la opción Cambiar a contenedores Linux desde el menú de Docker Desktops.
1. En Visual Studio, cree una aplicación de consola NET Core 3.1.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. Instale la última versión de Aspose.GIS desde NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. Dado que la aplicación se ejecutará en Linux, se deben instalar los activos nativos de Linux apropiados. Comience con la imagen base del sdk dotnet core 3.1 e instale libgdiplus libc6-dev.
1. Cuando se agregan todas las dependencias requeridas, escriba un programa simple que cree una curva compuesta:<br>
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

Tenga en cuenta que la carpeta �TestOut� se especifica como una carpeta de salida para guardar documentos de salida. Cuando ejecute la aplicación en Docker, una carpeta en la máquina host se montará en esta carpeta en el contenedor. Esto le permitirá ver fácilmente la salida generada por Aspose.GIS en el contenedor de Docker.

### Configurando un Archivo Dockerfile

El siguiente paso es crear y configurar el archivo Dockerfile.

1. Cree el archivo Dockerfile y colóquelo junto al archivo de solución de su aplicación. Mantenga este nombre de archivo sin extensión (el predeterminado).
1. En el archivo Dockerfile, especifique:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

Lo anterior es un archivo Dockerfile simple, que contiene las siguientes instrucciones:

- La imagen del SDK a utilizar. Aquí es la imagen Net 3.1. Docker lo descargará cuando se ejecute la compilación. La versión del SDK se especifica como una etiqueta.
- El directorio de trabajo, que se especifica en la siguiente línea.
- El comando para instalar libgdiplus se ejecuta en el contenedor. Esto es requerido por System.Drawing.Common.
- El comando para copiar todo al contenedor, publicar la aplicación y especificar el punto de entrada.

### Compilando y Ejecutando la Aplicación en Docker

Ahora la aplicación se puede compilar y ejecutar en Docker. Abra su símbolo del sistema favorito, cambie el directorio a la carpeta con la aplicación (carpeta donde se colocan el archivo de solución y el archivo Dockerfile) y ejecute el siguiente comando:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

La primera vez que se ejecuta este comando puede tardar más, ya que Docker necesita descargar las imágenes requeridas. Una vez completado el comando anterior, ejecute el siguiente comando:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

Preste atención al argumento de montaje, porque, como se mencionó anteriormente, una carpeta en la máquina host se monta en la carpeta del contenedor, para ver fácilmente los resultados de la ejecución de la aplicación. Las rutas en Linux distinguen entre mayúsculas y minúsculas.

{{% /alert %}}


## Más Ejemplos

Para obtener más ejemplos de cómo puede utilizar Aspose.GIS en Docker, consulte [ejemplos](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## Ver También

- [Instalar Docker Desktop en Windows](https://docs.docker.com/docker-for-windows/install/)
- [Instalar Docker Desktop en Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, SDK de NET 3.1](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [Cambiar a contenedores Linux](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) opción
- Información adicional sobre [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
