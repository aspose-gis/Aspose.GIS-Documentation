---
title: "Streams and Remote Storage"
type: docs
url: /net/streams-and-remote-storage/
weight: 70
---

## **Working with Multi-File Formats**
Some GIS data formats split content into several files. For example, a shapefile must have at least three files: *.shp, *.shx, and *.dbf. These formats require all files to be stored in a particular directory structure with a predefined pattern for filenames.

At the same time, the files may be stored on a remote server, or another location accessible through streams only. Streams lack information about filenames and directory structure, making it impossible for file format drivers to determine how to process data. Aspose.GIS solves this by providing the abstract paths mechanism.

An abstract path represents a path to a file (or a directory) in some filesystem-like storage. The storage can be anything that has a concept of the file and the directory, from an archive to an FTP server. It defines how to execute typical file operations, such as opening a file or listing a directory.

You can specify how to perform file operations for your storage by implementing a class that inherits [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) and providing implementations for its abstract methods.
## **Showcase: Azure Blob Storage**
The Aspose.GIS Examples repository contains an example of a fully-functional implementation of a custom abstract path for Azure Blob Storage. This showcase shows how to read a shapefile directly from Azure Blob Storage. You can find it here: <https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET>.
## **Single-file formats (GeoJSON, KML)**
GIS data formats like GeoJSON and KML can store all data for a layer in a single file. If you can obtain a stream for the file, you can skip implementing a custom abstract path, and use method [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) to instantiate an abstract path for the stream.
### **Read a file from a stream**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **Write a file to a stream**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
