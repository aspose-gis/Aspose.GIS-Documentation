---
title: "Simbolizzatore del marcatore"
type: docs
url: /it/net/marker-symbolizer/
weight: 10
description: La libreria o API GIS C# supporta il simbolizzatore del marcatore semplice che disegna una forma predefinita con riempimento e contorno personalizzabili su geometrie di qualsiasi tipo come Punto, Linea, Superficie.
---

## **Simbolizzatore del marcatore**
Il simbolizzatore del marcatore semplice disegna una forma predefinita con riempimento e contorno personalizzabili. Questo è il simbolizzatore predefinito per le geometrie 0-dimensionali (punti). 

Le forme supportate sono:

|![todo:image_alt_text](marker-symbolizer_1.png)|Cerchio| |![todo:image_alt_text](marker-symbolizer_2.png)|Stella|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Quadrato| |![todo:image_alt_text](marker-symbolizer_4.png)|Croce|
|![todo:image_alt_text](marker-symbolizer_5.png)|Triangolo| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

Le opzioni di stile supportate sono:

|**Proprietà**|**Descrizione**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|Specifica la forma del marcatore.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|Specifica le dimensioni della forma del marcatore|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|Specifica il colore e la trasparenza dati al riempimento|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|Specifica il colore e la trasparenza dati alla linea|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|Specifica lo spessore della linea|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|Determina come le linee vengono renderizzate alle intersezioni dei segmenti di linea.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|Specifica come dovrebbe essere disegnato il tratto del simbolo.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|Specifica un array di distanze che specifica le lunghezze di trattini e spazi alternati nelle linee tratteggiate.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|Specifica la distanza dall'inizio di una linea all'inizio di un modello di trattini.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|Specifica la rotazione del simbolo attorno al suo punto centrale, in gradi decimali. I valori positivi indicano la rotazione in senso orario, i valori negativi indicano la rotazione in senso antiorario. Il valore predefinito è 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|Specifica l'offset orizzontale dalla posizione di un punto al punto di ancoraggio della forma.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|Specifica l'offset verticale dalla posizione di un punto al punto di ancoraggio della forma.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|Specifica quale lato di una forma del marcatore sarà allineato orizzontalmente con la posizione del punto.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|Specifica quale lato di una forma del marcatore sarà allineato verticalmente con la posizione del punto.|

### **Tipi di geometria**
` `Il simbolizzatore può essere applicato a geometrie di qualsiasi tipo.

|**Dimensione della geometria**|**Tipi di geometria**|**Comportamento di rendering**|
| :-: | :-: | :-: |
|**Punto**|Punto, MultiPoint|Disegna la forma centrata sulle coordinate del punto.|
|**Linea**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>Disegna la forma centrata sul centroide della geometria</p><p> </p>|
|**Superficie**|Poligono, CurvePolygon, MultiPolygon, MultiSurface||

Per GeometryCollections, il comportamento di rendering viene determinato separatamente per ciascuna geometria all'interno della collection. I layer con tipo di geometria Misto seguono la logica per GeometryCollections.

Utilizza MixedGeometrySymbolizer per limitare un simbolizzatore a tipi di geometria specifici.

### **Esempi**
Per impostazione predefinita, il simbolizzatore del marcatore disegna cerchi neri:



Ecco come cambiare il colore di riempimento in rosso:



|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

Un altro esempio di stile con una forma predefinita (triangolo):



|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----
Per scenari più avanzati, potrebbe essere necessario regolare lo stile del marcatore dinamicamente in base ai valori degli attributi delle feature. Ecco come farlo:



|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
Potresti anche voler aggiungere etichette ai tuoi marcatori. Visita [Esempi di etichettatura dei punti](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) per esempi.
