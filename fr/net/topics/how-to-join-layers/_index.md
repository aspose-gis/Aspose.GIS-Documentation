---
title: "Comment joindre des couches en utilisant la géométrie ou les attributs"
type: docs
url: /fr/net/how-to-join-layers
weight: 70
---

## Résumé

Dans un SIG, les jointures sont un mécanisme puissant pour combiner des informations provenant de différentes couches en fonction d'un attribut commun ou d'une relation spatiale. Les jointures vous permettent de fusionner des données d'attributs d'une couche (la couche source) avec une autre couche (la couche cible) à l'aide d'un champ commun ou d'un emplacement spatial. La première est la jointure de données par clé (attribut dans le tableau). En utilisant un champ commun, tel qu'une clé unique, vous pouvez relier des enregistrements dans un tableau à des enregistrements dans un autre tableau. La deuxième approche consiste à joindre les données par emplacement (spatialement). Nous prenons en charge les deux approches et vous offrons la possibilité de les utiliser en fonction de vos besoins.

Supposons que vous ayez reçu des données décrivant le pourcentage de variation de la population pour différents districts, et que vous souhaitiez générer plusieurs cartes de croissance démographique basées sur ces informations. Bien que vos données démographiques soient stockées dans un tableau dans votre base de données et partagent un champ commun avec votre couche, vous pouvez joindre ces données à vos objets géographiques et utiliser des champs supplémentaires pour l'étiquetage, la catégorisation, l'interrogation ou l'analyse d'objets de couche.

Généralement, vous effectuez des jointures de données en fonction d'une valeur de champ qui existe dans les deux tableaux. Les noms des champs n'ont pas nécessairement besoin de correspondre, mais les types de données doivent être identiques - nombres avec nombres, chaînes avec chaînes, et ainsi de suite. Vous pouvez exécuter la jointure de données à l'aide de l'outil de géotraitement "Add Join". Lors de la jointure d'attributs, les champs joints sont ajoutés dynamiquement au tableau existant. Les propriétés des champs telles que les alias, la visibilité et le formatage numérique sont conservées lors de l'ajout ou de la suppression de la jointure.

## Capacités de jointure par champ clé

- Cette approche vous permet de **relier des enregistrements de différents tableaux** en fonction d'un champ clé commun. Vous pouvez spécifier le champ clé à utiliser pour la comparaison afin d'établir la relation entre les enregistrements. Ceci est particulièrement utile lorsque vous devez fusionner des données en fonction d'un identifiant ou d'un autre attribut unique.

Spécification de la méthode de comparaison des données basée sur le champ clé :

- Vous pouvez définir **différentes méthodes de comparaison** pour le champ clé lors de la fusion de données. Par exemple, vous pouvez choisir d'avoir une correspondance exacte, comparer en fonction d'un modèle ou dans une plage de valeurs. Cela permet une détermination plus précise des relations entre les enregistrements et donne un contrôle sur le processus de fusion des données.

Spécification d'une liste de noms d'attributs à fusionner :

- Lors de la fusion de données, vous pouvez spécifier **des attributs spécifiques** qui doivent être fusionnés. Cela vous permet de choisir uniquement les attributs nécessaires pour la fusion et de gérer la structure du tableau résultant.

## Capacités de jointure en utilisant la géométrie

- Cette approche vous permet de relier des données en fonction de leur **emplacement spatial**. Vous pouvez définir un rayon de recherche dans lequel les objets géométriques les plus proches seront recherchés pour la fusion. Ceci est utile lorsque vous devez joindre des données en fonction de leur position géographique.

Contrôle du rayon de recherche pour trouver les objets géométriques les plus proches :

- Vous pouvez contrôler **le rayon de recherche** lors de la fusion de données basée sur l'emplacement. En spécifiant une valeur de rayon, vous déterminez la distance dans laquelle les objets les plus proches seront recherchés pour la fusion. Cela donne un contrôle sur les objets qui participeront au processus de fusion des données en fonction de leur relation spatiale.

## Projet Démo

Pour mieux comprendre la fonctionnalité de notre bibliothèque, considérons [un exemple de son utilisation](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Layers.Join). Ce code illustre comment joindre des couches vectorielles par attributs ou géométrie.

Le code fourni se compose de deux méthodes, JoinByIndex() et JoinByCoords(), qui démontrent les opérations de jointure de données à l'aide d'une classe LayerConstructor.

Dans la méthode JoinByIndex() :

- Des listes de géométries avec des attributs associés sont créées.

- Un objet LayerConstructor est initialisé.

- La méthode crée une couche vectorielle et une couche de géométrie en utilisant les géométries fournies.

- La couche de géométrie est jointe en fonction d'un identifiant unique ("Id") à l'aide de la méthode JoinLayersById().

- La couche vectorielle jointe résultante est renvoyée.

Dans la méthode JoinByCoords() :

- Des listes de géométries avec des attributs associés sont créées.

- Un objet LayerConstructor est initialisé.

- Des couches de géométrie sont créées à l'aide des géométries fournies.

- Les couches de géométrie sont jointes en fonction de la correspondance des coordonnées à l'aide de la méthode JoinLayersByCoords().

- La couche vectorielle jointe résultante est renvoyée.

En résumé, ces méthodes illustrent deux approches différentes pour joindre des données : une basée sur un identifiant unique et l'autre basée sur la correspondance des coordonnées. La classe LayerConstructor facilite ces opérations de jointure de données.

## Options de jointure pour Index

La classe JoinOptions fournit un ensemble d'options pour configurer les couches de jointure. Approfondissons chaque option :

