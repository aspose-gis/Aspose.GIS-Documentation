---
title: "流和远程存储"
type: docs
url: /zh/net/streams-and-remote-storage/
weight: 70
---

## **使用多文件格式**
某些 GIS 数据格式将内容拆分为多个文件。例如，shapefile 必须至少有三个文件：*.shp、*.shx 和 *.dbf。这些格式要求所有文件存储在特定的目录结构中，文件名具有预定义的模式。

同时，文件可能存储在远程服务器上，或者通过流访问的其他位置。流缺乏有关文件名和目录结构的信息，这使得文件格式驱动程序无法确定如何处理数据。Aspose.GIS 通过提供抽象路径机制来解决这个问题。

抽象路径表示某种类似文件系统的存储中文件的（或目录的）路径。该存储可以是任何具有文件和目录概念的东西，从档案到 FTP 服务器。它定义了如何执行典型的文件操作，例如打开文件或列出目录。

您可以通过实现继承 [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) 的类并为其抽象方法提供实现来指定如何为您的存储执行文件操作。
## **案例：Azure Blob 存储**
Aspose.GIS 示例库包含一个针对 Azure Blob 存储的自定义抽象路径的完整功能实现的示例。此案例演示了如何直接从 Azure Blob 存储读取 shapefile。您可以在这里找到它：[https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET)。
## **单文件格式（GeoJSON、KML）**
GIS 数据格式，如 GeoJSON 和 KML，可以将图层的全部数据存储在一个文件中。如果您可以获取文件的流，则可以跳过实现自定义抽象路径，并使用方法 [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) 来实例化流的抽象路径。
### **从流读取文件**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **将文件写入流**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
