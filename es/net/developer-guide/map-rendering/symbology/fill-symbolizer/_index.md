---
title: "Simbolizador de Relleno"
type: docs
url: /es/net/fill-symbolizer/
weight: 30
description: La biblioteca API de GIS C# admite el simbolizador de relleno simple para rellenar el estilo y el trazo de geometrías bidimensionales, polígonos de cualquier tipo como Punto, Línea, Superficie.
---

## **Simbolizador de Relleno**
El simbolizador de relleno simple rellena un área con un estilo de relleno y trazo personalizable. Este es el simbolizador predeterminado para geometrías bidimensionales (polígonos). 

Si un polígono tiene “agujeros”, no se rellenan, pero los bordes alrededor de los agujeros se trazan de la manera habitual. Las “islas” dentro de los agujeros se rellenan y se trazan, y así sucesivamente.

Opciones de estilo admitidas:

|**Propiedad**|**Descripción**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Especifica el color y la transparencia dados al relleno.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Sólido - Relleno sólido</p><p>- Ninguno - No rellenar el polígono</p><p>- Rayado Horizontal - Un patrón de líneas horizontales.</p><p>- Rayado Vertical - Un patrón de líneas verticales.</p><p>- Rayado Cruzado - Especifica líneas horizontales y verticales que se cruzan.</p><p>- Rayado Diagonal Hacia Adelante - Un patrón de líneas en diagonal desde la esquina superior izquierda a la inferior derecha.</p><p>- Rayado Diagonal Hacia Atrás - Un patrón de líneas en diagonal desde la esquina superior derecha a la inferior izquierda.</p><p>- Rayado Cruzado Diagonal - Un patrón de líneas diagonales cruzadas.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Especifica el color y la transparencia dados a la línea de trazo.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Especifica cómo se deben dibujar los trabajos de líneas del símbolo.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Especifica el ancho de la línea de trazo.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Especifica una matriz de distancias que especifica las longitudes de guiones y espacios alternados en líneas discontinuas.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Especifica la distancia desde el inicio de una línea hasta el comienzo de un patrón de guiones.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Determina cómo se representan las líneas en las intersecciones de los segmentos de línea.</p><p>- Mitre - esquina afilada</p><p>- Redondo - esquina redondeada</p><p>- Bisel - esquina diagonal</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Especifica el desplazamiento horizontal desde la ubicación de un punto hasta el punto de anclaje de la forma.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Especifica el desplazamiento vertical desde la ubicación de un punto hasta el punto de anclaje de la forma.|

### **Tipos de geometría**
` `El simbolizador se puede aplicar a geometrías de cualquier tipo.

|**Dimensión de la geometría**|**Tipos de geometría**|**Comportamiento de representación**|
| :-: | :-: | :-: |
|**Punto**|Punto, MultiPunto|Dibuja un pequeño cuadrado ortogonal polígono.|
|**Línea**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|La línea se cierra para el relleno conectando su punto final con su punto de inicio. Solo la línea original está trazada.|
|**Superficie**|Polígono, CurvePolygon, MultiPolygon, MultiSurface|Dibuja el polígono.|

Para GeometryCollections, el comportamiento de representación se determina por separado para cada geometría dentro de la colección. Las capas con tipo de geometría mixto siguen la lógica para GeometryCollections.

Utilice MixedGeometrySymbolizer para limitar un simbolizador a tipos de geometría específicos.

### **Ejemplos**
Por defecto, el Simple Fill symbolizer dibuja una línea de trazo negra y un relleno blanco sólido:



Aquí se muestra cómo cambiar el estilo:




|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

También es posible que desee agregar etiquetas a sus polígonos. Visite [Ejemplos de etiquetado de líneas](/gis/es/net/simple-labeling/#simplelabeling-lineslabelingexamples) para obtener ejemplos sobre cómo etiquetar el borde del polígono o [Ejemplos de etiquetado de puntos](/gis/es/net/simple-labeling/#simplelabeling-pointslabelingexamples) sobre exmaples sobre cómo etiquetar los centros del polígono.
