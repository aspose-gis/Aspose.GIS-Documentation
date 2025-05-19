---
title: "Simbolizzatore di Linee"
type: docs
url: /it/net/line-symbolizer/
weight: 20
description: La libreria o API GIS C# supporta il simbolizzatore di linee semplici per geometrie unidimensionali (linee) e può essere applicata su geometrie di qualsiasi tipo come Punto, Linea, Superficie.
---

## **Simbolizzatore di Linee**
Il simbolizzatore di linee semplice disegna una linea con uno stile personalizzabile. Questo è il simbolizzatore predefinito per le geometrie unidimensionali (linee). 

Opzioni di stile supportate:

|**Proprietà**|**Descrizione**|
| :- | :- |
|[Color](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|Specifica il colore e la trasparenza dati alla linea.|
|[Width](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|Specifica la larghezza della linea|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|Determina come le linee vengono renderizzate alle intersezioni dei segmenti di linea.|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|Specifica come dovrebbe essere disegnato il lavoro di linea del simbolo.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|Specifica un array di distanze che specifica le lunghezze delle tratteggio e degli spazi nelle linee tratteggiate.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|Specifica la distanza dall'inizio di una linea all'inizio di un modello di trattino.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>Specifica come le linee vengono renderizzate alle loro estremità.</p><p>- Butt - bordo quadrato nitido</p><p>- Round - bordo arrotondato</p><p>- Square - bordo quadrato leggermente allungato</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|Specifica l'offset dalla linea originale. Per una distanza positiva, l'offset sarà sul lato sinistro della linea di input (relativo alla direzione della linea). Per una distanza negativa, sarà sul lato destro.|

### **Tipi di Geometria**
` `Il simbolizzatore può essere applicato a geometrie di qualsiasi tipo.

|**Dimensione della geometria**|**Tipi di geometria**|**Comportamento di rendering**|
| :-: | :-: | :-: |
|**Punto**|Punto, MultiPoint|Disegna una linea di piccola lunghezza con orientamento orizzontale centrata sul punto, con due tappi terminali.|
|**Linea**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Disegna la linea.|
|**Superficie**|Poligono, CurvePolygon, MultiPolygon, MultiSurface|Il contorno chiuso della geometria viene utilizzato come stringa di linea (senza tappi terminali)|

Per GeometryCollections, il comportamento di rendering è determinato separatamente per ciascuna geometria all'interno della collection. I layer con tipo di geometria Misto seguono la logica per GeometryCollections.

Utilizza MixedGeometrySymbolizer per limitare un simbolizzatore a tipi di geometria specifici.

### **Esempi**
Per impostazione predefinita, il simbolizzatore di linee disegna linee nere:



Ecco come cambiare il colore della linea in blu:



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

Per scenari più avanzati, potrebbe essere necessario regolare lo stile della linea dinamicamente in base ai valori degli attributi delle feature. Ecco come farlo:



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |



Potresti anche voler aggiungere etichette alle tue linee. Visita [Esempi di etichettatura delle linee](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) per esempi.
