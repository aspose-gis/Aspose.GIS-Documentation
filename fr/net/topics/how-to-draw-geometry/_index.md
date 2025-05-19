---
title: "Comment dessiner de la géométrie sur une carte"
type: docs
url: /fr/net/how-to-draw-geometry
weight: 70
---

Pour créer et afficher des objets géométriques sur une carte, vous devez commencer par **créer un objet géométrique**. Il existe deux méthodes que vous pouvez utiliser :

- **Constructeur pour chaque type de caractéristique géométrique**
Cette méthode consiste à utiliser un constructeur personnalisé pour chaque type de caractéristique géométrique. Par exemple, pour créer un point, vous utiliserez le code suivant :

```
Point point = new Point(40.7128, -74.006);
```

Cependant, cette méthode peut devenir difficile et encombrante à gérer lors de la création d’objets complexes tels que des polylignes ou des collections. Par conséquent, le développeur peut devoir ajouter de nombreuses lignes de code, ce qui réduit la lisibilité du code. Assurer l’intégrité des données pendant l’initialisation peut également être difficile. Par exemple, considérez l’exemple suivant qui crée un polygone avec un trou à l’intérieur :

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

Un autre inconvénient de cette approche est le manque d’uniformité des données pour l’initialisation. Vous ne pouvez pas créer un référentiel de constantes ou de fichiers dans votre projet.

- **WKT (Well-Known Text)**
Cette méthode consiste à générer une géométrie à partir du WKT (Well-Known Text), qui offre une manière standardisée de créer des géométries. Le code suivant montre comment créer un point et une ligne :

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

Bien que cette approche puisse légèrement réduire les performances en raison de la nécessité d’analyser la chaîne, elle simplifie la création d’objets plus complexes.

Vous pouvez trouver plus de détails sur WKT dans l’article suivant : « Exporter et importer des données depuis/vers WKT et WKB ».

Affichage d’objets géométriques sur la carte
Une fois que vous avez créé un objet géométrique, l’étape suivante consiste à l’afficher sur la carte. Bien que la carte puisse afficher des calques chargés à partir de diverses sources et formats, le InMemoryLayer est un calque qui ne nécessite pas de source.

**Pour afficher votre objet géométrique**, vous pouvez créer un InMemoryLayer et ajouter l’objet :

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

Maintenant, vous pouvez **afficher ce calque sur la carte et créer un fichier dans l’un des formats pris en charge**, tels que SVG, avec le code suivant :

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

Une fois que vous avez ajouté le calque et l’avez affiché sur la carte, vous pouvez l’enregistrer dans n’importe lequel des formats pris en charge. Dans cet exemple, le format SVG est choisi pour éviter les problèmes potentiels avec la prise en charge de Bitmap. Il est important de noter que Net 6.0 a une prise en charge limitée de Bitmap, ce qui peut entraîner des restrictions telles que l’impossibilité de rendre des images Bitmap à l’aide de Blazor WebAsm sur le côté client. Par conséquent, lors du choix d’un format pour enregistrer votre carte, il est important de tenir compte des limitations de la plateforme cible et de sélectionner un format qui lui soit compatible.

L’article explique comment créer et afficher des objets géométriques sur une carte avec un style par défaut et simple. Cependant, la bibliothèque Aspose offre une large gamme d’options de style qui peuvent être personnalisées pour répondre à vos besoins. Pour explorer ces options, nous vous recommandons de consulter la [documentation Aspose.MapRendering]( https://docs.aspose.com/gis/net/map-rendering/), qui fournit des informations détaillées sur la façon d’utiliser différentes techniques de style pour améliorer l’attrait visuel de votre carte.

**En résumé**, pour créer des objets géométriques sur une carte, vous pouvez utiliser un constructeur pour chaque type de caractéristique géométrique ou générer une géométrie à partir du WKT. Pour afficher l’objet, placez-le sur un calque et affichez le calque sur une carte avec un style par défaut. Enregistrez la carte dans un format pris en charge, tel que SVG, et utilisez notre bibliothèque pour explorer les options de style. De plus, notre bibliothèque offre la possibilité de voir un exemple terminé en cliquant sur le [lien]( https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer) fourni dans la documentation, ce qui peut vous aider à comprendre comment implémenter ces techniques dans vos propres projets.
