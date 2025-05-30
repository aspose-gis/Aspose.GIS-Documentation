---
title: "機能"
second_title: Aspose.GIS for .NET
type: docs
url: /ja/net/features/
weight: 30
keywords: GIS C# Library, GIS C# API, Read ShapeFile in C#
description: GIS C#.NET ライブラリまたは API は、Shapefile、GeoJSON、FileGDB、GML、KML、SVG、PostGis、Sql Server、GeoTIFF 形式をサポートします。ベクターデータの読み込み、書き込み、変換、視覚化、ジオメトリの操作、分析の実行、SRID による空間参照システムの検索が可能です。
---

Aspose.GIS for .NET は、一般的な GIS ファイル形式で保存されたデータを使用するための豊富な機能セットを提供します。ベクター GIS データの読み書き、GIS ファイル形式間の変換、フィーチャジオメトリの作成と分析、SVG へのマップレンダリングを行うことができます。

# **サポートされている形式**
主要なサポート対象ファイル形式は次のとおりです。

- Shapefile
- GeoJSON
- ESRI File Geodatabase (FileGDB)
- Geography Markup Language (GML)
- Keyhole Markup Language (KML)
- Scalable Vector Graphics (SVG)
- Databases (PostGis, Sql Server)
- GeoTIFF

完全なリストについては、[サポートされているファイル形式](/gis/ja/net/supported-file-formats/) を参照してください。

# **ベクターデータの読み書き**
- ベクターデータを読み込む
  - レイヤーフィーチャを反復処理する
  - インデックスでレイヤーフィーチャを読み込む
  - ベクターレイヤーに関するメタデータを取得する
- ベクターデータを書き込む
  - 新しいレイヤーとデータセットを作成する
- マルチレイヤーデータセットを使用する
  - 既存のレイヤーをリストする
  - 新しいレイヤーを追加する
  - データセットからレイヤーを削除する
- 空間クエリを高速化するために空間インデックスを構築します。

# **ベクターデータの変換**
- サポートされている形式にデータを変換する
- データ変換時にリプロジェクションを実行する
- 変換中にフィーチャ属性を調整する

# **データの視覚化**
- マップを SVG、PNG、JPEG、または BMP にレンダリングする
- 各ジオメトリタイプに合わせてスタイルをカスタマイズする
- 複雑な描画を行うために複数のシンボライザーを組み合わせる
- レイヤーレンダリングルールによってフィーチャの視覚表現を制御する
- フィーチャの属性値に基づいてフィーチャのスタイリングパラメータを計算する

詳細については、[マップレンダリング](/gis/ja/net/map-rendering/) を参照してください。

# **ジオメトリの操作**
- 最初からポイント、ライン、ポリゴンを作成する
- 既存のジオメトリを編集する
- 地図上にオブジェクトにラベルを付ける。
- 非線形ジオメトリ（曲線）を構築する
- 非線形ジオメトリ（曲線）を直線化する
- WKT および WKB から/へのジオメトリをインポートおよびエクスポートする
- 計算の精度モデルを制御する

# **ベクターデータ分析を実行**
- 2 つのジオメトリが互いに交差するかどうかを判断します。
- ジオメトリが重複しているか、エッジに触れているか、交差しているかなど、ジオメトリ間の他の関係をテストします。
- ジオメトリ間の距離を見つける
- ジオメトリの凸包、重心、バッファー領域を計算する
- 任意のジオメトリの交差、和集合、または差分を計算します。

# **空間参照システムを使用**
- SRID で空間参照システムを検索する
- データファイルから SRS 情報読み込む
- 作成したデータに SRS を割り当てる
- 個々のジオメトリと完全なレイヤーをリプロジェクションする
- WKT から空間参照システムをインポートし、WKT に空間参照システムをエクスポートします。
