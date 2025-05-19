---
title: "Licences"
second_title: Aspose.GIS pour .NET
type: docs
url: /fr/net/licensing/
weight: 50
keywords: bibliothèque gis c#, bibliothèque gis .net
description: Évaluez la bibliothèque ou l'API GIS C# .NET avec certaines limitations. Appliquez une licence en utilisant un objet Fichier ou Flux ou comme Ressource Intégrée.
---

## **Évaluer Aspose.GIS pour .NET**
Vous pouvez télécharger gratuitement Aspose.GIS pour .NET. Avant d’appliquer une licence, le composant fonctionne en mode évaluation. Lorsque vous achetez une licence et ajoutez quelques lignes de code pour appliquer la licence, les limitations d'évaluation sont supprimées.

{{% alert color="primary" %}} Si vous souhaitez tester Aspose.GIS sans limitations du mode évaluation, vous pouvez demander une Licence Temporaire de 30 jours. Veuillez consulter [Obtenir une Licence Temporaire](https://purchase.aspose.com/temporary-license). {{% /alert %}}
### **Limitations du Mode Évaluation**
Lors de l’exécution en mode évaluation (sans licence appliquée), Aspose.GIS fournit toutes les fonctionnalités du produit, à l'exception de certaines limitations d'évaluation.

1. Pas plus de **15 documents** peuvent être ouverts et/ou créés **par heure**.
1. Pas plus de **100 entités** peuvent être accessibles dans chaque document (lecture ou écriture).
1. Pas plus de **10 000 données raster** peuvent être accessibles dans chaque document (lecture ou écriture).
1. Le nombre maximal d'entités autorisé dans un document pour les opérations de conversion est de **50**.

Lorsque vous exécutez en mode licence, vous pouvez traiter un nombre illimité de documents et d'entités.
## **Application d’une Licence**
La licence est un fichier XML texte brut qui contient des détails tels que le nom du produit, le nombre de développeurs pour lesquels il est concédé sous licence, la date d'expiration de l'abonnement, etc. Le fichier est signé numériquement, alors ne modifiez pas le fichier. Même l’ajout involontaire d’un saut de ligne supplémentaire dans le fichier l’invalidera.

Vous devez définir une licence avant d’utiliser Aspose.GIS si vous souhaitez éviter ses limitations d’évaluation. Il n’est nécessaire de définir une licence qu'une seule fois par application (ou processus).
### **Définir une Licence dans Aspose.GIS pour .NET**
Dans Aspose.GIS, la licence peut être chargée à partir d’un fichier, d’un flux ou d’une ressource intégrée. Aspose.GIS tente de trouver la licence aux emplacements suivants :

- Chemin explicite
- Le dossier qui contient Aspose.GIS.dll
- Le dossier qui contient l'assembly qui a appelé Aspose.GIS.dll
- Le dossier qui contient l’assembly d’entrée (votre .exe)
- Une ressource intégrée dans l’assembly qui a appelé Aspose.GIS.dll. Il existe deux méthodes courantes pour définir la licence, qui sont discutées ci-dessous :
### **Appliquer une Licence à l'aide d'un Objet Fichier ou Flux**
La façon la plus simple de définir une licence est de placer le fichier de licence dans le même dossier que celui d’Aspose.GIS.dll et de spécifier uniquement le nom du fichier sans son chemin.

{{< highlight java >}}

 // Instancier une instance de license et définir le fichier de license via son chemin

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // Instancier une instance de license et définir la license via un flux

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}

Lorsque vous appelez la méthode SetLicense, le nom de la licence doit être identique à celui du nom de votre fichier de licence. Par exemple, vous pouvez modifier le nom du fichier de licence en « Aspose.GIS.lic.xml ». Ensuite, dans votre code, vous devez utiliser le nom de licence modifié (c’est-à-dire Aspose.GIS.lic.xml) pour la méthode SetLicense.

## **Inclure le Fichier de Licence comme une Ressource Intégrée**
Une autre façon astucieuse d'empaqueter la licence avec votre application et de vous assurer qu'elle ne sera pas perdue est de l'inclure en tant que ressource intégrée dans l'un des assemblies qui appelle le DLL du composant (inclus dans Aspose.GIS). Pour inclure le fichier de licence comme une ressource intégrée, effectuez les étapes suivantes :

- Dans Visual Studio, incluez le fichier de licence (.lic) dans le projet en utilisant le menu Fichier | Ajouter un élément existant...
- Sélectionnez le fichier dans l'Explorateur de solutions et définissez Action de génération sur Ressource intégrée dans la fenêtre Propriétés.
- Pour accéder à la licence intégrée dans l’assembly (en tant que ressource intégrée), il n’est pas nécessaire d’appeler les méthodes GetExecutingAssembly et GetManifestResourceStream de la classe System.Reflection.Assembly du .NET Framework Microsoft. Tout ce qui est nécessaire est d'ajouter le fichier de licence en tant que ressource intégrée à votre projet et de transmettre le nom du fichier de licence à la méthode License.SetLicense. La classe Licence trouvera automatiquement le fichier de licence dans les ressources intégrées.

Veuillez consulter l’exemple ci-dessous pour comprendre cette méthode de définition de la licence (intégrée) dans vos applications.

{{< highlight java >}}

 // Instancier la classe License

Aspose.Gis.License license = new Aspose.Gis.License();

// Transmettre uniquement le nom du fichier de licence intégré à l'assembly

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **Application d’une Clé Mesurée**
[L'API Aspose.GIS pour .NET](/gis/net/) permet aux développeurs d'appliquer une clé mesurée. Il s'agit d'un nouveau mécanisme de licence. Le nouveau mécanisme de licence sera utilisé en même temps que la méthode de licence existante. Les clients qui souhaitent être facturés en fonction de l'utilisation des fonctionnalités de l'API peuvent utiliser la licence mesurée. Pour plus de détails, veuillez consulter la section [FAQ sur les licences mesurées](https://purchase.aspose.com/faqs/licensing/metered).

Une nouvelle classe **Metered** a été introduite pour appliquer une clé mesurée. Voici un exemple de code montrant comment définir une clé publique et privée mesurée.

**[C#]**

{{< highlight csharp >}}

 // Définir les clés publiques et privées mesurées
 
Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();
 
// Accéder à la propriété setMeteredKey et transmettre les clés publique et privée en tant que paramètres
 
metered.SetMeteredKey("*****", "*****");
 
// EFFECTUER LE TRAITEMENT
 
// obtenir le montant de consommation mesuré
 
decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();
 
// Afficher les informations
 
Console.WriteLine("Montant consommé : " + amount.ToString());

{{< /highlight >}}
