---
title: "Optimal Path Finder"
type: docs
url: /it/optimal-path-finder
weight: 70
---

## Summary

La ricerca del percorso più breve su una rete stradale è un processo di analisi volto a determinare il modo più efficiente per viaggiare tra punti su una mappa. Questo strumento può essere utile per creare percorsi ottimali con più tappe o misurare la distanza e i tempi di percorrenza tra diverse località. Con ogni chiamata, la nostra tecnologia può trovare percorsi ottimali per uno o più veicoli. Ad esempio, può aiutare gli autisti a trovare i percorsi ottimali per consegnare merci o determinare la distanza ottimale dal luogo di residenza al lavoro per diversi passeggeri.

## Algorithm Capabilities

La nostra libreria fornisce la possibilità di costruire il percorso più **ottimale tra due punti** su una mappa. Ha le seguenti caratteristiche principali:

1. Ricerca del percorso ottimale sulla mappa, considerando sentieri e ostacoli: Teniamo conto non solo delle strade ma anche dei percorsi fuoristrada come sentieri, marciapiedi e ostacoli che possono influenzare la scelta del percorso ottimale.

2. Ricerca del percorso ottimale solo su strade: Se è necessario trovare un percorso esclusivamente su strade, forniamo questa funzionalità. Questo è utile, ad esempio, per i veicoli autorizzati a viaggiare solo su strada.

3. Impostazione di diverse velocità per le strade: Abbiamo la possibilità di assegnare diverse velocità a diverse strade. Ad esempio, velocità più elevate possono essere impostate per le autostrade principali e velocità inferiori per le corsie strette.

4. Impostazione di ostacoli rettangolari: È possibile definire ostacoli rettangolari sulla mappa che devono essere presi in considerazione durante la costruzione del percorso ottimale. Questo è utile quando ci sono ostacoli noti come edifici o laghi (la loro approssimazione).

5. Limitazione del raggio di ricerca per le strade: È possibile limitare il raggio di ricerca per le strade per ridurre i tempi di ricerca e concentrarsi solo su un'area specifica.

6. Controllo delle prestazioni e della precisione: Forniamo la possibilità di controllare le prestazioni e la precisione dell'algoritmo. Puoi ottimizzarlo per ottenere l'equilibrio desiderato tra velocità di ricerca e accuratezza della costruzione del percorso.

Successivamente, forniremo una descrizione più dettagliata di ciascuna di queste funzionalità ed esamineremo esempi delle loro applicazioni.

## Approach to Solution

Sebbene la ricerca del percorso sia un compito non banale, ci sono diversi buoni algoritmi affidabili riconosciuti nella comunità di sviluppo.

Nella nostra implementazione, abbiamo utilizzato un algoritmo di Lee modificato. Abbiamo una griglia di celle sul piano. Dal punto di partenza, un'onda si propaga in 8 direzioni (incluse le diagonali) alle celle vicine, calcolando il tempo necessario per raggiungerle ciascuna. Una cella vicina può contenere un ostacolo o una strada. Le strade possono avere diversi coefficienti di velocità. Pertanto, "segnaliamo" la nostra griglia con il tempo necessario per raggiungere ogni cella dalla cella iniziale entro un certo raggio o fino a raggiungere il punto di destinazione. Se raggiungiamo il punto di destinazione, costruiamo un percorso inverso utilizzando la nostra griglia.

Per determinare il percorso ottimale sulla rete stradale, è necessario eseguire diversi passaggi. Innanzitutto, è necessario definire le strade e specificare la velocità di movimento su ciascuna di esse. È inoltre necessario considerare la presenza di ostacoli artificiali e naturali che possono influenzare il percorso. Dopo aver eseguito questi passaggi preliminari, puoi procedere alla ricerca del percorso effettivo. Il risultato sarà un percorso rappresentato, ad esempio, come un elenco di coordinate dei punti.

È importante notare che il percorso ottimale può dipendere dalla modalità di trasporto scelta, poiché la velocità di movimento e l'insieme degli ostacoli possono variare. Pertanto, diversi set di strade e ostacoli devono essere utilizzati per ogni tipo di trasporto durante la ricerca del percorso ottimale.

## Demo Project on GitHub

Per comprendere meglio le funzionalità della nostra libreria, consideriamo [un esempio del suo utilizzo](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths). Questo codice illustra come impostare strade e ostacoli nell'algoritmo di ricerca del percorso e trovare il percorso ottimale.

L'esempio consiste nei seguenti passaggi:

