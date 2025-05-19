---
title: Jak spustit Aspose.GIS v Dockeru
type: docs
description: "Spusťte Aspose.GIS v kontejneru Docker pro Linux, Windows Server a jakýkoli OS."
weight: 139
url: /cs/net/how-to-run-aspose-gis-in-docker/
---

## Předpoklady

- Docker musí být nainstalován ve vašem systému. Informace o tom, jak nainstalovat Docker na Windows nebo Mac, naleznete v odkazech v sekci „Viz také“.

- Visual Studio 2022.

- V příkladu se používá .NET Core 3.1 SDK.


## Aplikace Hello World

V tomto příkladu vytvoříte jednoduchou konzolovou aplikaci Hello World, která vytvoří složitou křivku a uloží ji do souborů. Aplikaci pak můžete sestavit a spustit v Dockeru.

### Vytvoření konzolové aplikace

Chcete-li vytvořit program Hello World, postupujte podle následujících kroků:
1. Po instalaci Dockeru se ujistěte, že používá Linux Containers (výchozí). Pokud je to nutné, vyberte možnost Přepnout na Linux kontejnery z nabídky Docker Desktop.
1. Ve Visual Studiu vytvořte konzolovou aplikaci .NET Core 3.1.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. Nainstalujte nejnovější verzi Aspose.GIS z NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. Protože aplikace bude spuštěna na Linuxu, je třeba nainstalovat odpovídající nativní linuxové prostředky. Začněte se základním obrazem dotnet core sdk 3.1 a nainstalujte libgdiplus libc6-dev.
1. Po přidání všech požadovaných závislostí napište jednoduchý program, který vytvoří složitou křivku:<br>
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
                // vytvořte písmeno 'S' (začíná v levém dolním rohu)
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

Upozorňujeme, že složka „TestOut“ je specifikována jako výstupní složka pro ukládání výstupních dokumentů. Při spuštění aplikace v Dockeru se do této složky v kontejneru namontuje složka na hostitelském stroji. To vám umožní snadno zobrazit výstup generovaný Aspose.GIS v kontejneru Docker.

### Konfigurace souboru Dockerfile

Dalším krokem je vytvoření a konfigurace souboru Dockerfile.

1. Vytvořte soubor Dockerfile a umístěte jej vedle souboru řešení vaší aplikace. Zachovejte toto jméno bez přípony (výchozí).
1. V souboru Dockerfile specifikujte:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

Výše uvedené je jednoduchý soubor Dockerfile, který obsahuje následující instrukce:

- Obraz SDK, který se má použít. Zde je to obraz Net 3.1. Docker jej stáhne při spuštění sestavení. Verze SDK je specifikována jako tag.
- Pracovní adresář, který je specifikován v další řádku.
- Příkaz k instalaci libgdiplus se spustí v kontejneru. To vyžaduje System.Drawing.Common.
- Příkaz ke kopírování všeho do kontejneru, publikování aplikace a určení vstupního bodu.

### Sestavení a spuštění aplikace v Dockeru

Nyní lze aplikaci sestavit a spustit v Dockeru. Otevřete své oblíbené příkazové okno, změňte adresář do složky s aplikací (složka, kde jsou umístěny soubor řešení a soubor Dockerfile) a spusťte následující příkaz:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

Při prvním spuštění tohoto příkazu může trvat déle, protože Docker musí stáhnout požadované obrazy. Po dokončení předchozího příkazu spusťte následující příkaz:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

Věnujte pozornost argumentu mount, protože, jak bylo zmíněno dříve, je složka na hostitelském stroji namontována do složky kontejneru, abyste snadno viděli výsledky spuštění aplikace. Cesty v Linuxu jsou rozlišující velikost písmen.

{{% /alert %}}


## Další příklady

Další vzorky toho, jak můžete Aspose.GIS používat v Dockeru, naleznete na [příkladech](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## Viz také

- [Instalace Docker Desktop na Windows](https://docs.docker.com/docker-for-windows/install/)
- [Instalace Docker Desktop na Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, .NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [Přepnout na Linux kontejnery](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) možnost
- Další informace o [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
