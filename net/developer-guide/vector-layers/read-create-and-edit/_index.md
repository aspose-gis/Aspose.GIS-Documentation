---
title: "Working with Vector Layers"
type: docs
url: /net/read-create-and-edit/
weight: 50
---

## **Create ShapeFile**
Aspose.GIS for .NET lets you create new ShapeFile and add information to it. A ShapeFile can be populated with Attributes information and Features can be added against these.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateNewShapeFile-CreateNewShapeFile.cs" >}}
## **Create Vector Layer with Spatial Reference System**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateVectorLayerWithSpatialReferenceSystem-CreateVectorLayerWithSpatialReferenceSystem.cs" >}}
## **Add new features in ShapeFile**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ModifyFeatures-AddFeaturesInExistShapeFile.cs" >}}
## **Convert Polygon Shape File Line String Shape File**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ConvertPolygonShapeFileToLineStringShapeFile-ConvertPolygonShapeFileToLineStringShapeFile.cs" >}}
## **Working with KML Files**
### **Creating KML File**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateKMLFile-CreateKMLFile.cs" >}}
### **Export style properties to KML**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ExportStylePropertiesToKml-ExportStylePropertiesToKml.cs" >}}
### **Reading Features from KML File**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadFeaturesFromKML-ReadFeaturesFromKML.cs" >}}
## **Working with OpenStreetMap (OSM) XML Files**
Aspose.GIS lets you open and read features from OpenStreetMap (OSM) XML files. At present, the API doesn't provide the facility to create new OSM XML file and only reading is supported.
### **Reading Features from OSM XML File**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadFeaturesFromOSMXML-ReadFeaturesFromOSMXML.cs" >}}
## **Working with GPS Exchange File (GPX) Files**
Aspose.GIS lets you open and read features from GPS Exchange File (GPX) files. At present, the API doesn't provide the facility to create a new GPX file and only reading is supported.
### **Reading Features from GPX File**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadFeaturesFromGPX-ReadGPXFeatures.cs" >}}
## **Working with Geography Markup Language (GML)**
Aspose.GIS provides the capability to read features from Geography Markup Language (GML). It lets you specify the schema option in case there is one.
### **Reading Features from GML File by Specifying Schema**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadFeaturesFromGML-ReadGMLBySpecifyingGMLOptions.cs" >}}
### **Reading Features from GML File without Specifying Schema**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadFeaturesFromGML-ReadGMLWithoutSpecifyingGMLOptions.cs" >}}
## **Working with ESRI File GeoDatabases (FileGDB)**
ESRI File GeoDatabases (FileGDB) are one of the most widely used native formats among GIS Software. Aspose.GIS lets you work with the FileGDB file formats and iterate over its features.
### **Iterate over Layers in FileGDB File**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-IterateOverLayersInFileGdb.cs" >}}
### **Convert FileGDB to GeoJSON**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-ConvertFeaturesFromFileGdbToGeoJson.cs" >}}
### **Reading FileGDB as Layer**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}
### **Open ShapeFile as Dataset**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadingESRIFileGeoDatabaseFileGDB-OpenFileGdbAsLayer.cs" >}}
### **Add Layer to FileGDB Dataset**
Open existing FileGDB dataset and adds new layers to it

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-AddLayerToFileGdbDataset-AddLayerToFileGdbDataset.cs" >}}
### **Remove Layer from FileGDB Dataset**
Open an existing FileGDB dataset and remove layers from it.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-RemoveLayersFromFileGdbDataset-RemoveLayersFromFileGdbDataset.cs" >}}
### **Create FileGDB Dataset**
Creates a new FileGDB dataset and add layers to it.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDataset-CreateFileGdbDataset.cs" >}}
### **Create FileGDB Dataset with one Layer using VectorLayer API**
This example creates a FileGDB dataset with one layer using VectorLayer API.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-CreateFileGdbDatasetWithSingleLayer-CreateFileGdbDatasetWithSingleLayer.cs" >}}
### **Convert GeoJSON Layer to FileGDB Dataset Layer**
Create new Layer in FileGDB and add data from GeoJSON Layer into it.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ConvertGeoJsonLayerToLayerInFileGdbDataset-ConvertGeoJsonLayerToLayerInFileGdbDataset.cs" >}}
### **Read OBJECTID from FileGDB Dataset Layer**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadObjectIdFromFileGdbLayer-ReadObjectIdFromFileGdbLayer.cs" >}}
### **Specify Precision Grid for FileGDB Layer**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyPrecisionGridForFileGdbLayer-SpecifyPrecisionGridForFileGdbLayer.cs" >}}
### **Specify Tolerances for FileGDB Layer**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyTolerancesForFileGdbLayer-SpecifyTolerancesForFileGdbLayer.cs" >}}
### **Specify Names of ObjectId and Geometry Fields**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-SpecifyNamesOfObjectIdAndGeometryFields-SpecifyNamesOfObjectIdAndGeometryFields.cs" >}}




