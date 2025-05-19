---
title: Filtrage et indexation des calques vectoriels SIG en C#
linktitle: Filtrage et indexation
second_title: Aspose.GIS pour .NET
type: docs
url: /fr/filtering-and-indexing/
weight: 30
description: Avec la bibliothèque ou l'API GIS C# .NET, vous pouvez filtrer les calques vectoriels SIG par valeurs d'attributs ou limites spatiales. Vous pouvez également utiliser des index pour accélérer le filtrage et les requêtes spatiales.
---

Avec Aspose.GIS pour .NET, vous pouvez filtrer les calques par valeurs d'attributs ou limites spatiales. Vous pouvez également utiliser des index pour accélérer le filtrage et les requêtes spatiales.
## **Index d'attribut**
### **Filtrage sans index**
Voici comment filtrer un calque par les valeurs d'un attribut :

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **Filtrage avec index**
Le code ci-dessus est correct tant que le calque n'est filtré qu'une seule fois. Mais, si le calque risque d'être interrogé plusieurs fois, nous pouvons tirer parti des index d'attributs. La création d'un index d'attribut prend un certain temps, mais il peut être réutilisé plusieurs fois pour accélérer le filtrage.

L’exemple suivant utilise un fichier d’index d’attributs pour accélérer le filtrage des calques par les valeurs de l’attribut :

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **Enregistrer les caractéristiques filtrées**
Les caractéristiques filtrées peuvent être enregistrées dans des calques :

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **Rendre les caractéristiques filtrées**
Il est également possible de rendre des caractéristiques filtrées. L’exemple suivant utilise un index d’attributs pour sélectionner rapidement toutes les caractéristiques dont la population est supérieure à 2000 et les ajouter à la carte :

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **Index spatial**
Les index spatiaux sont utilisés pour accélérer les requêtes spatiales. Tout comme les index d’attributs, les index spatiaux sont réutilisés après leur création.
### **Trouver des caractéristiques proches d'un point**
Voici comment utiliser un index spatial pour accélérer la recherche de la caractéristique la plus proche d'un certain point :

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **Sélectionner des caractéristiques qui intersectent une géométrie**
L’exemple suivant utilise un index spatial pour accélérer la sélection de caractéristiques qui intersectent une géométrie :

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
