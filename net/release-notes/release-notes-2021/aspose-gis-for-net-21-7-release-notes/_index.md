---
title: "Aspose.GIS for .NET 21.7 Release Notes"
type: docs
url: /net/aspose-gis-for-net-21-7-release-notes/
weight: 100
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.GIS for .NET 21.7](https://www.nuget.org/packages/Aspose.GIS/21.7.0).

{{% /alert %}} 
## **Major Features**
- Write data to CSV
- Add options for CSV
- Fix bugs in KML, GML
## **Full List of Issues Covering all Changes in this Release**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|GISNET-1229|Write data to CSV|Feature|
|GISNET-1237|Add geometry options to CSV|Feature|
|GISNET-1233|Add delimiters options to read CSV|Feature|
|GISNET-1234|Add record and fields options to read CSV|Feature|
|GISNET-1241|Support Esri style VERTCS for WKT|Enhancement|
|GISNET-1239|Fix 'Missed closing point' for Geometry.ReplacePolygonsByLines|Bug|
|GISNET-1243|Fix 'Non-negative number required' Exception For KML|Bug|
|GISNET-1244|Fix 'Undeclared prefix' Exception For KML|Bug|
|GISNET-1245|Fix 'Value cannot be null' Exception For GML|Bug|

## **Public API and Backward Incompatible Changes**
Following members have been added:

- M:Aspose.Gis.Raster.RasterLayer.Crop(Aspose.Gis.Geometries.IGeometry)
- P:Aspose.Gis.Formats.Csv.CsvOptions.Delimiter
- P:Aspose.Gis.Formats.Csv.CsvOptions.DoubleQuoteEscape
- P:Aspose.Gis.Formats.Csv.CsvOptions.StartLineNumber
- P:Aspose.Gis.Formats.Csv.CsvOptions.HasAttributeNames
- P:Aspose.Gis.Formats.Csv.CsvOptions.ColumnX
- P:Aspose.Gis.Formats.Csv.CsvOptions.ColumnY
- P:Aspose.Gis.Formats.Csv.CsvOptions.ColumnZ
- P:Aspose.Gis.Formats.Csv.CsvOptions.ColumnM
- P:Aspose.Gis.Formats.Csv.CsvOptions.ColumnWkt

Following members have been removed:
- none