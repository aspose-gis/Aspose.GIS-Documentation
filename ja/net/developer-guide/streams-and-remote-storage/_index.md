---
title: "ストリームとリモートストレージ"
type: docs
url: /ja/net/streams-and-remote-storage/
weight: 70
---

## **マルチファイル形式での作業**
一部のGISデータ形式は、コンテンツを複数のファイルに分割します。たとえば、シェープファイルには、*.shp、*.shx、および*.dbfの少なくとも3つのファイルが必要です。これらの形式では、すべてのファイルを特定のディレクトリ構造内に、定義済みのファイル名パターンで保存する必要があります。

同時に、ファイルはリモートサーバーまたはストリーム経由でのみアクセス可能な別の場所に格納されている場合があります。ストリームにはファイル名とディレクトリ構造の情報がないため、ファイル形式ドライバーがデータをどのように処理するかを判断することはできません。Aspose.GISはこの問題を抽象パスメカニズムを提供することで解決します。

抽象パスは、ある種のファイルシステムのようなストレージ内のファイル（またはディレクトリ）へのパスを表します。ストレージは、アーカイブからFTPサーバーまで、ファイルとディレクトリの概念を持つものであれば何でも構いません。ファイルを開いたりディレクトリをリストしたりするなど、典型的なファイル操作を実行する方法を定義します。

[AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) を継承し、その抽象メソッドの実装を提供することで、ストレージのファイル操作の方法を指定できます。
## **ショーケース：Azure Blob Storage**
Aspose.GIS Examplesリポジトリには、Azure Blob Storage用のカスタム抽象パスの完全な実装例が含まれています。このショーケースでは、Azure Blob Storageから直接シェープファイルを読み取る方法を示します。こちらで見つけることができます：[https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET)。
## **単一ファイル形式（GeoJSON、KML）**
GeoJSONやKMLなどのGISデータ形式は、レイヤーのすべてのデータを1つのファイルに保存できます。ファイルのストリームを取得できる場合は、カスタム抽象パスの実装をスキップし、メソッド[AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream)を使用してストリーム用の抽象パスをインスタンス化できます。
### **ストリームからファイルを読み込む**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **ストリームにファイルを書き込む**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
