---
title: "Mises à jour d'Aspose.GIS : Modification des entités et des géométries et sauvegarde des modifications dans la base de données."
type: docs
url: /fr/net/showcases/saving-changes-to-database/
description: "Cet article explore les améliorations récentes de la bibliothèque Aspose.GIS, en se concentrant sur les nouvelles fonctionnalités permettant de détecter et d'enregistrer les modifications de géométrie dans une application cartographique."
weight: 80
---
# Mises à jour d'Aspose.GIS : Modification des entités et des géométries et sauvegarde des modifications dans la base de données.

## Introduction

À la lumière des récents changements apportés à la bibliothèque [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis), il est important de souligner certains d'entre eux afin qu'ils ne passent pas inaperçus. Dans cet article, nous discuterons de la nouvelle capacité à détecter et à enregistrer les modifications apportées aux géométries et aux entités dans la base de données.

À titre d'exemple pour la démonstration, nous continuerons à travailler sur l'application décrite dans l'article ["Créer une carte. Une carte glissante avec des tuiles"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) et l'étendrons légèrement en ajoutant des fonctionnalités d'édition d'objets à la carte. L'ensemble de données reste le même que dans l'article précédent.

## Front-end

Pour la démonstration des capacités de modification de géométrie, nous avons choisi une extension open source populaire pour [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/).

Nous ajoutons cette bibliothèque via le fichier libman.json :
![Libman](libman.png)

Ensuite, nous connectons les styles et les scripts à la page :
```razor
@section Styles {
    <link href="~/lib/leaflet/leaflet.min.css" rel="stylesheet" />
    <link href="~/lib/contagt/leaflet-geoman-free/dist/leaflet-geoman.min.css" rel="stylesheet" />
    <link href="~/css/map.css" rel="stylesheet" asp-append-version="true"/>
}

@section Scripts {
    <script src="~/lib/leaflet/leaflet.js"></script>
    <script src="~/lib/contagt/leaflet-geoman-free/dist/leaflet-geoman.min.js"></script>
    <script src="~/js/map.js" asp-append-version="true"></script>
}
```

À des fins de démonstration, nous limiterons les capacités d'édition aux bâtiments uniquement. L'utilisateur clique sur le bouton gauche de la souris sur la carte et si un bâtiment se trouve à cet emplacement, il est mis en évidence et devient disponible pour l'édition. Ceci est réalisé en superposant une couche supplémentaire au-dessus des tuiles.

Lorsque l'utilisateur clique sur la carte, la bibliothèque Leaflet calcule les coordonnées géospatiales du clic. Nous envoyons ces coordonnées au back-end et recherchons dans la base de données les géométries qui intersectent avec le point cliqué. S'il y a des bâtiments parmi ces géométries, nous les retournons.

Les bâtiments sont renvoyés par le back-end au format `GeoJSON` et ajoutés à la carte sous forme de couche distincte pour l'édition. Voici comment nous gérons le clic :
```javascript
var featuresLayer = L.featureGroup().addTo(map);

map.on('click', function (e) {
    var latlng = e.latlng;
    var featureFound = false;

    console.log(latlng.lat + ' ' + latlng.lng);

    featuresLayer.eachLayer(function (layer) {
        if (layer.getBounds && layer.getBounds().contains(latlng)) {
            featureFound = true;
            return;
        }
    });

    if (!featureFound) {
        loadGeoJSON(latlng.lat, latlng.lng)
            .then((addedFeatureLayer) => {
                if (addedFeatureLayer) {
                    addedFeatureLayer.addTo(featuresLayer);
                    addedFeatureLayer.pm.enable();
                    console.log('Feature added.');
                } else {
                    console.log('No feature to add.');
                }
            });
    }

    featureFound = false;
});
```

Nous avons un groupe de couches persistant pour les géométries modifiables, `featuresLayer`, qui a été ajouté à la carte. Nous vérifions si le clic a été effectué sur une géométrie déjà chargée et, sinon, nous envoyons une requête au back-end pour charger les polygones représentant les bâtiments. Les calques de fonctionnalités chargés sont ajoutés à featuresLayer et le mode d'édition est activé.

Voici la fonction pour charger des fonctionnalités et convertir depuis `GeoJSON` :
```javascript
function loadGeoJSON(lat, lng) {
    return fetch(`/features?lat=${lat}&lng=${lng}`)
        .then(response => response.json())
        .then(data => {
            if (data && data.features && data.features.length > 0) {
                return L.geoJSON(data);

            } else {
                return null;
            }
        })
        .catch(error => console.error('Error loading a feature:', error));
}
```

Après la session d'édition, l'utilisateur clique sur un bouton `Save` personnalisé :

![Save](save-btn.png)

Actualisez la page et voyez les modifications :

![Changes](changes.png)

