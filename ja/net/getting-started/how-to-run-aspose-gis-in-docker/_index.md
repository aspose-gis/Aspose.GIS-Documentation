---
title: Docker で Aspose.GIS を実行する方法
type: docs
description: "Linux、Windows Server および任意の OS 用の Docker コンテナーで Aspose.GIS を実行します。"
weight: 139
url: /ja/net/how-to-run-aspose-gis-in-docker/
---

## 前提条件

- Docker がシステムにインストールされている必要があります。Windows または Mac に Docker をインストールする方法については、「関連項目」セクションのリンクを参照してください。

- Visual Studio 2022。

- 例で使用されるのは NET Core 3.1 SDK です。

## Hello World アプリケーション

この例では、コンパウンドカーブを作成し、ファイルを保存する簡単な Hello World コンソールアプリケーションを作成します。その後、アプリケーションをビルドして Docker で実行できます。

### コンソールアプリケーションの作成

Hello World プログラムを作成するには、以下の手順に従ってください。
1. Docker がインストールされていることを確認したら、Linux コンテナー (デフォルト) を使用していることを確認してください。必要な場合は、Docker Desktops メニューから「Linux コンテナーに切り替える」オプションを選択します。
1. Visual Studio で NET Core 3.1 コンソールアプリケーションを作成します。<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. NuGet から最新の Aspose.GIS バージョンをインストールします。<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. アプリケーションは Linux で実行されるため、適切なネイティブ Linux アセットをインストールする必要があります。dotnet core sdk 3.1 ベースイメージから開始し、libgdiplus libc6-dev をインストールします。
1. すべての必要な依存関係を追加したら、コンパウンドカーブを作成する簡単なプログラムを書きます。<br>
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
                // 'S' の文字を作成します (左下の端から開始)
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

出力ドキュメントを保存するための出力フォルダーとして「TestOut」フォルダーが指定されていることに注意してください。Docker でアプリケーションを実行する場合、ホストマシンのフォルダーはコンテナー内のこのフォルダーにマウントされます。これにより、Docker コンテナーで生成された Aspose.GIS の出力を簡単に表示できます。

### Dockerfile の設定

次のステップは、Dockerfile を作成して構成することです。

1. Dockerfile を作成し、アプリケーションのソリューションファイルと一緒に配置します。このファイルの拡張子は付けないようにしてください (デフォルト)。
1. Dockerfile で以下を指定します。

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

上記は単純な Dockerfile であり、次の指示が含まれています。

- 使用する SDK イメージ。ここでは Net 3.1 イメージです。ビルドが実行されると Docker がこれをダウンロードします。SDK のバージョンはタグとして指定されます。
- 次の行で指定されている作業ディレクトリ。
- コンテナー内で libgdiplus をインストールするためのコマンドを実行します。これは System.Drawing.Common によって必要です。
- すべてをコンテナーにコピーし、アプリケーションを発行し、エントリポイントを指定するコマンド。

### Docker でアプリケーションのビルドと実行

これで、Docker でアプリケーションをビルドして実行できます。お気に入りのコマンドプロンプトを開き、アプリケーション (ソリューションファイルと Dockerfile が配置されているフォルダー) のディレクトリを変更し、次のコマンドを実行します。

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

このコマンドを初めて実行すると、Docker が必要なイメージをダウンロードする必要があるため、時間がかかる場合があります。前のコマンドが完了したら、次のコマンドを実行します。

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

マウント引数に注意してください。前述のように、アプリケーションの実行結果を簡単に確認できるように、ホストマシンのフォルダーがコンテナーのフォルダーにマウントされます。Linux のパスは大文字と小文字を区別します。

{{% /alert %}}


## その他の例

Aspose.GIS を Docker で使用する方法の詳細なサンプルについては、[examples](https://github.com/aspose-gis/Aspose.Gis-for-.NET) を参照してください。

## 関連項目

- [Install Docker Desktop on Windows](https://docs.docker.com/docker-for-windows/install/)
- [Install Docker Desktop on Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [Switch to Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) オプション
- [.NET Core SDK]に関する追加情報 (https://hub.docker.com/_/microsoft-dotnet-sdk)
