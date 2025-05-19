---
title: Como Executar Aspose.GIS em Docker
type: docs
description: "Execute o Aspose.GIS em um contêiner Docker para Linux, Windows Server e qualquer sistema operacional."
weight: 139
url: /pt/net/how-to-run-aspose-gis-in-docker/
---

## Pré-requisitos

- O Docker deve estar instalado no seu sistema. Para informações sobre como instalar o Docker no Windows ou Mac, consulte os links na seção "Ver Também".

- Visual Studio 2022.

- O SDK NET Core 3.1 é usado no exemplo.


## Aplicação Hello World

Neste exemplo, você cria uma aplicação de console simples Hello World que cria uma curva composta e a salva em arquivos. A aplicação pode então ser construída e executada no Docker.

### Criando a Aplicação do Console

Para criar o programa Hello World, siga os passos abaixo:
1. Depois que o Docker for instalado, certifique-se de que ele usa Contêineres Linux (padrão). Se necessário, selecione a opção Alternar para contêineres Linux no menu Docker Desktops.
1. No Visual Studio, crie uma aplicação de console NET Core 3.1.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. Instale a versão mais recente do Aspose.GIS do NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. Como a aplicação será executada no Linux, os ativos nativos Linux apropriados devem ser instalados. Comece com a imagem base dotnet core sdk 3.1 e instale libgdiplus libc6-dev.
1. Quando todas as dependências necessárias forem adicionadas, escreva um programa simples que cria uma curva composta:<br>
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

Observe que a pasta �TestOut� é especificada como uma pasta de saída para salvar documentos de saída. Ao executar a aplicação no Docker, uma pasta na máquina host será montada nesta pasta no contêiner. Isso permitirá que você visualize facilmente a saída gerada pelo Aspose.GIS no contêiner Docker.

### Configurando um Dockerfile

O próximo passo é criar e configurar o Dockerfile.

1. Crie o Dockerfile e coloque-o ao lado do arquivo de solução da sua aplicação. Mantenha este nome de arquivo sem extensão (o padrão).
1. No Dockerfile, especifique:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

O acima é um Dockerfile simples, que contém as seguintes instruções:

- A imagem SDK a ser usada. Aqui está a imagem Net 3.1. O Docker irá baixá-la quando a construção for executada. A versão do SDK é especificada como uma tag.
- O diretório de trabalho, que é especificado na próxima linha.
- O comando para instalar libgdiplus é executado no contêiner. Isso é necessário pelo System.Drawing.Common.
- O comando para copiar tudo para o contêiner, publicar a aplicação e especificar o ponto de entrada.

### Construindo e Executando a Aplicação em Docker

Agora a aplicação pode ser construída e executada no Docker. Abra seu prompt de comando favorito, altere o diretório para a pasta com a aplicação (pasta onde o arquivo de solução e o Dockerfile estão localizados) e execute o seguinte comando:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

A primeira vez que este comando for executado pode demorar mais, pois o Docker precisa baixar as imagens necessárias. Depois que o comando anterior for concluído, execute o seguinte comando:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

Preste atenção ao argumento de montagem, porque, como mencionado anteriormente, uma pasta na máquina host é montada na pasta do contêiner, para ver facilmente os resultados da execução da aplicação. Caminhos no Linux diferenciam maiúsculas de minúsculas.

{{% /alert %}}


## Mais Exemplos

Para mais exemplos de como você pode usar o Aspose.GIS em Docker, consulte o [exemplos](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## Ver Também

- [Instale o Docker Desktop no Windows](https://docs.docker.com/docker-for-windows/install/)
- [Instale o Docker Desktop no Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, SDK NET 3.1](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [Alternar para contêineres Linux](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) opção
- Informações adicionais sobre [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
