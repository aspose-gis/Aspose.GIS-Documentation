---
title: "インストール"
second_title: Aspose.GIS for .NET
type: docs
url: /ja/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: NuGet を使用してパッケージマネージャー UI またはコンソールから GIS C#.NET ライブラリまたは API をインストールするか、ZIP アーカイブからインストールします。また、.NET Core および Linux OS でも使用できます。
---

## **Aspose.GIS のインストール**
### **NuGet から**
Aspose.GIS をインストールするには、パッケージマネージャー UI またはパッケージマネージャーコンソールを使用します。 パッケージをインストールすると、NuGet は依存関係をプロジェクトファイルまたは packages.config ファイルに記録します。
#### **パッケージマネージャー UI**
1. ソリューションエクスプローラーで、**参照**を右クリックし、**NuGet パッケージの管理**を選択します。

![todo:image_alt_text](installation_1.png)

1. **パッケージソース**として "nuget.org" が選択されていることを確認し、[参照] タブを選択して Aspose.GIS を検索し、リストからそのパッケージを選択して [インストール] をクリックします。

![todo:image_alt_text](installation_2.png)

1. [Aspose エンドユーザーライセンス契約](https://about.aspose.com/legal/eula)を確認してください。
2. 変更の確認を求められた場合は、**OK** を選択します。
#### **パッケージマネージャーコンソール**
1. **ツール** > **NuGet パッケージマネージャー** > **パッケージマネージャーコンソール** メニューコマンドを選択します。
2. コンソールが開いたら、**既定のプロジェクト**ドロップダウンリストに、パッケージをインストールする対象のプロジェクトが表示されていることを確認します。 ソリューションに単一のプロジェクトがある場合、すでに選択されています。

![todo:image_alt_text](installation_3.png)

1. Install-Package Aspose.GIS コマンドを入力します。 コンソールウィンドウにコマンドの出力が表示されます。
### **MSI インストーラーまたは ZIP アーカイブから**
NuGet によるインストールに加えて、Aspose.GIS を [ダウンロードセクション](https://downloads.aspose.com/gis/net) から MSI インストーラーまたは ZIP アーカイブとしてダウンロードできます。

## **プラットフォーム固有の指示**
### **Linux**
Aspose.GIS のマップレンダリング機能を使用する場合、System.Drawing.Common ライブラリが正しく構成されていることを確認してください。 次のようなエラーメッセージが表示された場合:

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

これは、System.Drawing.Common の依存関係がシステムに不足していることを意味します。 これを修正するには、次を実行してください。

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev

## **Aspose.GIS for .NET のシステム要件**
すべての Aspose .NET コンポーネントには完全信頼の権限セットが必要です。

Aspose.GIS には、次のためにビルドされたアセンブリの 2 つのバリアントが含まれています。

- .NET Framework 4.7,
- .NET Standard 2.0.

### **.NET Framework v4.7 以降**
オペレーティングシステム: 

- Microsoft Windows 10、8、7 SP1
- Microsoft Windows Server 2016、2012 R2、2012、2008 R2 SP1

` `32 ビットおよび 64 ビットバージョンがサポートされています。
### **.NET Core v2.0 以降**
` `オペレーティングシステム:

- Microsoft Windows 7 SP1、8.1、10 Anniversary Update (バージョン 1607) またはそれ以降のバージョン
- Microsoft Windows Server 2008 R2 SP1 (フルサーバーまたはサーバーコア)、2012 SP1 (フルサーバーまたはサーバーコア)、2012 R2 (フルサーバーまたはサーバーコア)、2016 以降のバージョン (フルサーバー、サーバーコア、または Nano Server)
- macOS 10.12 "Sierra" 以降のバージョン
- Linux (64 ビット、x86_64 または amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64 ビット、arm32), 8.7 以降のバージョン
  - Ubuntu 18.04 (64 ビット、arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 以降のバージョン
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 以降のバージョン
  - Alpine Linux 3.7 以降のバージョン

詳細については、.NET Core ガイドを参照してください: [Windows の前提条件](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies)、[macOS の前提条件](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies)、[Linux の前提条件](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **実験的サポート**
- Mono 5.4 以降
- Xamarin:
  - Xamarin.iOS: バージョン 10.14 以降
  - Xamarin.Android: バージョン 8.0 以降
  - Xamarin.Mac: バージョン 3.8 以降
