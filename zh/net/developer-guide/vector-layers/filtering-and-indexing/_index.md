---
title: 在 C# 中过滤和索引 GIS 矢量图层
linktitle: 过滤和索引
second_title: Aspose.GIS for .NET
type: docs
url: /zh/filtering-and-indexing/
weight: 30
description: 使用 GIS C# .NET 库或 API，您可以按属性值或空间边界过滤 GIS 矢量图层。您还可以使用索引来加速过滤和空间查询。
---

使用 Aspose.GIS for .NET 可以通过属性值或空间边界过滤图层。您还可以使用索引来加速过滤和空间查询。
## **属性索引**
### **无索引的过滤**
以下是如何按属性的值过滤图层：

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **有索引的过滤**
如果图层只被过滤一次，那么上面的代码是可以的。但是，如果图层可能被多次查询，我们可以从属性索引中受益。构建属性索引需要一些时间，但可以多次重用它来加速过滤。

以下示例使用属性索引文件来加速按属性值过滤图层：

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **保存过滤后的要素**
过滤后的要素可以保存到图层中：

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **渲染过滤后的要素**
也可以渲染过滤后的要素。以下示例使用属性索引快速选择所有人口大于 2000 的要素并将它们添加到地图中：

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **空间索引**
空间索引用于加速空间查询。就像属性索引一样，空间索引在创建后会被重用。
### **查找距离点最近的要素**
以下是如何使用空间索引来加速查找距离某个点最近的要素：

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **选择与几何体相交的要素**
以下示例使用空间索引来加速选择与几何体相交的要素：

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
