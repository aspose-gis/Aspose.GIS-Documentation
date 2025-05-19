---
title: Filtrowanie i indeksowanie warstw wektorowych GIS w C#
linktitle: Filtrowanie i indeksowanie
second_title: Aspose.GIS dla .NET
type: docs
url: /pl/filtering-and-indexing/
weight: 30
description: Dzięki bibliotece lub API GIS C# .NET możesz filtrować warstwy wektorowe GIS według wartości atrybutów lub granic przestrzennych. Możesz również używać indeksów, aby przyspieszyć filtrowanie i zapytania przestrzenne.
---

Dzięki Aspose.GIS dla .NET możesz filtrować warstwy według wartości atrybutów lub granic przestrzennych. Możesz również używać indeksów, aby przyspieszyć filtrowanie i zapytania przestrzenne.
## **Indeks atrybutu**
### **Filtr bez indeksu**
Oto jak filtrować warstwę według wartości atrybutu:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **Filtr z indeksem**
Powyższy kod jest w porządku, dopóki warstwa jest filtrowana tylko raz. Ale jeśli warstwa ma być wielokrotnie przeszukiwana, możemy skorzystać z indeksów atrybutów. Budowanie indeksu atrybutów zajmuje trochę czasu, ale można go wielokrotnie wykorzystywać do przyspieszenia filtrowania.

Poniższy przykład używa pliku indeksu atrybutów, aby przyspieszyć filtrowanie warstwy według wartości atrybutu:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **Zapisz przefiltrowane obiekty**
Przefiltrowane obiekty można zapisać do warstw:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **Renderuj przefiltrowane obiekty**
Można również renderować przefiltrowane obiekty. Poniższy przykład używa indeksu atrybutów, aby szybko wybrać wszystkie obiekty z populacją większą niż 2000 i dodać je do mapy:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **Indeks przestrzenny**
Indeksy przestrzenne służą do przyspieszenia zapytań przestrzennych. Podobnie jak indeksy atrybutów, indeksy przestrzenne są ponownie wykorzystywane po utworzeniu.
### **Znajdź obiekty najbliższe punktowi**
Oto jak użyć indeksu przestrzennego, aby przyspieszyć wyszukiwanie obiektu najbliższego danemu punktowi:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **Wybierz obiekty przecinające geometrię**
Poniższy przykład używa indeksu przestrzennego, aby przyspieszyć wybór obiektów, które przecinają się z geometrią:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
