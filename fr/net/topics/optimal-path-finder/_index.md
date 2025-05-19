---
title: "Optimal Path Finder"
type: docs
url: /fr/net/optimal-path-finder
weight: 70
---

## Summary

La recherche du chemin le plus court sur un réseau routier est un processus d'analyse visant à déterminer la manière la plus efficace de voyager entre des points sur une carte. Cet outil peut être utile pour créer des itinéraires optimaux avec plusieurs arrêts ou mesurer la distance et le temps de trajet entre différents lieux. À chaque appel, notre technologie peut trouver des itinéraires optimaux pour un ou plusieurs véhicules. Par exemple, elle peut aider les conducteurs à trouver les meilleurs itinéraires pour livrer des marchandises ou déterminer la distance de déplacement optimale du domicile au travail pour différents passagers.

## Algorithm Capabilities

Notre bibliothèque offre la possibilité de construire le chemin le plus **optimal entre deux points** sur une carte. Elle possède les principales fonctionnalités suivantes :

1. Recherche du chemin optimal sur la carte, en tenant compte des sentiers et des obstacles : Nous prenons en compte non seulement les routes mais aussi les chemins hors route tels que les sentiers, les passages piétons et les obstacles qui peuvent affecter le choix du chemin optimal.

2. Recherche du chemin optimal uniquement sur les routes : Si vous devez trouver un itinéraire exclusivement sur les routes, nous fournissons cette fonctionnalité. Ceci est utile, par exemple, pour les véhicules autorisés à rouler uniquement sur les routes.

3. Définition de différentes vitesses pour les routes : Nous avons la possibilité d'attribuer des vitesses différentes à différentes routes. Par exemple, des vitesses plus élevées peuvent être définies pour les principales autoroutes et des vitesses plus faibles pour les voies étroites.

4. Définition d'obstacles rectangulaires : Vous pouvez définir des obstacles rectangulaires sur la carte qui doivent être pris en compte lors de la construction du chemin optimal. Ceci est utile lorsqu'il existe des obstacles connus tels que des bâtiments ou des lacs (leur approximation).

5. Limitation du rayon de recherche pour les routes : Vous pouvez restreindre le rayon de recherche pour les routes afin de réduire le temps de recherche et de vous concentrer uniquement sur une zone spécifique.

6. Contrôle des performances et de la précision : Nous fournissons la possibilité de contrôler les performances et la précision de l'algorithme. Vous pouvez l'affiner pour atteindre l'équilibre souhaité entre la vitesse de recherche et la précision de la construction de l'itinéraire.

Ensuite, nous fournirons une description plus détaillée de chacune de ces fonctionnalités et examinerons des exemples de leurs applications.

## Approach to Solution

Bien que la recherche de chemin soit une tâche non triviale, il existe plusieurs bons algorithmes fiables qui sont reconnus dans la communauté du développement.

Dans notre implémentation, nous avons utilisé un algorithme de Lee modifié. Nous disposons d'une grille de cellules sur le plan. À partir du point de départ, une vague se propage dans 8 directions (y compris les diagonales) vers les cellules voisines, calculant le temps nécessaire pour atteindre chacune d'entre elles. Une cellule voisine peut contenir un obstacle ou une route. Les routes peuvent avoir différents coefficients de vitesse. Ainsi, nous "marquons" notre grille avec le temps qu'il faut pour atteindre chaque cellule à partir de la cellule de départ dans un certain rayon ou jusqu'à ce que l'on atteigne le point d'arrivée. Si nous atteignons le point d'arrivée, nous construisons un chemin inverse en utilisant notre grille.

Pour déterminer le meilleur itinéraire sur le réseau routier, plusieurs étapes doivent être franchies. Tout d'abord, vous devez définir les routes et spécifier la vitesse de déplacement sur chacune d'entre elles. Vous devez également tenir compte de la présence d'obstacles artificiels et naturels qui peuvent affecter le parcours du chemin. Après cela, vous devez spécifier les points de départ et d'arrivée de la recherche. Une fois ces étapes préliminaires terminées, vous pouvez passer à la recherche réelle du chemin. Le résultat sera un chemin représenté, par exemple, sous forme de liste de coordonnées de points.

Il est important de noter que le meilleur itinéraire peut dépendre du mode de transport choisi, car la vitesse de déplacement et l'ensemble des obstacles peuvent varier. Par conséquent, différents ensembles de routes et d'obstacles doivent être utilisés pour chaque type de transport lors de la recherche du chemin optimal.

## Demo Project on GitHub

Pour mieux comprendre les fonctionnalités de notre bibliothèque, considérons [un exemple de son utilisation](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths). Ce code illustre comment configurer des routes et des obstacles dans l'algorithme de recherche de chemin et trouver le meilleur itinéraire.

L'exemple se compose des étapes suivantes :

