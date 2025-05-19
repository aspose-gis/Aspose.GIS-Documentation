---
title: "レイヤー生成コンソールアプリケーション"
type: docs
url: /ja/net/layer-generator-console
weight: 50
---

## 要約

このコンソールアプリケーションは、さまざまな種類の幾何学的オブジェクトを生成し、選択した形式で保存するように設計されています。ポイント、ポリゴン、およびポリラインを作成したり、生成するオブジェクトの数を指定したり、保存用の出力形式を選択したりできます。

## 使用方法

コマンド構文：

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

引数：

```
-t, --type: ジオメトリタイプ。次のいずれか：Point、Polygon、Polyline。

-c, --count: 必須。生成するオブジェクトの数。例：15。

-f, --fileName: 必須。保存するためのファイル名。ファイル名と拡張子を指定してください。例：test.json。

-o, --outputFormat: 出力形式。サポートされているファイル形式についてはこちらを参照ください。

--help: コマンドのヘルプ情報を表示します。

--version: アプリケーションのバージョン情報を表示します。
```

15個のランダムなポイントを作成し、それらを「test.json」という形式のファイルに保存するコマンド例：

```
app.exe -t Point -c 15 -f test.json -o json
```

## インストールとライセンス

アプリケーションを使用するには、アーカイブをダウンロードして展開する必要があります。以下のリンクに従ってください。

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

Aspose.GIS Layer Generator Console Applicationは無料ですが、Aspose.GIS .NETは通常どおりライセンスされているため、アプリケーションを介してライセンスを再利用するか、トライアルモードでAspose.GIS .NETを使用してアプリケーションを評価するか、または一時ライセンスをリクエストできます。

## 結論

幾何学的オブジェクトジェネレーターは、さまざまな種類のジオメトリのサンプルを作成し、希望する形式で保存するのに役立つ便利なコンソールアプリケーションです。これは、地理空間データと地理情報システムの開発に取り組むための有用なツールです。
