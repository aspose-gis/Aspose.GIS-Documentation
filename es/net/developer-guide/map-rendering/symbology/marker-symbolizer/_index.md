---
title: "Simbolizador de Marcadores"
type: docs
url: /es/net/marker-symbolizer/
weight: 10
description: La biblioteca o API GIS C# admite un simbolizador de marcadores simple que dibuja una forma predefinida con relleno y contorno personalizables en geometrías de cualquier tipo, como Punto, Línea, Superficie.
---

## **Simbolizador de Marcadores**
El simbolizador de marcadores simple dibuja una forma predefinida con relleno y contorno personalizables. Este es el simbolizador predeterminado para geometrías 0-dimensionales (puntos). 

Las formas admitidas son:

|![todo:image_alt_text](marker-symbolizer_1.png)|Círculo| |![todo:image_alt_text](marker-symbolizer_2.png)|Estrella|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Cuadrado| |![todo:image_alt_text](marker-symbolizer_4.png)|Cruz|
|![todo:image_alt_text](marker-symbolizer_5.png)|Triángulo| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

Opciones de estilo admitidas:

|**Propiedad**|**Descripción**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|Especifica la forma del marcador.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|Especifica el tamaño de la forma del marcador|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|Especifica el color y la transparencia dados al relleno|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|Especifica el color y la transparencia dados a la línea|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|Especifica el ancho de la línea|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|Determina cómo se representan las líneas en las intersecciones de los segmentos de línea.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|Especifica cómo debe dibujarse el trazo del símbolo.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|Especifica una matriz de distancias que especifica las longitudes de los guiones y espacios alternados en líneas discontinuas.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|Especifica la distancia desde el inicio de una línea hasta el comienzo de un patrón de guiones.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|Especifica la rotación del símbolo alrededor de su punto central, en grados decimales. Los valores positivos indican rotación en el sentido de las agujas del reloj, los valores negativos indican rotación en sentido antihorario. El valor predeterminado es 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|Especifica un desplazamiento horizontal desde la ubicación de un punto hasta el punto de anclaje de la forma.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|Especifica un desplazamiento vertical desde la ubicación de un punto hasta el punto de anclaje de la forma.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|Especifica qué lado de una forma de marcador se alineará horizontalmente con la ubicación del punto.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|Especifica qué lado de una forma de marcador se alineará verticalmente con la ubicación del punto.|

### **Tipos de Geometría**
` `El simbolizador puede aplicarse a geometrías de cualquier tipo.

|**Dimensión de la geometría**|**Tipos de geometría**|**Comportamiento de representación**|
| :-: | :-: | :-: |
|**Punto**|Punto, MultiPoint|Dibuja la forma centrada en las coordenadas del punto.|
|**Línea**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>Dibuja la forma centrada en el centroide de la geometría</p><p> </p>|
|**Superficie**|Polígono, CurvePolygon, MultiPolygon, MultiSurface||

Para GeometryCollections, el comportamiento de representación se determina por separado para cada geometría dentro de la colección. Las capas con tipo de geometría mixto siguen la lógica para GeometryCollections.

Utilice MixedGeometrySymbolizer para limitar un simbolizador a tipos de geometría específicos.

### **Ejemplos**
Por defecto, el simbolizador de marcadores dibuja círculos negros:



Aquí te mostramos cómo cambiar el color de relleno a rojo:



|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

Otro ejemplo de estilo con una forma predefinida (triángulo):



|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

Para escenarios más avanzados, es posible que desees ajustar el estilo del marcador dinámicamente según los valores de los atributos de las entidades. Así es como puedes hacerlo:



|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

También es posible que desees agregar etiquetas a tus marcadores. Visita [Ejemplos de etiquetado de puntos](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) para obtener ejemplos.
