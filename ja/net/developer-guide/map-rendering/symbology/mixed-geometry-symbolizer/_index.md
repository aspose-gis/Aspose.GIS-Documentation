---
title: "混合ジオメトリシンボライザー"
type: docs
url: /ja/net/mixed-geometry-symbolizer/
weight: 50
description: GIS C# Library API の混合ジオメトリシンボライザーを使用すると、レイヤーに混合ジオメトリタイプが含まれている場合、各ジオメトリタイプに対して別々にシンボライザーを指定できます。
---

## **混合ジオメトリシンボライザー**
混合ジオメトリシンボライザーを使用すると、レイヤーに混合ジオメトリタイプが含まれている場合、各ジオメトリタイプに対して別々にシンボライザーを指定できます。

|**プロパティ**|**説明**|
| :- | :- |
|[PointSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/pointsymbolizer)|レイヤー内のポイントジオメトリ (Point、MultiPoint) に使用するシンボライザーを指定します|
|[LineSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/linesymbolizer)|レイヤー内のラインジオメトリ (LineString、CircularString、CompoundCurve、LinerRing、MultiCurve、MultiLineString) に使用するシンボライザーを指定します|
|[PolygonSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer/properties/polygonsymbolizer)|レイヤー内のポリゴンジオメトリ (Polygon、CurvePolygon、MultiPolygon、MultiSurface) に使用するシンボライザーを指定します|
### **例**
この例では、レイヤーにポイント、ライン、およびポリゴンが含まれています。各ジオメトリタイプを別々にスタイル設定します。
