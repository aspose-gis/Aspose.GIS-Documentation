---
title: Simbologia - API GIS C#
linktitle: "Simbologia"
type: docs
url: /it/symbology/
weight: 10
description: La libreria o API GIS C# supporta i simbolizzatori per disegnare la geometria delle entità come Marcatori, Linee, Riempimenti e combinando i simbolizzatori per creare visualizzazioni più complesse.
---

Un simbolizzatore è un modo per disegnare una geometria di entità su una mappa.

|** **|**Simbolizzatore**|**Classe API**|**Descrizione**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**Marcatore**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Disegna una forma predefinita con riempimento e contorno personalizzabili.|
|![todo:image_alt_text](symbology_2.png)|**Linea**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Disegna una linea con stile personalizzabile.|
|![todo:image_alt_text](symbology_3.png)|**Riempimento**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Riempie un poligono o un'area delimitata da una linea con riempimento e tratto personalizzabili.|
Oltre ai simbolizzatori che eseguono effettivamente il disegno, esiste un numero di altri simbolizzatori che consentono di combinare altri simbolizzatori per creare visualizzazioni più complesse.

|**Simbolizzatore**|**Classe API**|**Descrizione**|
| :- | :- | :- |
|**Simbolizzatore a livelli**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Disegna un'entità con diversi simbolizzatori uno sopra l'altro|
|**Simbolizzatore di geometria mista**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Disegna entità da livelli che contengono geometrie di tipi misti con un simbolizzatore specifico per ogni tipo di geometria|
|**Simbolizzatore basato su regole**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Seleziona un simbolizzatore da applicare a un'entità in base alle regole specificate dall'utente.|
|**Simbolizzatore di cluster di marcatori**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|Disegna il clustering dei marcatori, raggruppamento di questi elementi.|
|**Simbolizzatore del generatore di geometria**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Consente di sostituire la geometria dell'entità prima del rendering.|
|**Simbolizzatore nullo**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|Non disegna nulla. Utile quando combinato con altri simbolizzatori, come il simbolizzatore basato su regole.|
