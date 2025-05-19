---
title: "Simbolizador de Línea"
type: docs
url: /es/net/line-symbolizer/
weight: 20
description: La biblioteca o API GIS C# admite el simbolizador de línea simple para geometrías unidimensionales líneas y se puede aplicar a geometrías de cualquier tipo como Punto, Línea, Superficie.
---

## **Simbolizador de Línea**
El simbolizador de línea simple dibuja una línea con un estilo personalizable. Este es el simbolizador predeterminado para geometrías unidimensionales (líneas). 

Opciones de estilo admitidas:

|**Propiedad**|**Descripción**|
| :- | :- |
|[Color](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|Especifica el color y la transparencia dados a la línea.|
|[Width](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|Especifica el ancho de la línea|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|Determina cómo se renderizan las líneas en las intersecciones de los segmentos de línea.|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|Especifica cómo debe dibujarse el trabajo de línea del símbolo.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|Especifica una matriz de distancias que especifica las longitudes de los guiones y espacios alternados en líneas discontinuas.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|Especifica la distancia desde el inicio de una línea hasta el comienzo de un patrón de guiones.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>Especifica cómo se renderizan las líneas en sus extremos.</p><p>- Butt - borde cuadrado afilado</p><p>- Round - borde redondeado</p><p>- Square - borde cuadrado ligeramente alargado</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|Especifica el desplazamiento de la línea original. Para una distancia positiva, el desplazamiento estará en el lado izquierdo de la línea de entrada (en relación con la dirección de la línea). Para una distancia negativa, estará en el lado derecho.|

### **Tipos de Geometría**
` `El simbolizador se puede aplicar a geometrías de cualquier tipo.

|**Dimensión de la geometría**|**Tipos de geometría**|**Comportamiento de renderizado**|
| :-: | :-: | :-: |
|**Punto**|Punto, MultiPunto|Dibuja una línea de pequeña longitud con orientación horizontal centrada en el punto, con dos tapas finales.|
|**Línea**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Dibuja la línea.|
|**Superficie**|Polígono, CurvePolygon, MultiPolígono, MultiSurface|El contorno cerrado de la geometría se utiliza como la cadena de línea (sin tapas finales)|

Para GeometryCollections, el comportamiento de renderizado se determina por separado para cada geometría dentro de la colección. Las capas con tipo de geometría mixto siguen la lógica para GeometryCollections.

Utilice MixedGeometrySymbolizer para limitar un simbolizador a tipos de geometría específicos.

### **Ejemplos**
Por defecto, el simbolizador de línea dibuja líneas negras:



Aquí le mostramos cómo cambiar el color de la línea a azul:



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

Para escenarios más avanzados, es posible que desee ajustar el estilo de la línea dinámicamente en función de los valores de los atributos de las características. Así es como puedes hacerlo:



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |



También es posible que desee agregar etiquetas a sus líneas. Visite [Ejemplos de etiquetado de líneas](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) para obtener ejemplos.
