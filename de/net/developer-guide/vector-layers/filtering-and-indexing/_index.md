---
title: Filtern und Indizieren von GIS-Vektorlayern in C#
linktitle: Filtern und Indizieren
second_title: Aspose.GIS für .NET
type: docs
url: /de/filtering-and-indexing/
weight: 30
description: Mit der GIS C#- .NET-Bibliothek oder API können Sie GIS-Vektorlayer nach Attributwerten oder räumlichen Grenzen filtern. Sie können auch Indizes verwenden, um das Filtern und die räumlichen Abfragen zu beschleunigen.
---

Mit Aspose.GIS für .NET können Sie Layer nach Attributwerten oder räumlichen Grenzen filtern. Sie können auch Indizes verwenden, um das Filtern und die räumlichen Abfragen zu beschleunigen.
## **Attributindex**
### **Filtern ohne Index**
Hier erfahren Sie, wie Sie einen Layer nach Werten eines Attributs filtern:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **Filtern mit Index**
Der obige Code ist in Ordnung, solange der Layer nur einmal gefiltert wird. Wenn der Layer jedoch wahrscheinlich mehrmals abgefragt wird, können wir von Attributindizes profitieren. Der Aufbau eines Attributindex dauert einige Zeit, kann aber mehrfach wiederverwendet werden, um das Filtern zu beschleunigen.

Das folgende Beispiel verwendet eine Attributindexdatei, um das Filtern von Layern nach Werten des Attributs zu beschleunigen:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **Gefilterte Features speichern**
Gefilterte Features können in Layern gespeichert werden:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **Gefilterte Features rendern**
Es ist auch möglich, gefilterte Features zu rendern. Das folgende Beispiel verwendet einen Attributindex, um schnell alle Features mit einer Bevölkerung von mehr als 2000 auszuwählen und sie der Karte hinzuzufügen:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **Räumlicher Index**
Räumliche Indizes werden verwendet, um räumliche Abfragen zu beschleunigen. Genau wie Attributindizes werden räumliche Indizes nach der Erstellung wiederverwendet.
### **Features in der Nähe eines Punktes finden**
Hier erfahren Sie, wie Sie einen räumlichen Index verwenden, um die Suche nach dem Feature in der Nähe eines bestimmten Punktes zu beschleunigen:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **Features auswählen, die sich mit einer Geometrie schneiden**
Das folgende Beispiel verwendet einen räumlichen Index, um die Auswahl von Features zu beschleunigen, die sich mit einer Geometrie schneiden:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
