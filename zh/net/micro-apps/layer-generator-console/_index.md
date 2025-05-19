---
title: "图层生成器控制台应用程序"
type: docs
url: /zh/net/layer-generator-console
weight: 50
---

## 摘要

这个控制台应用程序旨在生成各种类型的几何对象并将它们保存为所选格式。它允许您创建点、多边形和折线，指定要生成的对象数量以及选择用于保存的输出格式。

## 用法

命令语法：

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

参数：

```
-t, --type: 几何类型。以下之一：Point、Polygon、Polyline。

-c, --count: 必需。要生成的对象数量。例如：15。

-f, --fileName: 必需。保存的文件名。指定文件名和扩展名。例如：test.json。

-o, --outputFormat: 输出格式。请在此处查看支持的文件格式。

--help: 显示命令的帮助信息。

--version: 显示应用程序版本信息。
```

一个示例命令，用于创建 15 个随机点并将它们保存到格式为“test.json”的文件中：

```
app.exe -t Point -c 15 -f test.json -o json
```

## 安装和许可

如果您想使用该应用程序，需要下载存档并解压缩它。请按照以下链接操作。

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

虽然 Aspose.GIS 图层生成器控制台应用程序是免费的，但 Aspose.GIS .NET 仍按常规许可授权，因此您可以通过应用程序重用您的许可证或使用试用模式下的 Aspose.GIS .NET 评估该应用程序或请求临时许可证。

## 结论

几何对象生成器是一个方便的控制台应用程序，可帮助您创建各种类型的几何样本并将它们保存为所需的格式。它是处理地理空间数据和开发地理信息系统的有用工具。
