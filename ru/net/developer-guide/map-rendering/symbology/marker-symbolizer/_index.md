---
title: "Маркерный Символизатор"
type: docs
url: /ru/net/marker-symbolizer/
weight: 10
description: GIS C# Библиотека или API поддерживает простой символизатор маркеров, который рисует предопределенную форму с настраиваемым заполнением и обводкой на геометриях любого типа, таких как Точка, Линия, Поверхность.
---

## **Маркерный Символизатор**
Простой символизатор маркеров рисует предопределенную форму с настраиваемым заполнением и обводкой. Это символ по умолчанию для 0-мерных геометрий (точек). 

Поддерживаемые формы:

|![todo:image_alt_text](marker-symbolizer_1.png)|Круг| |![todo:image_alt_text](marker-symbolizer_2.png)|Звезда|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Квадрат| |![todo:image_alt_text](marker-symbolizer_4.png)|Крест|
|![todo:image_alt_text](marker-symbolizer_5.png)|Треугольник| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

Поддерживаемые параметры стилизации:

|**Свойство**|**Описание**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|Указывает форму маркера.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|Указывает размер формы маркера|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|Указывает цвет и прозрачность заливки|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|Указывает цвет и прозрачность линии|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|Указывает ширину линии|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|Определяет, как линии отображаются в точках пересечения сегментов линий.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|Указывает, как должны быть нарисованы штрихи символа.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|Указывает массив расстояний, определяющих длины чередующихся тире и пробелов в пунктирных линиях.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|Указывает расстояние от начала линии до начала шаблона тире.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|Указывает поворот символа вокруг его центральной точки в десятичных градусах. Положительные значения указывают на вращение по часовой стрелке, отрицательные значения - против часовой стрелки. Значение по умолчанию - 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|Указывает горизонтальное смещение от местоположения точки до опорной точки формы.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|Указывает вертикальное смещение от местоположения точки до опорной точки формы.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|Указывает, какая сторона формы маркера будет выровнена по горизонтали с местоположением точки.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|Указывает, какая сторона формы маркера будет выровнена по вертикали с местоположением точки.|

### **Типы Геометрий**
` `Символизатор может быть применен к геометриям любого типа.

|**Размерность Геометрии**|**Типы Геометрий**|**Поведение При Рендеринге**|
| :-: | :-: | :-: |
|**Точка**|Точка, MultiPoint|Рисует форму, центрированную в координате точки.|
|**Линия**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>Рисует форму, центрированную в центре тяжести геометрии</p><p> </p>|
|**Поверхность**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

Для GeometryCollections поведение рендеринга определяется отдельно для каждой геометрии внутри коллекции. Слои с геометрией смешанного типа следуют логике для GeometryCollections.

Используйте MixedGeometrySymbolizer, чтобы ограничить символизатор определенными типами геометрий.

### **Примеры**
По умолчанию маркерный символизатор рисует черные круги:



Здесь показано, как изменить цвет заливки на красный:



|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

Еще один пример стилизации с предопределенной формой (треугольник):



|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----
Для более сложных сценариев может потребоваться динамически настраивать стиль маркера в зависимости от значений атрибутов объекта. Вот как это сделать:



|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
Вы также можете добавить метки к своим маркерам. Посетите [Примеры Подписи Точек](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) для примеров.
