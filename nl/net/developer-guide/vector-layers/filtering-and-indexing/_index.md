---
title: Filteren en Indexeren van GIS Vector Layers in C#
linktitle: Filteren en Indexeren
second_title: Aspose.GIS voor .NET
type: docs
url: /nl/filtering-and-indexing/
weight: 30
description: Met de GIS C# .NET Library of API kunt u GIS vector layers filteren op attribuutwaarden of ruimtelijke grenzen. U kunt ook indices gebruiken om het filteren en ruimtelijke queries te versnellen.
---

Met Aspose.GIS voor .NET kunt u lagen filteren op attribuutwaarden of ruimtelijke grenzen. U kunt ook indices gebruiken om het filteren en ruimtelijke queries te versnellen.
## **Attribuutindex**
### **Filter Zonder Index**
Hier is hoe u een laag kunt filteren op waarden van een attribuut:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **Filter Met Index**
De bovenstaande code is prima zolang de laag slechts één keer wordt gefilterd. Maar als de laag waarschijnlijk meerdere keren wordt opgevraagd, kunnen we profiteren van attribuutindices. Het duurt even om een attribuutindex te bouwen, maar deze kan meerdere keren worden hergebruikt om het filteren te versnellen.

Het volgende voorbeeld gebruikt een attribuutindexbestand om het filteren van lagen op waarden van het attribuut te versnellen:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **Opslaan Gefilterde Features**
Gefilterde features kunnen worden opgeslagen in lagen:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **Renderen Gefilterde Features**
Het is ook mogelijk om gefilterde features te renderen. Het volgende voorbeeld gebruikt een attribuutindex om snel alle features met een bevolking van meer dan 2000 te selecteren en toe te voegen aan de kaart:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **Ruimtelijke Index**
Ruimtelijke indices worden gebruikt om ruimtelijke queries te versnellen. Net als attribuutindices, worden ruimtelijke indices hergebruikt na creatie.
### **Zoek Features Dichtstbijzijnde Punt**
Hier is hoe u een ruimtelijke index kunt gebruiken om het zoeken naar de feature die het dichtst bij een bepaald punt ligt te versnellen:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **Selecteer Features Die Snijden Met Geometrie**
Het volgende voorbeeld gebruikt een ruimtelijke index om het selecteren van features die met geometrie snijden te versnellen:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
