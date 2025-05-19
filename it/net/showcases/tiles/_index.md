---
title: "Disegna una mappa. Una mappa scorrevole con delle tessere."
type: docs
url: /it/net/showcases/sliding-map-with-tiles/
description: "Come disegnare le tessere e costruire una mappa scorrevole da esse."
weight: 80
aliases:
 - /it/net/showcases/tiles/
---
# Disegna una mappa. Una mappa scorrevole con delle tessere.
In questo articolo, vogliamo mostrare come, utilizzando la libreria [Aspose.GIS](https://www.nuget.org/packages/Aspose.GIS/) e dati pubblici, è possibile costruire una mappa scorrevole che verrà generata in tempo reale. Grazie alla nuova funzionalità della libreria, ora possiamo interrogare i dati GIS dal database tramite query SQL. Ecco cosa dovremmo ottenere come risultato:

![Risultato](result.png)

Repository del codice sorgente [qui](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest).

## Preparazione dei dati.

Innanzitutto, avremo bisogno di informazioni geospaziali che possiamo caricare nel database. Una delle fonti più popolari di tali informazioni è `OpenStreetMap`, quindi usiamolo. Il modo più conveniente, a mio parere, è estrarre i dati in formato pbf dalla risorsa pubblica https://download.geofabrik.de/ . Ad esempio, scarichiamo [Ungheria](https://download.geofabrik.de/europe/hungary-latest.osm.pbf).

Nella fase successiva, abbiamo bisogno di un'istanza funzionante di `PostGIS`. Naturalmente, puoi utilizzare una versione installata localmente di `PostgreSQL`, ma trovo molto conveniente utilizzare i container Docker. Installiamo PostGIS utilizzando un file docker compose:

```yaml
services:
  postgis:
    image: postgis/postgis
    environment:
      - POSTGRES_DB=gis
      - POSTGRES_USER=gis
      - POSTGRES_PASSWORD=password
    ports:
      - 5432:5432
    volumes:
      - d:\\local_folder:/usr/share/gisdata
```

Il volume `d:\local_folder:/usr/share/gisdata` è necessario per caricare i dati GIS dalla macchina locale.

Successivamente, eseguiamo il nostro container:

```bash
docker compose up
```

Connettiti all'istanza del database utilizzando `pgAdmin` e crea lì il database Ungheria:

![Crea DB](create_db.png)

o tramite il comando SQL:

```sql
CREATE DATABASE Hungary;
```

Aggiungi le estensioni necessarie a questo database:

![Estensioni](add_extention.png)

Queste saranno le estensioni `postgis` e `hstore`. hstore è un'estensione che consente di utilizzare il tipo di dati chiave-valore. OpenStreetMap utilizza ampiamente questo tipo per descrivere gli attributi che non rientrano nella categoria dei principali, quindi non vengono creati campi separati per essi, ma sono archiviati nel campo tags.

Esiste anche una versione simile a SQL dei comandi:

```sql
CREATE EXTENSION IF NOT EXISTS hstore;
CREATE EXTENSION IF NOT EXISTS postgis;
```

Ora connettiamoci al container, nel mio caso è `local_folder-postgis-1`:

```bash
docker exec -it local_folder-postgis-1 sh
```

E installa il programma che importerà i dati dal file `pbf` nel database:

```bash
apt-get update && apt-get install -y osm2pgsql
```

Assicurati che il file `hungary-latest.osm.pbf` si trovi nella tua cartella `local_folder` e quindi esegui il comando di importazione:

```bash
osm2pgsql --create --database=Hungary --user=gis --password --host=localhost --port=5432 --hstore /usr/share/gisdata/hungary-latest.osm.pbf
```

Nel caso dell'Ungheria, ci sono voluti un minuto e mezzo per completare questo comando. L'opzione `--create` significa la semplice creazione di un nuovo database. A proposito, oltre a tutto il resto, esiste anche la modalità `--append`, che consente di aggiornare i dati se sono cambiati:

```bash
osm2pgsql --append --slim OSMFILE
```

L'opzione `--hstore` dice all'applicazione di creare anche un campo `tags` di tipo hstore per archiviare informazioni aggiuntive sulle funzionalità e le geometrie.

## Back-end

Quindi, i nostri dati sono pronti per essere utilizzati. Il passo successivo verso la creazione di una mappa è la creazione del back-end. L'obiettivo del nostro back-end è generare speciali `tiles`, solitamente di dimensioni `256*256`, dai quali, come un mosaico, la mappa verrà assemblata nel browser. Ogni tile è identificato in modo univoco da una combinazione di parametri come Z, che è il grado di zoom in/out della mappa, X è la riga nell'array dei tile e Y è la colonna. Puoi leggere di più sulla natura delle tessere [qui](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames).

Il nostro backend sarà su ASP.NET Core di conseguenza, quindi iniziamo con la creazione del progetto. Quindi creiamo un progetto basato sul modello `ASP.NET Core MVC` preinstallato in `Visual Studio`.

Successivamente, installa il pacchetto NuGet `Aspose.GIS` nel progetto che genererà le tessere:

```cmd
dotnet add package Aspose.GIS --version 24.6.0
```

Pulisci il progetto dai file non necessari. In modo che la struttura sia approssimativamente come mostrato di seguito:

![Esplora soluzioni](project.png)

Quindi elimina i contenuti della cartella wwwroot/lib, poiché installeremo le nostre dipendenze tramite `libman`. Di seguito è riportata la struttura del file `libman.json`:
```json
{
  "version": "1.0",
  "defaultProvider": "cdnjs",
  "libraries": [
    {
      "library": "leaflet@1.9.4",
      "destination": "wwwroot/lib/leaflet/"
    },
    {
      "library": "bootstrap@5.3.3",
      "destination": "wwwroot/lib/bootstrap/",
      "files": [
        "css/bootstrap-reboot.min.css"
      ]
    }
  ]
}
```


Aggiunto le dipendenze client nel file `_Layout.cshtml`:

```razor
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>@ViewData["Title"] - Aspose.GIS.TilesTest</title>
    <link href="~/lib/bootstrap/css/bootstrap-reboot.min.css" rel="stylesheet" />
    @await RenderSectionAsync("Styles", required: false)
</head>
<body>
    @RenderBody()
    @await RenderSectionAsync("Scripts", required: false)
</body>
</html>
```

E modifica anche `Index.cshtml`:

```razor
@{
    ViewData["Title"] = "Home Page";
}

<div id="map"></div>

@section Styles {
    <link href="~/lib/leaflet/leaflet.min.css" rel="stylesheet" />
    <link href="~/css/map.css" rel="stylesheet" asp-append-version="true"/>
}

@section Scripts {
    <script src="~/lib/leaflet/leaflet.min.js"></script>
    <script src="~/js/map.js" asp-append-version="true"></script>
}
```

In questo caso, `bootstrap-reboot.min.css` reimposta le impostazioni di stile predefinite e `leaflet.min.js` è responsabile del rendering della mappa, ovvero dell'assemblaggio dei pezzi dai tile in una mappa.
Impostiamo l'altezza del blocco mappa all'altezza completa dell'area visibile nel file `map.css`:

```css
#map {
    min-height: 100vh;
}
```

Il contenuto del file `map.js` è anche piuttosto semplice, ma un po' più interessante:

```javascript
var map = L.map('map').setView([47.59995, 19.36623], 13);
const tiles = L.tileLayer('/tiles/{z}/{x}/{y}.png', {
    maxZoom: 19,
    minZoom: 11
}).addTo(map);
```

Qui utilizziamo l'API della libreria leaflet, dove specifichiamo l'id del blocco mappa `'map'`, quindi nel metodo `setView` impostiamo le coordinate del luogo da cui inizierà il caricamento iniziale della mappa e anche la scala, ad esempio 13. Nota il metodo `tileLayer`, accetta una stringa di modello per la richiesta del tile al server. Questo indirizzo può essere assoluto per accedere a server di tile di terze parti o relativo come nel nostro caso.

Per implementare l'handler della richiesta per la generazione dei tile, definiamo prima un percorso separato nel file `Program.cs`:

```csharp
app.MapControllerRoute(name: "tiles",
  pattern: "tiles/{z}/{x}/{y}.png",
  defaults: new { controller = "Tiles", action = "Index" });

app.MapControllerRoute(
  name: "default",
  pattern: "{controller=Home}/{action=Index}/{id?}");
```

Qui vengono definiti due percorsi, il primo per i tile e il secondo è quello standard. Nel caso di `MapControllerRoute`, l'ordine conta, quindi per evitare comportamenti imprevisti, vale la pena posizionare il percorso per i tile prima del percorso standard.

Successivamente, passiamo all'handler stesso. Crea il controller `TilesController.cs`:

```csharp
public async Task<ActionResult> Index(int z, int x, int y)
```

E così, ora abbiamo tutti i dati necessari per calcolare il bounding box coperto dal tile nel corrispondente sistema di coordinate. Nell'implementazione corrente, i nostri dati nel database sono archiviati nel sistema di coordinate Web Mercator. OpenStreetMap utilizza il sistema di coordinate Web Mercator.

```csharp
VectorLayer inputLayer;
using (var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary"))
{
  var builder = new DatabaseDataSourceBuilder();

  builder
    .FromQuery(query)
    .GeometryField("way")
    .AddAttribute("osm_id", AttributeDataType.Long)
    .AddAttribute("addr:housenumber", AttributeDataType.String)
    .AddAttribute("building", AttributeDataType.String)
    .AddAttribute("name", AttributeDataType.String)
    .AddAttribute("source", AttributeDataType.String)
    .AddAttribute("admin_level", AttributeDataType.Integer)
    .AddAttribute("place", AttributeDataType.String)
    .AddAttribute("landuse", AttributeDataType.String)
    .AddAttribute("water", AttributeDataType.String);
  conn.Open();

  var inputLayer = await builder.Build().ReadAsync(conn);
}
```

Abbiamo ricevuto un layer che contiene tutte le geometrie che intersecano il nostro tile.

Ok, ora possiamo colorare la mappa un po', come città, corpi idrici o foreste. Per fare ciò, dobbiamo rompere il nostro singolo layer in layer separati e indipendenti che corrispondano a criteri specifici, come foreste o fiumi. Ecco un esempio:

```csharp
var cities = inputLayer.Where(x => x.GetValue<string>("place") == "city");
citiesLayer = CopyToNewLayer(cities, inputLayer);

var forest = inputLayer.Where(x => x.GetValue<string>("landuse") == "forest");
forestLayer = CopyToNewLayer(forest, inputLayer);

var water = inputLayer.Where(x => !x.IsValueNull("water"));
waterLayer = CopyToNewLayer(water, inputLayer);
```

Di seguito vedrai come utilizzeremo questi layer. La funzione `CopyToNewLayer` è ausiliaria, aiuta a creare nuovi layer; per questo articolo, non è di grande importanza, puoi dare un'occhiata alla sua implementazione nel repository che ho menzionato all'inizio dell'articolo.

E ora dobbiamo solo renderizzare tutto in un tile PNG e restituirlo al client. Questo è un esempio di codice:

```csharp
using var map = new Map(256, 256);
var pngStream = new MemoryStream();
var labeling = new RuleBasedLabeling
{
  { x => x.GetValue<string>("source") == "polygon",  new SimpleLabeling("addr:housenumber") },
  LabelingRule.CreateElseRule(new SimpleLabeling("name"))
};

map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);            
map.Add(citiesLayer, new SimpleFill { FillColor = Color.PeachPuff }, labeling);
map.Add(forestLayer, new SimpleFill { FillColor = Color.PaleGreen }, labeling);
map.Add(waterLayer, new SimpleFill { FillColor = Color.SkyBlue }, labeling);
map.Add(buildingsLayer, new SimpleFill { FillColor = Color.SandyBrown }, labeling);
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

pngStream.Seek(0, SeekOrigin.Begin);

return File(pngStream, "image/png");
```

Qui viene creato un oggetto `Map` con le dimensioni standard del tile di 256x256. Fondamentalmente, una `Map` è una tela per il rendering del tile. Successivamente, inizializziamo uno speciale oggetto per l'etichettatura, a cui vengono passate regole per il rendering del testo su forme geometriche disegnate, ad esempio numeri di casa, nomi delle strade, ecc. In questo caso, se non è un poligono e/o l'attributo `addr:housenumber` è vuoto, i dati verranno presi dall'attributo `name`.

Un punto importante è che l'oggetto Map deve specificare esplicitamente il sistema di coordinate in cui renderà:

```csharp
map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
```

Successivamente, dobbiamo impostare la vera area del tile che dovrebbe essere renderizzata, non l'area espansa che abbiamo richiesto dal database. Per fare ciò, impostiamo esplicitamente l'area di rendering tramite la proprietà `Extent`:

```csharp
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);
```

E quindi aggiungiamo sequenzialmente i layer al tile. Il primo viene aggiunto sotto tutti gli altri e l'ultimo sopra.

Infine dobbiamo solo renderizzare il tile come uno stream di byte in memoria, quindi resettare lo stream all'inizio e passare lo stream alla piattaforma ASP.NET Core per un ulteriore trasferimento al client:

```csharp
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

pngStream.Seek(0, SeekOrigin.Begin);

return File(pngStream, "image/png");
```

Speriamo di essere stati in grado di trasmetterti le idee e le tecniche di base della costruzione di mappe. Ti auguriamo buona fortuna nei tuoi esperimenti.