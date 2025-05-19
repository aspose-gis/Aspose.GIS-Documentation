---
title: "Symboliseur de ligne"
type: docs
url: /fr/net/line-symbolizer/
weight: 20
description: La bibliothèque ou l'API GIS C# prend en charge le symboliseur de ligne simple pour les géométries unidimensionnelles (lignes) et peut être appliquée sur des géométries de n'importe quel type, comme Point, Ligne, Surface.
---

## **Symboliseur de ligne**
Le symboliseur de ligne simple dessine une ligne avec un style personnalisable. Il s'agit du symboliseur par défaut pour les géométries unidimensionnelles (lignes). 

Options de style prises en charge :

|**Propriété**|**Description**|
| :- | :- |
|[Couleur](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|Spécifie la couleur et la transparence données à la ligne.|
|[Largeur](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|Spécifie la largeur de la ligne|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|Détermine comment les lignes sont rendues aux intersections des segments de ligne.|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|Spécifie comment le tracé du symbole doit être dessiné.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|Spécifie un tableau de distances qui spécifient les longueurs des tirets et des espaces alternés dans les lignes en pointillés.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|Spécifie la distance du début d'une ligne au début d'un motif de tirets.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>Spécifie comment les lignes sont rendues à leurs extrémités.</p><p>- Butt - bord carré net</p><p>- Round - bord arrondi</p><p>- Square - bord carré légèrement allongé</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|Spécifie le décalage par rapport à la ligne d'origine. Pour une distance positive, le décalage sera du côté gauche de la ligne d'entrée (par rapport à la direction de la ligne). Pour une distance négative, il se trouvera sur le côté droit.|

### **Types de géométrie**
` `Le symboliseur peut être appliqué à des géométries de n'importe quel type.

|**Dimension de la géométrie**|**Types de géométrie**|**Comportement du rendu**|
| :-: | :-: | :-: |
|**Point**|Point, MultiPoint|Dessine une ligne de petite longueur avec une orientation horizontale centrée sur le point, avec deux capuchons d'extrémité.|
|**Ligne**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Dessine la ligne.|
|**Surface**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Le contour fermé de la géométrie est utilisé comme chaîne de ligne (sans capuchons d'extrémité)|

Pour les GeometryCollections, le comportement du rendu est déterminé séparément pour chaque géométrie dans la collection. Les calques avec un type de géométrie mixte suivent la logique des GeometryCollections.

Utilisez MixedGeometrySymbolizer pour limiter un symboliseur à des types de géométrie spécifiques.

### **Exemples**
Par défaut, le symboliseur de ligne dessine des lignes noires :



Voici comment modifier la couleur de la ligne en bleu :



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

-----

Pour des scénarios plus avancés, vous voudrez peut-être ajuster le style de la ligne dynamiquement en fonction des valeurs d'attributs des entités. Voici comment faire :



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |



-----

Vous voudrez peut-être également ajouter des étiquettes à vos lignes. Visitez [Exemples d'étiquetage de lignes](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) pour obtenir des exemples.
