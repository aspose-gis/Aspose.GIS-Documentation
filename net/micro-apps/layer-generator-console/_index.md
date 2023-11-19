---
title: "Layer Generator Console Application"
type: docs
url: /net/layer-generator-console
weight: 50
---

## Summary

This console application is designed to generate geometric objects of various types and save them in the chosen format. It allows you to create points, polygons, and polylines, specify the number of objects to generate, and choose the output format for saving.

## Usage

Command syntax:

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

Arguments:

- -t, --type: Geometry type. One of the following: Point, Polygon, Polyline.

- -c, --count: Required. Number of objects to generate. For example: 15.

- -f, --fileName: Required. File name for saving. Specify the file name and extension. For example: test.json.

- -o, --outputFormat: Output format. See the supported file formats here.

- --help: Display help information for the command.

- --version: Display the application version information.

An example command to create 15 random points and save them to a file with the format "test.json":

```
app.exe -t Point -c 15 -f test.json -o json
```

## Installation and Licensing

If you want to use the application, you need to download the archive and extract it. Please follow the link below.

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

Although Aspose.GIS Layer Generator Console Application is free, Aspose.GIS .NET is licensed as usual, so you may reuse your license via application or evaluate the application using Aspose.GIS .NET in trial mode or request Temporary license.

## Conclusion

The Geometric Objects Generator is a convenient console application that helps you create samples of geometry of various types and save them in the desired format. It is a useful tool for working with geospatial data and developing geoinformation systems.