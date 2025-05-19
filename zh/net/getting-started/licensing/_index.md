---
title: "许可"
second_title: Aspose.GIS for .NET
type: docs
url: /zh/net/licensing/
weight: 50
keywords: c# gis library, .net gis library
description: 评估 C# .NET GIS 库或 API，具有一些限制。 使用文件或流对象或作为嵌入式资源应用许可证。
---

## **评估 Aspose.GIS for .NET**
您可以免费下载 Aspose.GIS for .NET。 在您应用许可之前，该组件以评估模式工作。 当您购买许可证并添加几行代码以应用许可证时，将删除评估限制。

{{% alert color="primary" %}} 如果您想在没有评估模式限制的情况下测试 Aspose.GIS，您可以申请 30 天临时许可证。 请参阅 [获取临时许可证](https://purchase.aspose.com/temporary-license)。 {{% /alert %}}
### **评估模式限制**
在评估模式下执行（未应用许可）时，Aspose.GIS 提供完整的产品功能，但有一些评估限制。

1. 每小时最多可以打开和/或创建 **15 个文档**
2. 每个文档中最多可以访问 **100 个要素**（读取或写入）
3. 每个文档中最多可以访问 **10 000 个栅格数据**（读取或写入）。
4. 文档转换操作允许的最大要素数量为 **50**

在许可模式下执行时，您可以处理无限数量的文档和要素。
## **应用许可证**
许可证是一个纯文本 XML 文件，其中包含产品名称、授权开发人员数量、订阅到期日期等详细信息。 该文件经过数字签名，因此请勿修改该文件。 即使无意中将额外的换行符添加到文件中也会使它失效。

如果您想避免其评估限制，则需要在利用 Aspose.GIS 之前设置许可证。 只需要为每个应用程序（或进程）设置一次许可证即可。
### **在 Aspose.GIS for .NET 中设置许可证**
在 Aspose.GIS 中，许可可以从文件、流或嵌入式资源加载。 Aspose.GIS 会尝试在以下位置查找许可证：

- 明确路径
- 包含 Aspose.GIS.dll 的文件夹
- 包含调用 Aspose.GIS.dll 的程序集的文件夹
- 包含入口程序集（您的 .exe）的文件夹
- 嵌入到调用 Aspose.GIS.dll 的程序集中的嵌入式资源。 有两种常见的方法来设置许可证，如下所述：
### **使用文件或流对象应用许可证**
设置许可证的最简单方法是将许可文件放在与 Aspose.GIS.dll 相同的文件夹中，并仅指定文件名（不包括路径）。

{{< highlight java >}}

 // 实例化 License 的实例并通过其路径设置许可文件

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // 实例化 License 的实例并通过流设置许可

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}

当您调用 SetLicense 方法时，许可证名称应与您的许可证文件名相同。 例如，您可以将许可证文件名更改为“Aspose.GIS.lic.xml”。 然后在代码中，您应该使用修改后的许可名称（即 Aspose.GIS.lic.xml）来设置 SetLicense 方法。

## **将许可文件作为嵌入式资源包含**
将许可与您的应用程序打包并确保不会丢失的另一种方法是将其作为嵌入式资源包含到调用组件 DLL（包含在 Aspose.GIS 中）中的一个程序集中。 要将许可文件作为嵌入式资源包含，请执行以下步骤：

- 在 Visual Studio 中，使用“文件|添加现有项目...”菜单将许可 (.lic) 文件添加到项目中
- 在解决方案资源管理器中选择该文件，并在属性窗口中将生成操作设置为“嵌入式资源”
- 要访问程序集中嵌入的许可（作为嵌入式资源），无需调用 Microsoft .NET Framework 的 System.Reflection.Assembly 类的 GetExecutingAssembly 和 GetManifestResourceStream 方法。 所需做的就是将许可文件作为嵌入式资源添加到您的项目中，并将许可文件的名称传递给 License.SetLicense 方法。 License 类会自动在嵌入式资源中找到许可文件。

请查看以下示例以了解如何在应用程序中设置（嵌入）许可证的方法。

{{< highlight java >}}

 // 实例化 License 类

Aspose.Gis.License license = new Aspose.Gis.License();

// 只传递嵌入到程序集中的许可文件的名称

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **应用计量密钥**
[Aspose.GIS for .NET API](/gis/net/) 允许开发人员应用计量密钥。 它是一种新的许可机制。 新的许可机制将与现有的许可方法一起使用。 希望根据 API 功能的使用情况计费的客户可以使用计量许可。 有关详细信息，请参阅 [计量许可常见问题解答](https://purchase.aspose.com/faqs/licensing/metered) 部分。

引入了一个新的类 **Metered** 来应用计量密钥。 以下是演示如何设置计量公共和私钥的示例代码。

**[C#]**

{{< highlight csharp >}}

 // 设置计量公共和私钥
 
Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();

// 访问 setMeteredKey 属性并将公共和私钥作为参数传递

metered.SetMeteredKey("*****", "*****");

// 进行处理

// 获取计量数据量

decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();

// 显示信息

Console.WriteLine("消耗金额： " + amount.ToString());

{{< /highlight >}}
