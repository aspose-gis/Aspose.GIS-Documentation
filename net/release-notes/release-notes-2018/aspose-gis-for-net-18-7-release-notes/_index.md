---
title: "Aspose.GIS for .NET 18.7 Release Notes"
type: docs
url: /net/aspose-gis-for-net-18-7-release-notes/
weight: 80
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.GIS for .NET 18.7](https://downloads.aspose.com/gis/net).

{{% /alert %}} 
## **Major Features**
Major features and improvements in this release:

- Reading data in GML format
- Reading data in ESRI File Geodatabase format
## **List of Improvements**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|GISNET-174|Geography Markup Language (GML)|New Feature|
|GISNET-188|ESRI File Geodatabase (FileGDB)|New Feature|
## **Public API and Backward Incompatible Changes**
**Change in members of Drivers for working with vector layers** 

|**C# (before v18.7)**|
| :- |
|void HandleDriver(Driver driver)<br>{<br>`    `Console.WriteLine(driver.CanCreate);<br>`    `Console.WriteLine(driver.CanOpen);<br>`    `using (var layer = driver.Create("path"))<br>`    `{<br>`      `// work with layer<br>`    `}<br>`    `using (var layer = driver.Open("path"))<br>`    `{<br>`      `// work with layer<br>`    `}<br>}|
|**C# (since v18.7)**|
|void HandleDriver(Driver driver)<br>{<br>`    `Console.WriteLine(driver.CanCreateLayers);<br>`    `Console.WriteLine(driver.CanOpenLayers);<br>`    `using (var layer = driver.CreateLayer("path"))<br>`    `{<br>`      `// work with layer<br>`    `}<br>`    `using (var layer = driver.OpenLayer("path"))<br>`    `{<br>`      `// work with layer<br>`    `}<br>}|

