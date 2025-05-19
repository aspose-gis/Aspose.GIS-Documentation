---
title: 地図を画像 SVG、PNG、JPG にレンダリングする GIS C# ライブラリ
linktitle: "地図のレンダリング"
type: docs
url: /ja/net/map-rendering/
weight: 50
description: GIS C# API を使用すると、Shapefile、FileGDB、GeoJSON、KML 形式から地図をレンダリングし、高度なスタイルを設定して、ラスター形式から地図を描画できます。
---

## **地図のレンダリング概要**
Aspose.GIS for .NET C# API を使用すると、Shapefile、FileGDB、GeoJSON、KML またはその他の [サポートされているファイル形式](/gis/net/supported-file-formats/) から地図を SVG、PNG、JPEG、または BMP にレンダリングできます。

以下は、デフォルト設定を使用して Shapefile から SVG に地図をレンダリングする方法を示す C# コードです。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}

ここに結果を示します。

![地図のレンダリング](map_rendering.png)

コードを詳しく見てみましょう。

まず、[Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map)オブジェクトをインスタンス化します。これは、さまざまなソースからのレイヤーのコレクションを表し、レンダリングできます。 Map には、表示するサイズがあります。ここでは、地図の幅を 800 ピクセル、高さを 400 ピクセルに設定します。

Map は using ステートメントで囲まれていることに注意してください。これは、Map が追加されたすべてのリソースを追跡し、レンダリングが完了して Map オブジェクトが破棄されるときにそれらを破棄する必要があるためです。

次に、ファイルからレイヤーを地図に追加します。各レイヤーは、追加された順序で前のレイヤーの上にレンダリングされます。ベクターレイヤーを開く方法の詳細については、[こちら](/gis/net/working-with-vector-layers/)を参照してください。

最後に、[Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) を呼び出して地図をファイルにレンダリングします。結果ファイルを保存するパスと使用するレンダラーを指定します。クラス [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) には、Aspose.GIS に含まれるすべてのレンダラーへの参照が含まれています。たとえば、上記の例で Renderers.Png ではなく Renderers.Svg を指定して地図を PNG ファイルにレンダリングできます。

## **高度なスタイル設定**
Aspose.GIS API を使用すると、レンダリングとフィーチャースタイルをカスタマイズして、必要な外観を実現できます。

![高度なスタイル](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}

## **地図にラスターを描画**
Aspose.GIS for .NET を使用すると、ラスター形式から地図をレンダリングできます。

### **デフォルト設定でレンダリング**
以下は、デフォルト設定を使用して GeoTIFF から SVG に地図をレンダリングする方法です。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![デフォルトのラスター](default_raster.png)

### **歪んだラスターをレンダリング**
Aspose.GIS を使用すると、歪んだラスターセルを持つラスターをレンダリングできます。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![歪んだラスター](skew_raster.png)

### **極座標空間参照でレンダリング**
Aspose.GIS を使用すると、地図のレンダリングプロセスで極座標空間参照を使用できます。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![等角投影の国](gnomonic_countries.png)
