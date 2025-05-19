---
title: 使用 GIS C# 库连接矢量图层
linktitle: 连接图层
type: docs
url: /zh/Join-layers/
weight: 52
description: 文章中提供的代码片段可用于使用 C# API 连接 GIS 矢量图层。
---

## **连接矢量图层**
Aspose.GIS API 使您可以连接矢量图层，如下面的代码片段所示。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinByName.cs" >}}


## **使用少量属性连接图层**
Aspose.GIS API 使您可以连接少量属性，如下面的代码片段所示。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinFewAttributes.cs" >}}

## **使用自定义比较器连接图层**
Aspose.GIS API 使您可以像下面的代码片段所示，使用自己的比较器来连接图层。当您需要使用不区分大小写的字符串连接数据时，这种方法很好。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinWithConditionComparer.cs" >}}

比较器实现。

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-InsensitiveComparer.cs" >}}
