---
title: "Simbolo di Riempimento"
type: docs
url: /it/net/fill-symbolizer/
weight: 30
description: La libreria API GIS C# supporta il simbolo di riempimento semplice per lo stile e il tratto di geometrie bidimensionali poligoni di qualsiasi tipo come Punto, Linea, Superficie.
---

## **Simbolo di Riempimento**
Il simbolo di riempimento semplice riempie un'area con uno stile di riempimento e un tratto personalizzabili. Questo è il simbolo predefinito per le geometrie bidimensionali (poligoni). 

Se un poligono ha "buchi", questi non vengono riempiti, ma i bordi attorno ai buchi vengono tracciati nel modo usuale. Le "isole" all'interno dei buchi vengono riempite e tracciate, e così via.

Opzioni di stile supportate:

|**Proprietà**|**Descrizione**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Specifica il colore e la trasparenza dati al riempimento.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solido - Riempimento solido</p><p>- Nessuno - Non riempire il poligono</p><p>- Tratto Orizzontale - Un modello di linee orizzontali.</p><p>- Tratto Verticale - Un modello di linee verticali.</p><p>- Tratto a Croce - Specifica linee orizzontali e verticali che si incrociano.</p><p>- Tratto Diagonale in Avanti - Un modello di linee su una diagonale dall'alto a sinistra al basso a destra.</p><p>- Tratto Diagonale all'Indietro - Un modello di linee su una diagonale dall'alto a destra al basso a sinistra.</p><p>- Tratto Diagonale a Croce - Un modello di linee diagonali incrociate.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Specifica il colore e la trasparenza dati alla linea del tratto.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Specifica come dovrebbero essere disegnate le linee del simbolo.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Specifica la larghezza della linea del tratto.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Specifica un array di distanze che specifica le lunghezze di trattini e spazi alternati nelle linee tratteggiate.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Specifica la distanza dall'inizio di una linea all'inizio di un modello di trattini.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Determina come le linee vengono renderizzate alle intersezioni dei segmenti di linea.</p><p>- Miter - angolo acuto</p><p>- Round - angolo arrotondato</p><p>- Bevel - angolo diagonale</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Specifica l'offset orizzontale da una posizione del punto al punto di ancoraggio della forma.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Specifica l'offset verticale da una posizione del punto al punto di ancoraggio della forma.|

### **Tipi di Geometria**
` `Il simbolo può essere applicato a geometrie di qualsiasi tipo.

|**Dimensione della Geometria**|**Tipi di Geometria**|**Comportamento di Rendering**|
| :-: | :-: | :-: |
|**Punto**|Punto, MultiPoint|Disegna un piccolo quadrato ortogonale poligono.|
|**Linea**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|La linea viene chiusa per il riempimento collegando il suo punto finale al suo punto di partenza. Solo la linea originale viene tracciata.|
|**Superficie**|Poligono, CurvePolygon, MultiPolygon, MultiSurface|Disegna il poligono.|

Per GeometryCollections, il comportamento di rendering è determinato separatamente per ogni geometria all'interno della collection. I layer con tipo di geometria Misto seguono la logica per GeometryCollections.

Utilizza MixedGeometrySymbolizer per limitare un simbolo a tipi di geometria specifici.

### **Esempi**
Per impostazione predefinita, il simbolo di riempimento semplice disegna una linea del tratto nera e un riempimento bianco solido:



Ecco come modificare lo stile:




|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

-----
Potresti anche voler aggiungere etichette ai tuoi poligoni. Visita [Esempi di Etichettatura delle Linee](/it/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) per esempi su come etichettare i bordi dei poligoni o [Esempi di Etichettatura dei Punti](/it/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) su esempi su come etichettare i centri dei poligoni.
