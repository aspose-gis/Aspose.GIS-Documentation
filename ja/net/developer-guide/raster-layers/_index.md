---
title: GIS C# ライブラリを使用したラスターレイヤーの操作
linktitle: ラスターレイヤー
type: docs
url: /ja/net/raster-layers/
weight: 20
description: GIS C# ライブラリを使用すると、GISソフトウェアで最も広く使用されているラスター形式の1つであるGeoTIFFラスター形式を読み込んだり操作したりできます。
---

## **GeoTIFF サンプルのマルチバンドラスターでの作業**
GeoTIFFは、GISソフトウェアで最も広く使用されているラスター形式の1つです。Aspose.GISを使用すると、GeoTIFFラスター形式を操作できます。
### **マルチバンドラスター内の一般的なデータを読み込む**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-InteractWithRasterFormats-ReadGeneralDataInGeoTiff.cs" >}}
### **行ごとに値を読み込む**
{{< gist "evgeniy-timofeev-aspose" "bf3543d44881bfd31b27a80173268d52" "raster-layers-ReadValuesByLine.cs" >}}
### **指定された型の値の読み込み**
{{< gist "evgeniy-timofeev-aspose" "bf3543d44881bfd31b27a80173268d52" "raster-layers-ReadValuesWithSpecifiedType.cs" >}}
### **LINQまたはExpressionメソッドを使用してラスター値を分析する**
{{< gist "evgeniy-timofeev-aspose" "bf3543d44881bfd31b27a80173268d52" "raster-layers-ReadValuesByLine.cs" >}}
### **GoeTIFF内の生のビットを読み込む**
{{< gist "evgeniy-timofeev-aspose" "bf3543d44881bfd31b27a80173268d52" "raster-layers-ReadRawBytesInGeoTiff.cs" >}}

## **Esri ASCII サンプルのシングルバンドラスター形式での作業**
EsriAscii形式は常に単一のバンドを持ちます。
### **シングルバンドラスター内の一般的なデータを読み込む**
{{< gist "evgeniy-timofeev-aspose" "bf3543d44881bfd31b27a80173268d52" "raster-layers-ReadSingleBandEsriAscii.cs" >}}