1. Création d'une liste d'informations sur les routes (RoadInfo), qui comprend des informations sur le segment routier (Segment) et la vitesse de déplacement (Velocity).
2. Ajout de routes rapides à la liste.
3. Ajout de routes circulaires lentes à la liste.
4. Création d'un générateur de couches de voies (WayLayerGenerator) et ajout de routes au générateur.
5. Recherche de plusieurs chemins du point de départ (startPoint) aux points d'arrivée (goalPoint01, goalPoint02, goalPoint03) en utilisant le rayon spécifié (radius).
6. Préparation d'une couche routière (roadsLayer) pour l'affichage sur la carte et ajout d'objets routiers.
7. Préparation d'une couche de voies (wayLayer) pour l'affichage sur la carte et création d'objets géométriques pour chaque chemin trouvé.
8. [Affichage de la carte](https://docs.aspose.com/gis/net/how-to-draw-geometry/) à l'aide de la fonction ShowMap, enregistrement de la carte au chemin spécifié.

Ce code construit et affiche des chemins routiers sur la carte pour les points spécifiés en utilisant des informations routières et le générateur de couches de voies.

## Search Options

La recherche de chemin est effectuée à l'aide de la classe **WayLayerGenerator** située dans l'espace de noms Aspose.Gis.GeoTools.WayAnalyzer.

La classe WayLayerGenerator possède la **méthode FindTheWay** pour trouver le chemin du point de départ à la cible. Pour créer une instance de la classe WayLayerGenerator, nous passons les options WayOptions en tant que paramètres (tous les paramètres sont facultatifs) :

- StartPoint : Le point de départ

- GoalPoint : Le point cible

- Radius : Le rayon de recherche

- Scale : L'échelle de la grille

- IsMoveOnlyRoad : Indique s'il faut rechercher le chemin uniquement sur les routes

La caractéristique notable ici est le paramètre Scale. S'il est spécifié dans le constructeur, nous fixons une échelle constante pour les recherches ultérieures. Si le paramètre Scale n'est pas défini mais que StartPoint et GoalPoint sont définis, nous calculons l'échelle comme la distance entre le point de départ et le point d'arrivée divisée par 100. Dans tous les autres cas, la valeur par défaut de Scale est de 1. Pour les utilisateurs expérimentés, il est préférable de définir Scale ou de définir directement StartPoint et GoalPoint pour représenter au mieux les routes et les obstacles sur la grille (en particulier s'il y en a beaucoup).

Pour utiliser la méthode FindTheWay, nous devons spécifier les points de départ et d'arrivée. Nous pouvons également définir le rayon de recherche (la distance à laquelle la vague se propage). Par défaut, le rayon est calculé comme la distance entre le point de départ et le point d'arrivée multipliée par 3. Les points de départ et d'arrivée peuvent être proches ou très éloignés l'un de l'autre, nous calculons donc l'échelle de notre grille en fonction de la distance qui les sépare. Si l'échelle actuelle ne correspond pas à la précédente, nous recalculons la grille. L'échelle peut être fixée à l'aide du paramètre Scale. Dans ce cas, elle n'est pas calculée et la grille n'est pas recalculée.

Avant de commencer la recherche, nous devons définir la carte routière et des obstacles à l'aide des méthodes AddRoad et AddBlock correspondantes de la classe WayLayerGenerator.

Pour la **méthode AddRoad**, nous devons spécifier :

- startPoint : Le point de départ de la route

- endPoint : Le point d'arrivée de la route

- velocity : La vitesse de déplacement sur la route

Pour la **méthode AddBlock**, nous devons spécifier :

- x : La coordonnée x du coin supérieur gauche du bloc

- y : La coordonnée y du coin supérieur gauche du bloc

- sizeX : La taille dans l'axe des x

- sizeY : La taille dans l'axe des y

Ces méthodes nous permettent de définir la carte routière et des obstacles avant de commencer le processus de recherche de chemin.

## Code examples

Voici quelques exemples de code qui illustrent comment configurer des routes et des obstacles dans l'algorithme de recherche de chemin et trouver le meilleur itinéraire.

Exemple 1 : Trouver un chemin entre les points de départ et d'arrivée.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Exemple 2**: Définir le paramètre d'échelle et avoir des coordonnées négatives pour le point.

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Exemple 3**: Définir le paramètre IsMoveOnlyRoad et le rayon de recherche.

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

**Exemple 4**: Définir le paramètre d'échelle pour une recherche plus rapide.

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**Exemple 5**: Exemple de recherche multiple.

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

Ces exemples de code construisent et affichent des chemins routiers sur la carte pour les points spécifiés, en utilisant des informations routières et un générateur de couches de voies.

**En résumé**, le chercheur de chemin optimal est un outil puissant pour analyser les réseaux routiers et déterminer les itinéraires les plus efficaces entre les points sur une carte. Il tient compte de divers facteurs tels que les types de routes, les obstacles et différentes vitesses pour calculer le chemin optimal. Avec la possibilité de rechercher des chemins à la fois sur les routes et hors route, ainsi que de contrôler le rayon de recherche et d'ajuster les performances et la précision, cet algorithme fournit une solution polyvalente pour l'optimisation des itinéraires. En tenant compte de différents modes de transport et en ajustant les ensembles de routes et d'obstacles en conséquence, il peut être utilisé dans divers scénarios tels que la planification de livraison ou l'optimisation des trajets domicile-travail. Les exemples de code et les explications fournis démontrent les capacités de l'algorithme et les étapes impliquées dans son utilisation. En fin de compte, le chercheur de chemin optimal offre un moyen robuste de trouver les itinéraires les plus efficaces et d'améliorer la navigation sur un réseau routier.