---
title: Symbolika - C# GIS API
linktitle: "Symbolika"
type: docs
url: /cs/symbology/
weight: 10
description: GIS C# knihovna nebo API podporuje symbolizátory pro kreslení geometrie entit, jako jsou značky, čáry, výplně a kombinování symbolizátorů pro vytváření složitějších vizualizací.
---

Symbolizátor je způsob, jak nakreslit geometrii entity na mapě.

|** **|**Symbolizátor**|**API třída**|**Popis**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**Značka**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Kreslí předdefinovaný tvar s přizpůsobitelnou výplní a obrysem.|
|![todo:image_alt_text](symbology_2.png)|**Čára**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Kreslí čáru s přizpůsobitelným stylem.|
|![todo:image_alt_text](symbology_3.png)|**Výplň**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Vyplní polygon nebo oblast ohraničenou čarou s přizpůsobitelnou výplní a obrysem.|
Kromě symbolizátorů, které provádějí skutečné kreslení, existuje řada dalších symbolizátorů, které umožňují kombinovat další symbolizátory pro vytváření složitějších vizualizací.

|**Symbolizátor**|**API třída**|**Popis**|
| :- | :- | :- |
|**Vrstvený symbolizátor**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Kreslí entitu s několika symbolizátory na sobě|
|**Smíšený geometrický symbolizátor**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Kreslí entity z vrstev, které obsahují geometrie smíšených typů se specifickým symbolizátorem pro každý typ geometrie|
|**Symbolizátor založený na pravidlech**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Vybere symbolizátor, který se má aplikovat na entitu podle pravidel specifikovaných uživatelem.|
|**Symbolizátor shluků značek**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|Kreslí shluky značek, seskupování těchto položek.|
|**Generátor geometrie symbolizátor**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Umožňuje nahradit geometrii entity před vykreslením.|
|**Null Symbolizátor**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|Nic nekreslí. Užitečné v kombinaci s jinými symbolizátory, jako je symbolizátor založený na pravidlech.|
