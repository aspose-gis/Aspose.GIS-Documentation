---
title: Symbolika - C# GIS API
linktitle: "Symbolika"
type: docs
url: /pl/symbology/
weight: 10
description: Biblioteka lub interfejs API GIS C# obsługuje symbolizatory do rysowania geometrii obiektów, takich jak znacznik, linia, wypełnienie oraz łączenie symbolizatorów w celu tworzenia bardziej złożonych wizualizacji.
---

Symbolizator to sposób na narysowanie geometrii obiektu na mapie.

|** **|**Symbolizator**|**Klasa API**|**Opis**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**Znacznik**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Rysuje zdefiniowany kształt z konfigurowalnym wypełnieniem i obrysem.|
|![todo:image_alt_text](symbology_2.png)|**Linia**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Rysuje linię z konfigurowalnym stylem.|
|![todo:image_alt_text](symbology_3.png)|**Wypełnienie**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Wypełnia wielokąt lub obszar ograniczony linią konfigurowalnym wypełnieniem i obrysem.|
Oprócz symbolizatorów, które faktycznie rysują, istnieje szereg innych symbolizatorów, które pozwalają na łączenie innych symbolizatorów w celu tworzenia bardziej złożonych wizualizacji.

|**Symbolizator**|**Klasa API**|**Opis**|
| :- | :- | :- |
|**Warstwowy Symbolizator**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Rysuje obiekt za pomocą kilku symbolizatorów na sobie.|
|**Mieszany Symbolizator Geometrii**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Rysuje obiekty z warstw zawierających geometrie różnych typów za pomocą określonego symbolizatora dla każdego typu geometrii.|
|**Symbolizator Oparty na Regułach**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Wybiera symbolizator do zastosowania do obiektu zgodnie z regułami określonymi przez użytkownika.|
|**Symbolizator Klastra Znaczników**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|Rysuje grupowanie znaczników, grupując te elementy.|
|**Symbolizator Generatora Geometrii**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Pozwala na zastąpienie geometrii obiektu przed renderowaniem.|
|**Symbolizator Null**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|Nic nie rysuje. Przydatne w połączeniu z innymi symbolizatorami, takimi jak symbolizator oparty na regułach.|