- **JoinAttributeName** : Cette option vous permet de spécifier le nom de l'attribut de la couche jointe dont la valeur sera utilisée dans la comparaison des conditions. Elle établit la connexion entre les deux couches en fonction de cet attribut.

- **TargetAttributeName** : Avec cette option, vous pouvez spécifier le nom de l'attribut de la couche principale qui sera comparé à l'attribut de la couche jointe. Cela permet de déterminer les caractéristiques correspondantes entre les couches.

- **JoinAttributeNames** : Cette option vous permet de spécifier une liste de noms d'attributs que vous souhaitez joindre. Si cette liste est laissée vide ou définie sur null, tous les attributs de la couche jointe seront inclus dans l'opération de jointure. Cependant, en sélectionnant des noms d'attributs spécifiques, vous pouvez contrôler les attributs qui sont joints, ce qui peut être utile pour optimiser l'utilisation de la mémoire et le temps de traitement.

- **ConditionComparer** : Cette option vous permet de définir une logique personnalisée pour comparer les valeurs d'attribut entre les caractéristiques des deux couches. Par défaut, elle utilise le comparateur EqualityComparer.Default, qui vérifie l'égalité. Cependant, vous pouvez fournir votre propre comparateur personnalisé qui implémente IEqualityComparer pour des exigences de comparaison plus spécialisées.

- **JoinedAttributesPrefix** : Cette option vous permet de spécifier un préfixe de chaîne pour les noms d'attributs de la couche jointe. La valeur par défaut est "joined_", ce qui signifie que les attributs joints seront préfixés avec "joined_" dans la couche jointe résultante. Ce préfixe aide à différencier les attributs joints des attributs originaux de la couche principale.

La classe JoinOptions offre une flexibilité et un contrôle sur divers aspects du processus de jointure des couches. Vous pouvez spécifier les attributs à joindre, personnaliser la logique de comparaison et définir un préfixe pour les attributs joints résultants. Ces options vous permettent d'adapter l'opération de jointure en fonction de vos besoins spécifiques et d'obtenir des informations significatives des couches fusionnées.

## Options de jointure pour Géométrie

La classe **JoinByGeometryOptions** représente les options pour joindre des couches basées sur la géométrie. Explorons la fonctionnalité de chaque option :

- **Radius** : Cette option spécifie le rayon dans lequel la géométrie jointe sera recherchée. Elle détermine la proximité dans laquelle les caractéristiques de la couche principale seront mises en correspondance avec les caractéristiques de la couche jointe en fonction de leur relation spatiale.

- **ConditionComparer** : Cette option vous permet de définir une logique personnalisée pour comparer les valeurs d'attribut des caractéristiques des deux couches. Par défaut, elle utilise EqualityComparer.Default, qui vérifie l'égalité. Cependant, vous pouvez fournir votre propre comparateur personnalisé qui implémente IEqualityComparer pour des exigences de comparaison plus spécifiques.

- **JoinedAttributesPrefix** : Cette option vous permet de spécifier un préfixe de chaîne pour les noms d'attributs de la couche jointe. La valeur par défaut est "joined_", ce qui signifie que les attributs joints seront préfixés avec "joined_" dans la couche jointe résultante. Ce préfixe aide à différencier les attributs joints des attributs originaux de la couche principale.

La classe JoinByGeometryOptions fournit les moyens de personnaliser le processus de jointure des couches en fonction de leur relation spatiale. En spécifiant un rayon de recherche, vous pouvez contrôler l'étendue dans laquelle les géométries seront mises en correspondance. Cela permet d'affiner l'opération de jointure en fonction de la proximité souhaitée entre les caractéristiques. L'option de fournir un comparateur personnalisé vous donne une flexibilité pour comparer les valeurs d'attribut et l'option de préfixer les attributs joints aide à les différencier dans la couche jointe résultante.

En utilisant ces options, vous pouvez effectuer une fusion de données sensible spatialement et obtenir des informations des couches jointes qui sont basées sur leur proximité spatiale et leurs valeurs d'attribut.

## Résumé

Le mécanisme de jointure de données dans un SIG permet de combiner des objets géométriques avec leurs attributs respectifs provenant de différentes couches. Cela offre la possibilité d'analyser et d'extraire des informations en fonction des relations spatiales et des attributs au sein des données. Les options disponibles permettent une personnalisation du processus de jointure pour répondre aux exigences spécifiques et aux besoins d'analyse dans les données SIG.

La jointure de données facilite diverses tâches, notamment :

- Trouver des objets qui répondent à des critères spatiaux spécifiques, tels que l'identification de tous les bâtiments situés dans un rayon de 500 mètres d'un point spécifique.

- Combiner des données géographiques pour créer une vue d'ensemble plus complète et informative d'une situation.

- Analyser les valeurs d'attributs des objets en fonction de conditions spatiales spécifiques afin d'identifier les tendances et les modèles.

Les options de jointure de données permettent une configuration précise du processus de mise en correspondance des objets. Ces options incluent la sélection des attributs à joindre, la définition d'une logique personnalisée pour comparer les valeurs d'attribut et l'ajout d'un préfixe aux noms d'attributs des données jointes. Ces options offrent une flexibilité et une adaptabilité au processus de jointure, répondant aux exigences spécifiques et aux objectifs de l'analyse des données dans un SIG.

Le mécanisme de jointure de données joue un rôle important dans l'intégration et l'analyse des données géographiques, conduisant à une compréhension plus complète de la nature spatiale et des attributs des objets étudiés.