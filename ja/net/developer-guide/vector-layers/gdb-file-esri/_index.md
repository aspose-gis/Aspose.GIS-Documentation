---
title: C# で Esri Gdb ファイル形式を操作する
linktitle: "GDB ESRI ファイル"
type: docs
url: /ja/net/gdb-file-esri/
weight: 80
keywords: esri gdb ファイル形式, c# で gdb ファイルを読む
description: GIS C# ライブラリを使用すると、ESRI File GeoDatabases FileGDB 形式を読み取り、操作、変換、または変更できます。
---

## **ESRI File GeoDatabases (FileGDB)**
ESRI File GeoDatabases (FileGDB) は、GIS ソフトウェアで最も広く使用されているネイティブ形式の 1 つです。Aspose.GIS を使用すると、FileGDB ファイル形式を操作し、そのフィーチャを反復処理できます。

### **FileGDB ファイル内のレイヤーを反復処理する**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-IterateOverLayersInFileGdb.cs" >}}

### **FileGDB を GeoJSON に変換する**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-ConvertFeaturesFromFileGdbToGeoJson.cs" >}}

### **FileGDB をレイヤーとして読み込む**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}

### **ShapeFile をデータセットとして開く**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}

### **FileGDB データセットにレイヤーを追加する**
既存の FileGDB データセットを開き、新しいレイヤーをそれに追加します。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-AddLayerToFileGdbDataset-AddLayerToFileGdbDataset.cs" >}}

### **FileGDB データセットからレイヤーを削除する**
既存の FileGDB データセットを開き、そこからレイヤーを削除します。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-RemoveLayersFromFileGdbDataset-RemoveLayersFromFileGdbDataset.cs" >}}

### **FileGDB データセットを作成する**
新しい FileGDB データセットを作成し、レイヤーをそれに追加します。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDataset-CreateFileGdbDataset.cs" >}}

### **VectorLayer API を使用して 1 つのレイヤーを持つ FileGDB データセットを作成する**
この例では、VectorLayer API を使用して 1 つのレイヤーを持つ FileGDB データセットを作成します。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDatasetWithSingleLayer-CreateFileGdbDatasetWithSingleLayer.cs" >}}

### **GeoJSON レイヤーを FileGDB データセットレイヤーに変換する**
FileGDB に新しいレイヤーを作成し、GeoJSON レイヤーからデータを追加します。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ConvertGeoJsonLayerToLayerInFileGdbDataset-ConvertGeoJsonLayerToLayerInFileGdbDataset.cs" >}}

### **FileGDB データセットレイヤーから OBJECTID を読み取る**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadObjectIdFromFileGdbLayer-ReadObjectIdFromFileGdbLayer.cs" >}}

### **FileGDB レイヤーの精度グリッドを指定する**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyPrecisionGridForFileGdbLayer-SpecifyPrecisionGridForFileGdbLayer.cs" >}}

### **FileGDB レイヤーの許容値を指定する**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyTolerancesForFileGdbLayer-SpecifyTolerancesForFileGdbLayer.cs" >}}

### **ObjectId および Geometry フィールドの名前を指定する**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyNamesOfObjectIdAndGeometryFields-SpecifyNamesOfObjectIdAndGeometryFields.cs" >}}
