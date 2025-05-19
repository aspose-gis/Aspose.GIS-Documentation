---
title: "Symboliseur de remplissage"
type: docs
url: /fr/net/fill-symbolizer/
weight: 30
description: La bibliothèque d'API GIS C# prend en charge le symboliseur de remplissage simple pour remplir le style et le contour des géométries bidimensionnelles, des polygones de tout type comme Point, Ligne, Surface.
---

## **Symboliseur de remplissage**
Le symboliseur de remplissage simple remplit une zone avec un style de remplissage et un contour personnalisables. Il s'agit du symboliseur par défaut pour les géométries bidimensionnelles (polygones). 

Si un polygone a des « trous », ils ne sont pas remplis, mais les bordures autour des trous sont tracées de la manière habituelle. Les « îles » à l’intérieur des trous sont remplies et tracées, et ainsi de suite.

Options de style prises en charge :

|**Propriété**|**Description**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Spécifie la couleur et la transparence données au remplissage.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solide - Remplissage solide</p><p>- Aucun - Ne pas remplir le polygone</p><p>- Hachures horizontales - Un motif de lignes horizontales.</p><p>- Hachures verticales - Un motif de lignes verticales.</p><p>- Hachures croisées - Spécifie des lignes horizontales et verticales qui se croisent.</p><p>- Hachures diagonales avant - Un motif de lignes en diagonale de haut à gauche vers bas à droite.</p><p>- Hachures diagonales arrière - Un motif de lignes en diagonale de haut à droite vers bas à gauche.</p><p>- Hachures diagonales croisées - Un motif de lignes diagonales entrecroisées.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Spécifie la couleur et la transparence données à la ligne du contour.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Spécifie comment le tracé des symboles doit être dessiné.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Spécifie la largeur de la ligne du contour.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Spécifie un tableau de distances qui spécifient les longueurs des tirets et des espaces alternés dans les lignes en pointillés.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Spécifie la distance du début d’une ligne au début d’un motif de tirets.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Détermine comment les lignes sont rendues aux intersections de segments de ligne.</p><p>- Biseau - coin vif</p><p>- Arrondi - coin arrondi</p><p>- Chanfrein - coin diagonal</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Spécifie un décalage horizontal par rapport à l’emplacement d’un point jusqu’au point d’ancrage de la forme.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Spécifie un décalage vertical par rapport à l’emplacement d’un point jusqu’au point d’ancrage de la forme.|
### **Types de géométrie**
` `Le symboliseur peut être appliqué aux géométries de tout type.

|**Dimension de la géométrie**|**Types de géométrie**|**Comportement du rendu**|
| :-: | :-: | :-: |
|**Point**|Point, MultiPoint|Dessine un petit carré orthogonal polygonale.|
|**Ligne**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|La ligne est fermée pour le remplissage en connectant son point final à son point de départ. Seule la ligne d’origine est tracée.|
|**Surface**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Dessine le polygone.|

Pour les GeometryCollections, le comportement du rendu est déterminé séparément pour chaque géométrie dans la collection. Les calques avec un type de géométrie mixte suivent la logique des GeometryCollections.

Utilisez MixedGeometrySymbolizer pour limiter un symboliseur à des types de géométrie spécifiques.

### **Exemples**
Par défaut, le symboliseur de remplissage simple dessine une ligne de contour noire et un remplissage blanc solide :



Ici comment modifier le style :




|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

-----
Vous pouvez également ajouter des étiquettes à vos polygones. Visitez [Exemples d’étiquetage de lignes](/gis/fr/net/simple-labeling/#simplelabeling-lineslabelingexamples) pour des exemples sur la façon d’étiqueter les bordures des polygones ou [Exemples d’étiquetage de points](/gis/fr/net/simple-labeling/#simplelabeling-pointslabelingexamples) sur des exmaples sur la façon d’étiqueter les centres des polygones.
