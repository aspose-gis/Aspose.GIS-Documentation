---
title: "Aspose.GIS for .NET 21.5 Release Notes"
type: docs
url: /net/aspose-gis-for-net-21-5-release-notes/
weight: 120
---

{{% alert color="primary" %}} 

This page contains release notes information for [Aspose.GIS for .NET 21.5](https://www.nuget.org/packages/Aspose.GIS/21.5.0).

{{% /alert %}} 
## **Major Features**
- Format and parse coordinate using Degree Minutes Seconds (DMS), Degree Decimal Minutes (DDM), Decimal Degree (DD)
- Format and parse coordinate using GeoRef
## **Full List of Issues Covering all Changes in this Release**

|**Key**|**Summary**|**Category**|
| :- | :- | :- |
|GISNET-1221|Support for formatting and parsing GeoRef, DMS, DDM, DD|Feature|
|GISNET-1222|Invalid character when KML reading|Bug|
## **Public API and Backward Incompatible Changes**
Following members have been added:

- P:Aspose.Gis.Formats.Kml.KmlOptions.SymbolToReplaceInvalidChars
- T:Aspose.Gis.GeoConvert
- M:Aspose.Gis.GeoConvert.AsPointText(System.Double,System.Double,Aspose.Gis.PointFormats)
- M:Aspose.Gis.GeoConvert.AsPointText(Aspose.Gis.Geometries.IPoint,Aspose.Gis.PointFormats)
- M:Aspose.Gis.GeoConvert.ParsePointText(System.String)
- M:Aspose.Gis.GeoConvert.TryParsePointText(System.String,Aspose.Gis.Geometries.IPoint@)

Following members have been removed:
- none