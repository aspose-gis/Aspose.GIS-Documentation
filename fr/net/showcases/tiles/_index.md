---
title: "Draw a map. A sliding map with tiles."
type: docs
url: /fr/net/showcases/sliding-map-with-tiles/
description: "Comment dessiner des tuiles et construire une carte glissante à partir d'elles."
weight: 80
aliases:
 - /fr/net/showcases/tiles/
---
# Draw a map. A sliding map with tiles.
Dans cet article, nous voulons montrer comment, en utilisant la bibliothèque [Aspose.GIS](https://www.nuget.org/packages/Aspose.GIS/) et des données publiques, vous pouvez construire une carte glissante qui sera générée en temps réel. Grâce à la nouvelle fonctionnalité de la bibliothèque, nous pouvons maintenant interroger les données SIG depuis la base de données via une requête SQL. Voici ce que nous devrions obtenir comme résultat :

![Result](result.png)

Repository source code [here](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest).

## Data preparation.

Tout d'abord, nous aurons besoin d'informations géospatiales que nous pourrons charger dans la base de données. L'une des sources populaires de telles informations est `OpenStreetMap`, utilisons-la donc. La manière la plus pratique, à mon avis, consiste à extraire les données au format pbf à partir de la ressource publique https://download.geofabrik.de/ . Par exemple, téléchargeons [Hungary](https://download.geofabrik.de/europe/hungary-latest.osm.pbf).

À l'étape suivante, nous avons besoin d'une instance fonctionnelle de `PostGIS`. Bien sûr, vous pouvez utiliser une version installée localement de `PostgreSQL`, mais je trouve très pratique d'utiliser des conteneurs Docker. Installons PostGIS en utilisant un fichier docker compose :

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

Le volume `d:\local_folder:/usr/share/gisdata` est nécessaire pour charger les données SIG à partir de la machine locale.

Ensuite, lançons notre conteneur :

```bash
docker compose up
```

Connectez-vous à l'instance de base de données en utilisant `pgAdmin` et créez la base de données Hungary :

![Create DB](create_db.png)

ou via la commande SQL :

```sql
CREATE DATABASE Hungary;
```

Ajoutez les extensions nécessaires à cette base de données :

![Extentions](add_extention.png)

Il s'agira des extensions `postgis` et `hstore`. hstore est une extension qui vous permet d'utiliser le type de données clé-valeur. OpenStreetMap utilise largement ce type pour décrire les attributs qui ne relèvent pas de la catégorie principale, et donc aucun champ distinct n'est créé pour eux, mais ils sont stockés dans le champ tags.

Il existe également une version SQL-like des commandes :

```sql
CREATE EXTENSION IF NOT EXISTS hstore;
CREATE EXTENSION IF NOT EXISTS postgis;
```

Connectons-nous maintenant au conteneur, dans mon cas c'est `local_folder-postgis-1` :

```bash
docker exec -it local_folder-postgis-1 sh
```

Et installez le programme qui importera les données du fichier `pbf` dans la base de données :

```bash
apt-get update && apt-get install -y osm2pgsql
```

Assurez-vous que le fichier `hungary-latest.osm.pbf` se trouve dans votre dossier `local_folder`, puis exécutez la commande d'importation :

```bash
osm2pgsql --create --database=Hungary --user=gis --password --host=localhost --port=5432 --hstore /usr/share/gisdata/hungary-latest.osm.pbf
```

Dans le cas de la Hongrie, cela m'a pris une minute et demie pour terminer cette commande. L'option `--create` signifie le mode de création simple d'une nouvelle base de données. D'ailleurs, en plus de tout le reste, il existe également le mode `--append`, qui permet de mettre à jour les données si elles ont changé :

```bash
osm2pgsql --append --slim OSMFILE
```

L'option `--hstore` indique à l'application de créer également un champ `tags` de type hstore pour stocker des informations supplémentaires sur les entités et les géométries.

## Back-end

Nos données sont donc prêtes à être utilisées. L'étape suivante sur la voie de la création d'une carte consiste à créer le back-end. Le but de notre back-end est de générer des `tiles` spéciaux, généralement de taille `256*256`, à partir desquels, comme une mosaïque, la carte sera assemblée dans le navigateur. Chaque tuile est identifiée de manière unique par une combinaison de paramètres tels que Z, qui est le degré de zoom avant/arrière de la carte, X est la ligne dans le tableau des tuiles et Y est la colonne. Vous pouvez en savoir plus sur la nature des tuiles [here](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames).

Notre backend sera sur ASP.NET Core en conséquence, commençons donc par créer le projet. Créons un projet basé sur le modèle `ASP.NET Core MVC` préinstallé dans `Visual Studio`.

Installez ensuite le package NuGet `Aspose.GIS` dans le projet qui générera les tuiles :

```cmd
dotnet add package Aspose.GIS --version 24.6.0
```

Nettoyez le projet des fichiers inutiles. De sorte que la structure ressemble approximativement à celle illustrée ci-dessous :

![Solution explorer](project.png)

Supprimez ensuite le contenu du dossier wwwroot/lib, car nous allons installer nos dépendances via `libman`. Voici la structure du fichier `libman.json` :
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


Ajout des dépendances client dans le fichier `_Layout.cshtml` :

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

Et modifiez également `Index.cshtml` :

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

Dans ce cas, `bootstrap-reboot.min.css` réinitialise les paramètres de style par défaut et `leaflet.min.js` est responsable du rendu de la carte, c'est-à-dire de l'assemblage des pièces à partir des tuiles dans le navigateur.
Définissons la hauteur du bloc de la carte sur la hauteur totale de la zone visible dans le fichier `map.css` :

```css
#map {
    min-height: 100vh;
}
```

Le contenu du fichier `map.js` est également assez simple, mais un peu plus intéressant :

```javascript
var map = L.map('map').setView([47.59995, 19.36623], 13);
const tiles = L.tileLayer('/tiles/{z}/{x}/{y}.png', {
    maxZoom: 19,
    minZoom: 11
}).addTo(map);
```

Ici, nous utilisons l'API de la bibliothèque leaflet, où nous spécifions l'ID du bloc de carte `'map'`, puis dans la méthode `setView` nous définissons les coordonnées du lieu à partir duquel le chargement initial de la carte commencera et également l'échelle, par exemple 13. Notez la méthode `tileLayer`, elle accepte une chaîne de modèle pour la demande de tuile au serveur. Cette adresse peut être soit absolue pour accéder aux serveurs de tuiles tiers, soit relative comme dans notre cas. La route `'/tiles/{z}/{x}/{y}.png'` n'a pas encore été implémentée par nous et c'est la partie la plus importante de notre récit que nous devons encore implémenter.

Pour implémenter le gestionnaire de requête pour la génération de tuiles, définissons d'abord une route distincte dans le fichier `Program.cs` :

```csharp
app.MapControllerRoute(name: "tiles",
  pattern: "tiles/{z}/{x}/{y}.png",
  defaults: new { controller = "Tiles", action = "Index" });

app.MapControllerRoute(
  name: "default",
  pattern: "{controller=Home}/{action=Index}/{id?}");
```

Ici, deux routes sont définies, la première pour les tuiles et la seconde est le route par défaut.
Dans l'expression `WHERE`, nous spécifions que nous voulons récupérer toutes les géométries de la table qui intersectent avec la zone d'enveloppe en utilisant la fonction `ST_Intersects`.

Il est très important qu'à ce stade de l'intégration de la base de données, la bibliothèque peut lire les géométries au format `WKB`, mais il est préférable d'utiliser `EWKB`, c'est-à-dire Extended Well-Known Binary, alors il ne sera pas nécessaire de transmettre les informations du système de coordonnées spatiales comme un champ distinct car elles seront déjà intégrées dans les informations de la géométrie. Pour cela, nous utilisons la fonction `ST_AsEWKB`.

La fonction `ST_ClipByBox2D` est utilisée pour découper les géométries qui dépassent les limites de la boîte englobante.

Bien, maintenant c'est le moment clé, comment exécuter la requête et obtenir une couche avec un ensemble d'entités qui seront rendues sur la tuile. C'est assez simple :

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

Nous avons reçu une seule couche qui contient toutes les géométries intersectant notre tuile.

Ok, maintenant nous pouvons colorer un peu la carte, comme des villes, des étendues d'eau ou des forêts. Pour ce faire, nous devons diviser notre couche unique en couches indépendantes distinctes qui correspondent à des critères spécifiques, tels que des forêts ou des rivières. Voici un exemple :

```csharp
var cities = inputLayer.Where(x => x.GetValue<string>("place") == "city");
citiesLayer = CopyToNewLayer(cities, inputLayer);

var forest = inputLayer.Where(x => x.GetValue<string>("landuse") == "forest");
forestLayer = CopyToNewLayer(forest, inputLayer);

var water = inputLayer.Where(x => !x.IsValueNull("water"));
waterLayer = CopyToNewLayer(water, inputLayer);
```

Vous verrez ci-dessous comment nous utiliserons ces couches. La fonction `CopyToNewLayer` est auxiliaire, elle aide à créer de nouvelles couches ; pour cet article, elle n'est pas d'une grande importance, vous pouvez consulter sa mise en œuvre dans le référentiel que j'ai mentionné au début de l'article.

Et maintenant nous devons juste rendre tout cela dans une tuile PNG et la renvoyer au client. Voici un exemple de code :

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

Ici, un objet `Map` est créé avec la taille de tuile standard de 256x256. Essentiellement, une `Map` est une toile pour rendre la tuile. Ensuite, nous initialisons un objet spécial pour l'étiquetage, auquel des règles pour le rendu du texte sur les formes géométriques dessinées sont transmises, par exemple, les numéros de maison, les noms de rue, etc. Dans ce cas, si ce n'est pas un polygone et/ou que l'attribut `addr:housenumber` est vide, les données seront prises à partir de l'attribut `name`.

Un point important est que l'objet Map doit explicitement spécifier le système de coordonnées dans lequel il va rendre :

```csharp
map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
```

Ensuite, nous devons définir la zone réelle de la tuile qui doit être rendue, et non la zone étendue que nous avons demandée à la base de données. Pour ce faire, nous définissons explicitement la zone de rendu via la propriété `Extent` :

```csharp
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);
```

Et puis nous ajoutons séquentiellement des couches à la tuile. La première est ajoutée en dessous de toutes les autres et la dernière est au-dessus.

Enfin, nous devons juste rendre la tuile sous forme de flux d'octets en mémoire, puis réinitialiser le flux au début et transmettre le flux à la plateforme ASP.NET Core pour un transfert ultérieur au client :

```csharp
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

pngStream.Seek(0, SeekOrigin.Begin);

return File(pngStream, "image/png");
```

Espérons que nous avons pu vous transmettre les idées et techniques de base de la construction de cartes. Nous vous souhaitons bonne chance dans vos expériences.