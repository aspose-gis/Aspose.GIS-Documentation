---
title: "Symboliseur de marqueur"
type: docs
url: /fr/net/marker-symbolizer/
weight: 10
description: La bibliothèque ou l'API GIS C# prend en charge le symboliseur de marqueur simple qui dessine une forme prédéfinie avec un remplissage et un contour personnalisables sur des géométries de n'importe quel type, comme Point, Ligne, Surface.
---

## **Symboliseur de marqueur**
Le symboliseur de marqueur simple dessine une forme prédéfinie avec un remplissage et un contour personnalisables. Il s'agit du symboliseur par défaut pour les géométries 0-dimensionnelles (points). 

Les formes prises en charge sont :

|![todo:image_alt_text](marker-symbolizer_1.png)|Cercle| |![todo:image_alt_text](marker-symbolizer_2.png)|Étoile|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Carré| |![todo:image_alt_text](marker-symbolizer_4.png)|Croix|
|![todo:image_alt_text](marker-symbolizer_5.png)|Triangle| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

Options de style prises en charge :

|**Propriété**|**Description**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|Spécifie la forme du marqueur.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|Spécifie la taille de la forme du marqueur|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|Spécifie la couleur et la transparence données au remplissage|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|Spécifie la couleur et la transparence données à la ligne|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|Spécifie la largeur de la ligne|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|Détermine comment les lignes sont rendues aux intersections de segments de ligne.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|Spécifie comment le tracé du symbole doit être dessiné.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|Spécifie un tableau de distances qui spécifient les longueurs des tirets et des espaces alternés dans les lignes en pointillés.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|Spécifie la distance du début d'une ligne au début d'un motif de tirets.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|Spécifie la rotation du symbole autour de son point central, en degrés décimaux. Les valeurs positives indiquent une rotation dans le sens des aiguilles d'une montre, les valeurs négatives indiquent une rotation dans le sens inverse des aiguilles d'une montre. La valeur par défaut est 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|Spécifie un décalage horizontal à partir de l'emplacement d'un point jusqu'au point d'ancrage de la forme.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|Spécifie un décalage vertical à partir de l'emplacement d'un point jusqu'au point d'ancrage de la forme.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|Spécifie quel côté d'une forme de marqueur sera aligné horizontalement avec l'emplacement du point.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|Spécifie quel côté d'une forme de marqueur sera aligné verticalement avec l'emplacement du point.|

### **Types de géométrie**
` `Le symboliseur peut être appliqué à des géométries de n'importe quel type.

|**Dimension de la géométrie**|**Types de géométrie**|**Comportement de rendu**|
| :-: | :-: | :-: |
|**Point**|Point, MultiPoint|Dessine la forme centrée sur les coordonnées du point.|
|**Ligne**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>Dessine la forme centrée sur le centroïde de la géométrie</p><p> </p>|
|**Surface**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

Pour les GeometryCollections, le comportement de rendu est déterminé séparément pour chaque géométrie à l'intérieur de la collection. Les calques avec un type de géométrie mixte suivent la logique des GeometryCollections.

Utilisez MixedGeometrySymbolizer pour limiter un symboliseur à des types de géométrie spécifiques.

### **Exemples**
Par défaut, le symboliseur de marqueur dessine des cercles noirs :



Ici comment changer la couleur de remplissage en rouge :



|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

Autre exemple de style avec une forme prédéfinie (triangle) :



|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----

Pour des scénarios plus avancés, vous voudrez peut-être ajuster le style du marqueur dynamiquement en fonction des valeurs d'attribut de fonctionnalité. Voici comment faire :



|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----

Vous voudrez peut-être également ajouter des étiquettes à vos marqueurs. Visitez [Exemples d'étiquetage de points](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) pour des exemples.
