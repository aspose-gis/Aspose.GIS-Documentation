---
title: "Filtering and Indexing"
type: docs
url: /net/filtering-and-indexing/
weight: 30
---

With Aspose.GIS for .NET you can filter layers by attribute values or spatial bounds. You can also use indices to speed up filtering and spatial queries.
## **Attribute index**
### **Filter Without Index**
Here's how to filter a layer by values of an attribute:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **Filter With Index**
The code above is fine as long as layer is filtered only once. But, if layer is likely to be queried for multiple times, we can benefit from attribute indices. It takes some time to build attribute index, but it can be reused multiple times to speed up filtering.

The following example uses an attribute index file to speed up layer filtering by values of the attribute:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **Save Filtered Features**
Filtered features can be saved into layers:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **Render Filtered Features**
It is also possible to render filtered features. The following examples uses attribute index to quickly select all features with population greater than 2000 and add them to the map:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **Spatial Index**
Spatial indices are used to speed up spatial queries. Just as attribute indices, spatial indices are reused after creation.
### **Find Features Nearest to Point**
Here's how to use spatial index to speed up looking for the feature closest to some point:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **Select Features Intersecting With Geometry**
The following examples uses spatial index to speed up selection of features that intersect with geometry:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}


