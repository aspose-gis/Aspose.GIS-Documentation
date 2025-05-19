---
title: "标记簇符号化器"
type: docs
url: /zh/net/marker-cluster-symbolizer/
weight: 65
description: 在 GIS C# 库或 API 中的标记簇符号化器允许在指定距离内对标记进行聚类。
---

## **标记簇符号化器**
标记簇符号化器是高级符号化器之一。它允许在指定距离内对标记进行聚类。

在这个 C# 示例中，我们将集群中心绘制为红色圆圈。此外，我们使用不同的颜色绘制所有嵌套的集群点。为此，我们使用了 FeaturesBasedConfiguration 函数，该函数为每个集群设置自己的样式。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterMarkerSymbolizer.cs" >}}

这是结果：

![points cluster](points-cluster.png)

## **绘制项目总数**

此示例显示集群中的项目总数。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterTextSymbolizer.cs" >}}

这是结果：

![digits cluster](digits-cluster.png)
