---
title: Rendu de carte en image SVG, PNG, JPG à l'aide d'une bibliothèque C# GIS
linktitle: "Rendu de carte"
type: docs
url: /fr/net/map-rendering/
weight: 50
description: Avec l'API C# GIS, vous pouvez rendre une carte à partir de Shapefile, FileGDB, GeoJSON, KML, effectuer un style avancé et dessiner une carte à partir de formats raster.
---

## **Aperçu du rendu de carte**
Avec l'API C# Aspose.GIS pour .NET, vous pouvez rendre une carte à partir d'un Shapefile, FileGDB, GeoJSON, KML ou d'autres [formats de fichiers pris en charge](/gis/net/supported-file-formats/) vers SVG, PNG, JPEG ou BMP.

Voici un code C# illustrant comment rendre une carte à partir d'un shapefile vers SVG en utilisant les paramètres par défaut :



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



Voici le résultat :



![rendu de carte](map_rendering.png)

Examinons de plus près le code.

Tout d'abord, nous instancions un objet [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map). Il représente une collection de calques provenant de diverses sources qui peuvent être rendus. Une carte a une taille à laquelle elle est censée être affichée. Ici, nous définissons la carte sur 800 pixels de large et 400 pixels de haut.

Remarquez que la Map est incluse dans l'instruction using. Ceci est nécessaire car la map suit toutes les ressources ajoutées à celle-ci et les élimine lorsque nous avons terminé le rendu et que l'objet Map est éliminé.

Ensuite, nous ajoutons un calque à partir d'un fichier à la carte. Chaque calque est rendu par-dessus le calque précédent, dans l'ordre dans lequel ils ont été ajoutés à la carte. Voir plus de détails sur comment ouvrir les calques vectoriels [ici](/gis/net/working-with-vector-layers/).

Enfin, nous appelons [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) pour rendre la carte dans un fichier. Nous spécifions un chemin d'accès à l'endroit où enregistrer le fichier de résultat et un moteur de rendu à utiliser. La classe [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) contient des références à tous les moteurs de rendu inclus avec Aspose.GIS. Par exemple, vous pouvez spécifier Renderers.Png au lieu de Renderers.Svg dans l'exemple ci-dessus pour rendre la carte dans un fichier PNG

## **Style avancé**
Avec l'API Aspose.GIS, vous pouvez personnaliser le rendu et les styles des entités afin d'obtenir l'apparence souhaitée.

![style avancé](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **Dessiner un raster dans la carte**
Avec Aspose.GIS pour .NET, vous pouvez rendre une carte à partir de formats raster.
### **Rendu avec les paramètres par défaut**
Voici comment rendre une carte à partir d'un GeoTIFF vers SVG en utilisant les paramètres par défaut :

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![raster par défaut](default_raster.png)
### **Rendu des rasters asymétriques**
Avec Aspose.GIS, vous pouvez rendre un raster avec des cellules de raster asymétriques.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![raster asymétrique](skew_raster.png)
### **Rendu dans une référence spatiale polaire**
Aspose.GIS vous permet d'utiliser des références spatiales polaires sur un processus de rendu de carte.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![pays gnomoniques](gnomonic_countries.png)
