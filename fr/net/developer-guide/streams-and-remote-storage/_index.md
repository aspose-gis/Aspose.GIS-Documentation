---
title: "Flux et stockage distant"
type: docs
url: /fr/net/streams-and-remote-storage/
weight: 70
---

## **Travailler avec des formats multi-fichiers**
Certains formats de données SIG divisent le contenu en plusieurs fichiers. Par exemple, un shapefile doit avoir au moins trois fichiers : *.shp, *.shx et *.dbf. Ces formats nécessitent que tous les fichiers soient stockés dans une structure de répertoire particulière avec un schéma prédéfini pour les noms de fichiers.

Dans le même temps, les fichiers peuvent être stockés sur un serveur distant ou un autre emplacement accessible uniquement via des flux. Les flux manquent d'informations sur les noms de fichiers et la structure du répertoire, ce qui rend impossible aux pilotes de format de fichier de déterminer comment traiter les données. Aspose.GIS résout ce problème en fournissant le mécanisme de chemins abstraits.

Un chemin abstrait représente un chemin vers un fichier (ou un répertoire) dans un stockage de type système de fichiers. Le stockage peut être n'importe quoi qui a un concept du fichier et du répertoire, d'une archive à un serveur FTP. Il définit comment exécuter des opérations sur les fichiers typiques, telles que l'ouverture d'un fichier ou la liste d'un répertoire.

Vous pouvez spécifier comment effectuer des opérations sur les fichiers pour votre stockage en implémentant une classe qui hérite de [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) et en fournissant des implémentations à ses méthodes abstraites.
## **Présentation : Stockage d'objets blob Azure**
Le réféentiel Aspose.GIS Examples contient un exemple d'une implémentation entièrement fonctionnelle d'un chemin abstrait personnalisé pour le stockage d'objets blob Azure. Cette présentation montre comment lire un shapefile directement à partir du stockage d'objets blob Azure. Vous pouvez le trouver ici : [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **Formats de fichier unique (GeoJSON, KML)**
Les formats de données SIG tels que GeoJSON et KML peuvent stocker toutes les données d'une couche dans un seul fichier. Si vous pouvez obtenir un flux pour le fichier, vous pouvez ignorer l'implémentation d'un chemin abstrait personnalisé et utiliser la méthode [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) pour instancier un chemin abstrait pour le flux.
### **Lire un fichier à partir d'un flux**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **Écrire un fichier dans un flux**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
