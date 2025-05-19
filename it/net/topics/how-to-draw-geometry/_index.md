---
title: "Come disegnare geometrie su una mappa"
type: docs
url: /it/how-to-draw-geometry
weight: 70
---

Per creare e visualizzare oggetti geometrici su una mappa, è necessario iniziare **creando un oggetto geometria**. Esistono due metodi che puoi utilizzare:

- **Costruttore per ogni tipo di elemento geometria**
Questo metodo prevede l'utilizzo di un costruttore personalizzato per ogni tipo di elemento geometria. Ad esempio, per creare un punto, utilizzeresti il seguente codice:

```
Point point = new Point(40.7128, -74.006);
```

Tuttavia, questo metodo può diventare impegnativo e ingombrante da gestire quando si creano oggetti complessi come polilinee o raccolte. Di conseguenza, lo sviluppatore potrebbe dover aggiungere molte righe di codice, causando una diminuzione della leggibilità del codice. Garantire l'integrità dei dati durante l'inizializzazione può anche essere difficile. Ad esempio, considera il seguente esempio che crea un poligono con un foro all'interno:

```
Polygon polygon = new Polygon();

LinearRing ring = new LinearRing();
ring.AddPoint(50.02, 36.22);
ring.AddPoint(49.99, 36.26);
ring.AddPoint(49.97, 36.23);
ring.AddPoint(49.98, 36.17);
ring.AddPoint(50.02, 36.22);

LinearRing hole = new LinearRing();
hole.AddPoint(50.00, 36.22);
hole.AddPoint(49.99, 36.20);
hole.AddPoint(49.98, 36.23);
hole.AddPoint(50.00, 36.24);
hole.AddPoint(50.00, 36.22);

polygon.ExteriorRing = ring;
polygon.AddInteriorRing(hole);
```

Un altro svantaggio di questo approccio è la mancanza di uniformità dei dati per l'inizializzazione. Non puoi creare un repository di costanti o file all'interno del tuo progetto.

- **WKT (Well-Known Text)**
Questo metodo prevede la generazione della geometria da WKT (Well-Known Text), che offre un modo standardizzato per creare geometrie. Il seguente codice dimostra come creare un punto e una linea:

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

Sebbene questo approccio possa ridurre leggermente le prestazioni a causa della necessità di analizzare la stringa, semplifica la creazione di oggetti più complessi.

Puoi trovare maggiori dettagli su WKT nel seguente articolo: "Esportazione e importazione di dati da/verso WKT e WKB".

Visualizzazione di oggetti geometrici sulla mappa
Una volta creato un oggetto geometria, il passo successivo è visualizzarlo sulla mappa. Sebbene la mappa possa visualizzare livelli caricati da varie fonti e formati, InMemoryLayer è un livello che non richiede una fonte.

**Per visualizzare l'oggetto geometria**, puoi creare un InMemoryLayer e aggiungere l'oggetto ad esso:

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

Ora puoi **visualizzare questo livello sulla mappa e creare un file in uno dei formati supportati**, come SVG, con il seguente codice:

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

Una volta aggiunto il livello e visualizzato sulla mappa, puoi salvarlo in uno qualsiasi dei formati supportati. In questo esempio, viene scelto il formato SVG per evitare potenziali problemi con il supporto Bitmap. È importante notare che Net 6.0 ha un supporto Bitmap limitato, che può comportare restrizioni come l'impossibilità di eseguire il rendering di immagini Bitmap utilizzando Blazor WebAsm sul lato client. Pertanto, quando si sceglie un formato per salvare la mappa, è importante considerare i limiti della piattaforma di destinazione e selezionare un formato compatibile con essa.

L'articolo spiega come creare e visualizzare oggetti geometrici su una mappa con uno stile predefinito e semplice. Tuttavia, la libreria Aspose offre un'ampia gamma di opzioni di stile che possono essere personalizzate per adattarsi alle tue esigenze. Per esplorare queste opzioni, ti consigliamo di consultare la [documentazione Aspose.MapRendering](https://docs.aspose.com/gis/net/map-rendering/), che fornisce informazioni dettagliate su come utilizzare diverse tecniche di stile per migliorare l'appeal visivo della tua mappa.

**In sintesi**, per creare oggetti geometrici su una mappa, puoi utilizzare un costruttore per ogni tipo di elemento geometria o generare la geometria da WKT. Per visualizzare l'oggetto, posizionalo su un livello e visualizza il livello su una mappa con stile predefinito della mappa. Salva la mappa in un formato supportato, come SVG, e utilizza la nostra libreria per esplorare le opzioni di stile. Inoltre, la nostra libreria offre l'opportunità di vedere un esempio completo facendo clic sul [link](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer) fornito nella documentazione, che può aiutarti a capire come implementare queste tecniche nei tuoi progetti.