1. Creazione di un elenco di informazioni sulle strade (RoadInfo), che include informazioni sul segmento stradale (Segment) e la velocità di movimento (Velocity).
2. Aggiunta di strade veloci all'elenco.
3. Aggiunta di strade ad anello lente all'elenco.
4. Creazione di un generatore di livelli di percorso (WayLayerGenerator) e aggiunta di strade al generatore.
5. Ricerca di più percorsi dal punto di partenza (startPoint) ai punti di destinazione (goalPoint01, goalPoint02, goalPoint03) utilizzando il raggio specificato (radius).
6. Preparazione di un livello stradale (roadsLayer) per la visualizzazione sulla mappa e aggiunta di oggetti stradali.
7. Preparazione di un livello di percorso (wayLayer) per la visualizzazione sulla mappa e creazione di oggetti geometrici per ciascun percorso trovato.
8. [Visualizzazione della mappa](https://docs.aspose.com/gis/net/how-to-draw-geometry/) utilizzando la funzione ShowMap, salvando la mappa al percorso specificato.

Questo codice costruisce e visualizza i percorsi stradali sulla mappa per punti specificati utilizzando informazioni sulle strade e il generatore di livelli di percorso.

## Search Options

La ricerca del percorso viene eseguita utilizzando la classe **WayLayerGenerator** situata nello spazio dei nomi Aspose.Gis.GeoTools.WayAnalyzer.

La classe WayLayerGenerator ha il metodo **FindTheWay** per trovare il percorso dal punto di partenza al target. Per creare un'istanza della classe WayLayerGenerator, passiamo i WayOptions come parametri (tutti i parametri sono opzionali):

- StartPoint: Il punto di partenza

- GoalPoint: Il punto di destinazione

- Radius: Il raggio di ricerca

- Scale: La scala della griglia

- IsMoveOnlyRoad: Se cercare il percorso solo su strade

La caratteristica notevole qui è il parametro Scale. Se è specificato nel costruttore, fissiamo una scala costante per le ricerche successive. Se il parametro Scale non è impostato ma StartPoint e GoalPoint sono impostati, calcoliamo la scala come la distanza tra il punto di partenza e quello di destinazione divisa per 100. In tutti gli altri casi, il valore predefinito di Scale è 1. Per gli utenti esperti, è meglio impostare Scale o impostare direttamente StartPoint e GoalPoint per rappresentare in modo più efficiente strade e ostacoli sulla griglia (soprattutto se ce ne sono molti).

Per utilizzare il metodo FindTheWay, dobbiamo specificare i punti di partenza e di destinazione. Possiamo anche impostare il raggio di ricerca (la distanza a cui l'onda si propaga). Per impostazione predefinita, il raggio viene calcolato come la distanza tra il punto di partenza e quello di destinazione moltiplicata per 3. I punti di partenza e di destinazione possono essere vicini o molto lontani l'uno dall'altro, quindi in base alla distanza tra loro, calcoliamo la scala della nostra griglia. Se la scala corrente non corrisponde a quella precedente, ricalcoliamo la griglia. La scala può essere fissata utilizzando il parametro Scale. In questo caso, non viene calcolata e la griglia non viene ricalcolata.

Prima di avviare la ricerca, dobbiamo definire la mappa stradale e degli ostacoli utilizzando i metodi AddRoad e AddBlock corrispondenti della classe WayLayerGenerator.

Per il metodo **AddRoad**, dobbiamo specificare:

- startPoint: Il punto di partenza della strada

- endPoint: Il punto finale della strada

- velocity: La velocità di movimento sulla strada

Per il metodo **AddBlock**, dobbiamo specificare:

- x: La coordinata x dell'angolo in alto a sinistra del blocco

- y: La coordinata y dell'angolo in alto a sinistra del blocco

- sizeX: La dimensione sull'asse x

- sizeY: La dimensione sull'asse y

Questi metodi ci consentono di definire la mappa stradale e degli ostacoli prima di avviare il processo di ricerca del percorso.

## Code examples

Ecco alcuni esempi di codice che illustrano come impostare strade e ostacoli nell'algoritmo di ricerca del percorso e trovare il percorso ottimale.

Esempio 1: Trovare un percorso tra i punti di partenza e di destinazione.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Esempio 2**: Impostazione del parametro scala e avere coordinate negative per il punto.

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Esempio 3**: Impostazione del parametro IsMoveOnlyRoad e raggio di ricerca.

```
WayOptions mapGeneratorOptions = new WayOptions();
mapGeneratorOptions.IsMoveOnlyRoad = true;
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddRoad(new Point(100, 100), new Point(140, 150), 10);
generator.AddRoad(new Point(140, 150), new Point(190, 100), 10);
Point startPoint = new Point(100, 100);
Point goalPoint = new Point(190, 100);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 100);
```

**Esempio 4**: Impostazione del parametro scala per una ricerca più veloce.

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**Esempio 5**: Esempio di ricerca multipla.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddBlock(200, 1700, 1500, 100, 0);
generator.AddBlock(1700, 200, 100, 1600, 0);
generator.AddBlock(200, 200, 1500, 100, 0);
generator.AddRoad(new Point(1000, 1150), new Point(200, 600), 10);
generator.AddRoad(new Point(50, 450), new Point(150, 1850), 10);

Point startPoint = new Point(1000, 1000);
Point goalPoint = new Point(1900, 1000);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 3500);

Point startPoint = new Point(50, 50);
Point goalPoint = new Point(70, 70);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

Questi esempi di codice costruiscono e visualizzano i percorsi stradali sulla mappa per punti specificati, utilizzando informazioni sulle strade e il generatore di livelli di percorso.

**In sintesi**, l'optimal path finder è un potente strumento per analizzare le reti stradali e determinare i percorsi più efficienti tra punti su una mappa. Tiene conto di vari fattori come i tipi di strada, gli ostacoli e diverse velocità per calcolare il percorso ottimale. Con la possibilità di cercare percorsi sia su strade che fuoristrada, nonché controllare il raggio di ricerca e regolare le prestazioni e la precisione, questo algoritmo fornisce una soluzione versatile per l'ottimizzazione del percorso. Considerando diversi modi di trasporto e regolando i set di strade e ostacoli di conseguenza, può essere utilizzato in vari scenari come la pianificazione delle consegne o l'ottimizzazione dei tragitti casa-lavoro.