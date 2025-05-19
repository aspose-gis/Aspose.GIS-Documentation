---
title: "Application Console Générateur de Calques"
type: docs
url: /fr/net/layer-generator-console
weight: 50
---

## Résumé

Cette application console est conçue pour générer des objets géométriques de divers types et les enregistrer dans le format choisi. Elle vous permet de créer des points, des polygones et des polylignes, de spécifier le nombre d'objets à générer et de choisir le format de sortie pour l'enregistrement.

## Utilisation

Syntaxe de la commande :

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

Arguments :

```
-t, --type: Type de géométrie. L'un des suivants : Point, Polygone, Polyline.

-c, --count: Obligatoire. Nombre d'objets à générer. Par exemple : 15.

-f, --fileName: Obligatoire. Nom du fichier pour l'enregistrement. Spécifiez le nom du fichier et l'extension. Par exemple : test.json.

-o, --outputFormat: Format de sortie. Voir les formats de fichiers pris en charge ici.

--help: Afficher les informations d'aide pour la commande.

--version: Afficher les informations sur la version de l'application.
```

Un exemple de commande pour créer 15 points aléatoires et les enregistrer dans un fichier au format "test.json" :

```
app.exe -t Point -c 15 -f test.json -o json
```

## Installation et Licence

Si vous souhaitez utiliser l'application, vous devez télécharger l'archive et l'extraire. Veuillez suivre le lien ci-dessous.

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

Bien que l'application console Générateur de calques Aspose.GIS soit gratuite, Aspose.GIS .NET est concédé sous licence comme d'habitude, vous pouvez donc réutiliser votre licence via l'application ou évaluer l'application en utilisant Aspose.GIS .NET en mode d'essai ou demander une licence temporaire.

## Conclusion

Le générateur d'objets géométriques est une application console pratique qui vous aide à créer des échantillons de géométrie de divers types et à les enregistrer dans le format souhaité. C'est un outil utile pour travailler avec des données géospatiales et développer des systèmes d'information géographique.
