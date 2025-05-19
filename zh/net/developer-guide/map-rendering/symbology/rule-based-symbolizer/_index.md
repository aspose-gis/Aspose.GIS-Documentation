---
title: "基于规则的符号化器"
type: docs
url: /zh/net/rule-based-symbolizer/
weight: 60
description: 基于规则的符号化器在 GIS C# 库或 API 中应用其他符号化器到要素几何体，基于用 C# 编码的任意规则。
---

## **基于规则的符号化器**
基于规则的符号化器是最灵活的符号化器。它应用其他符号化器到要素几何体，基于用 C# 编码的任意规则。

如果多个规则匹配一个要素，所有匹配的符号化器都将被应用。你可以通过调用 [AddElseRule](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer/methods/addelserule) 来指定应用于未匹配任何规则的要素的符号化器。
