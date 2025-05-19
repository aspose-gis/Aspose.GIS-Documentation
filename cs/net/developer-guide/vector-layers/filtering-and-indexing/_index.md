---
title: Filtrování a indexování GIS vektorových vrstev v C#
linktitle: Filtrování a indexování
second_title: Aspose.GIS pro .NET
type: docs
url: /cs/filtering-and-indexing/
weight: 30
description: S knihovnou nebo API GIS C# .NET můžete filtrovat GIS vektorové vrstvy podle hodnot atributů nebo prostorových hranic. Můžete také použít indexy ke zrychlení filtrování a prostorových dotazů.
---

S Aspose.GIS pro .NET můžete filtrovat vrstvy podle hodnot atributů nebo prostorových hranic. Můžete také použít indexy ke zrychlení filtrování a prostorových dotazů.
## **Atributový index**
### **Filtr bez indexu**
Zde je postup, jak filtrovat vrstvu podle hodnot atributu:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **Filtr s indexem**
Výše uvedený kód je v pořádku, dokud se vrstva filtruje pouze jednou. Pokud se však vrstva pravděpodobně dotazuje vícekrát, můžeme těžit z atributových indexů. Vytvoření atributového indexu trvá nějaký čas, ale lze jej opakovaně použít ke zrychlení filtrování.

Následující příklad používá soubor atributového indexu ke zrychlení filtrování vrstvy podle hodnot atributu:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **Uložení filtrovaných prvků**
Filtrované prvky lze uložit do vrstev:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **Vykreslení filtrovaných prvků**
Je také možné vykreslit filtrované prvky. Následující příklad používá atributový index k rychlému výběru všech prvků s populací větší než 2000 a přidáním do mapy:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **Prostorový index**
Prostorové indexy se používají ke zrychlení prostorových dotazů. Stejně jako atributové indexy, i prostorové indexy jsou po vytvoření opakovaně využívány.
### **Nalezení prvků nejbližších bodu**
Zde je postup, jak použít prostorový index ke zrychlení hledání prvku nejblíže určitému bodu:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **Výběr prvků protínajících geometrii**
Následující příklad používá prostorový index ke zrychlení výběru prvků, které protínají geometrii:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
