---
title: C# で GPS Exchange Format GPX ファイルを操作する
linktitle: GPX - GPS Exchange Format
type: docs
url: /ja/net/gpx-gps-exchange/
weight: 60
description: C# GIS ライブラリを使用すると、GPS Exchange File (GPX) ファイルからフィーチャを開いて読み取ることができます。
---

## **GPS Exchange File (GPX) ファイルの操作**
Aspose.GIS を使用すると、GPS Exchange File (GPX) ファイルからフィーチャを開いて読み取ることができます。
## **GPX ファイルからフィーチャを読み取る**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **セグメント内の各ポイントのフィーチャを読み取る**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **GPX ファイルにポリゴンを線として書き込む**
GPX 形式は、ポリゴンとマルチポリゴンをサポートしていません。 その結果、他の形式からの変換が失敗することがあります。 この問題を解決するには、WritePolygonsAsLines オプションを適用する必要があります。
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