Malheureusement, la fonction `tiles.redraw()` ne fonctionne pas correctement car les tuiles précédemment chargées sont mises en cache, ce qui nécessite un actualisation forcée de la carte via `Ctrl + F5`.

Voici le gestionnaire pour appuyer sur le bouton d'enregistrement :
```javascript
function saveResult() {
    if (featuresLayer.getLayers().length === 0) {
        console.log('There are no layers to send to the server.');
        return;
    }
    sendGeoJSONToServer()
        .then(() => {
            console.log('clear and update map');
            featuresLayer.clearLayers();
            tiles.redraw();
        });
}

function sendGeoJSONToServer() {
    var geojsonData = featuresLayer.toGeoJSON();

    return fetch('/features', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/geo+json'
        },
        body: JSON.stringify(geojsonData)
    })
        .then(data => {
            console.log('The data has been successfully sent to the server.');
        })
        .catch(error => {
            console.error('Error when sending GeoJSON:', error);
        });
}
```

## Back-end

Ici, nous ajoutons un nouveau contrôleur, `FeaturesController`, où nous créons un gestionnaire pour extraire les maisons/entités en fonction des coordonnées envoyées.

La requête SQL est la suivante :

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

Les coordonnées sont transformées en un point, indiquant le système de coordonnées de la requête client d'origine (WGS 84), puis traduites dans le système dans lequel les données de la base de données sont présentées (Web Mercator). Nous recherchons des intersections avec ce point pour les géométries marquées comme bâtiments.

L'exécution de la requête et l'envoi des données au client se fait de manière similaire à ce que nous avons discuté dans l'article précédent :
```csharp
VectorLayer inputLayer;

using (var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary"))
{
    var dataSource = Drivers.PostGis
        .FromQuery(query)
        .GeometryField("way")
        .AddAttribute("osm_id", AttributeDataType.Long)
        .AddAttribute("name", AttributeDataType.String)
        .AddAttribute("building", AttributeDataType.String)
        .Build();

    conn.Open();

    inputLayer = await dataSource.ReadAsync(conn);
}

var jsonStream = new MemoryStream();

inputLayer.SaveTo(AbstractPath.FromStream(jsonStream), Drivers.GeoJson);

var result = Encoding.UTF8.GetString(jsonStream.ToArray());

return new ContentResult()
{
    Content = result,
    ContentType = "application/geo+json"
};
```
Avec une petite différence : nous enregistrons notre couche InMemory au format GeoJSON en mémoire sous forme de flux, puis le convertissons en chaîne et l'envoyons au client.

Nous arrivons maintenant à l'essence des mises à jour dans Aspose.GIS — l'enregistrement des modifications dans la base de données. La méthode `Edit()` gère cela. Nous lisons le corps de la requête pour le charger entièrement en mémoire et le lisons sous forme de flux :
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync();
Request.Body.Position = 0;
```
Ensuite, nous lisons les fonctionnalités modifiées au format GeoJSON :
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
L'étape suivante consiste à effectuer une série de transformations avant d'envoyer les modifications à la base de données :
```csharp
var transformer = SpatialReferenceSystem.Wgs84.CreateTransformationTo(SpatialReferenceSystem.WebMercator);

foreach (var feature in inputLayer)
{
    feature.Geometry = transformer.Transform(feature.Geometry);
    ((Geometry)feature.Geometry).HasZ = false;
}

foreach (var feature in inputLayer)
{
    var replacingId = feature.GetValue<long>("osm_id");
    var toReplaceIndex = editLayer.TakeWhile(x => x.GetValue<long>("osm_id") != replacingId).Count();
    editLayer.ReplaceAt(toReplaceIndex, feature);
}

await dataSource.SubmitChangesAsync(editLayer, conn, transaction);

transaction.Commit();
```
Leaflet génère des géométries dans le système de coordonnées WGS 84, cependant, le schéma de la base de données nécessite un stockage en Web Mercator. Pour transformer vers le système Web Mercator, nous créons un objet `transformer` spécial et l'utilisons pour la conversion.

De plus, leaflet remplit le troisième paramètre des coordonnées de géométrie Z avec une valeur de 0. Cependant, ce paramètre n'est pas pris en compte dans notre schéma de base de données, nous supprimons donc sa présence en définissant la valeur de `HasZ` sur false.

Le point final est l'application des modifications en remplaçant la fonctionnalité existante par celle reçue du client qui a le même osm_id. Cette opération conduira à la détection des changements par rapport aux instances plus anciennes de la fonctionnalité. Au moment d'appeler `SubmitChangesAsync`, le processus de détection des changements se produira et les commandes INSERT, DELETE et UPDATE seront envoyées à la base de données en fonction de vos modifications.

Merci d'avoir lu jusqu'à la fin. Tout le code sera disponible dans le référentiel suivant : [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)