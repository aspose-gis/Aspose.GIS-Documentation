---
title: 符号 - C# GIS API
linktitle: "符号"
type: docs
url: /zh/symbology/
weight: 10
description: GIS C# 库或 API 支持符号化器来绘制要素几何体，例如标记、线条、填充以及组合符号化器以创建更复杂的视觉效果。
---

符号化器是在地图上绘制要素几何体的一种方式。

|** **|**符号化器**|**API 类**|**描述**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**标记**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|绘制具有可自定义填充和轮廓的预定义形状。|
|![todo:image_alt_text](symbology_2.png)|**线条**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|绘制具有可自定义样式的线条。|
|![todo:image_alt_text](symbology_3.png)|**填充**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|用可自定义的填充和描边填充多边形或由线条限定的区域。|
除了执行实际绘制的符号化器之外，还有许多其他符号化器允许组合其他符号化器以创建更复杂的视觉效果。

|**符号化器**|**API 类**|**描述**|
| :- | :- | :- |
|**分层符号化器**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|用多个符号化器在顶部绘制要素|
|**混合几何体符号化器**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|使用特定于每种几何类型的符号化器绘制包含混合类型几何体的图层中的要素|
|**基于规则的符号化器**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|根据用户指定的规则选择应用于要素的符号化器。|
|**标记簇符号化器**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|绘制标记的聚类，对这些项目进行分组。|
|**几何体生成器符号化器**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|允许在渲染之前替换要素几何体。|
|**空符号化器**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|不绘制任何内容。与其它符号化器组合时很有用，例如基于规则的符号化器。|
