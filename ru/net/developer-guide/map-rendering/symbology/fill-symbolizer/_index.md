---
title: "Заполнитель Символизации"
type: docs
url: /ru/net/fill-symbolizer/
weight: 30
description: GIS C# Библиотека API поддерживает простую символизацию заливки для стиля и обводки двухмерных геометрий полигонов любого типа, таких как Точка, Линия, Поверхность.
---

## **Заполнитель Символизации**
Простая символизация заливки заполняет область настраиваемым стилем заливки и обводкой. Это символ по умолчанию для двухмерных геометрий (полигонов). 

Если у полигона есть «отверстия», они не заполняются, но границы вокруг отверстий обводятся обычным способом. «Острова» внутри отверстий заполняются и обводятся, и так далее.

Поддерживаемые параметры стиля:

|**Свойство**|**Описание**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Указывает цвет и прозрачность, заданные заливке.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - Сплошная заливка</p><p>- None - Не заполнять полигон</p><p>- Horizontal Hatch - Узор из горизонтальных линий.</p><p>- Vertical Hatch - Узор из вертикальных линий.</p><p>- Cross Hatch - Указывает горизонтальные и вертикальные линии, которые пересекаются.</p><p>- Forward Diagonal Hatch - Узор линий по диагонали сверху слева вниз направо.</p><p>- Backward Diagonal Hatch - Узор линий по диагонали сверху справа вниз налево.</p><p>- Diagonal Cross Hatch - Узор из перекрестных диагональных линий.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Указывает цвет и прозрачность, заданные линии обводки.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Указывает, как должны быть нарисованы штрихи символа.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Указывает ширину линии обводки.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Указывает массив расстояний, который определяет длины чередующихся тире и пробелов в пунктирных линиях.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Указывает расстояние от начала линии до начала шаблона тире.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Определяет, как линии отображаются в точках пересечения сегментов линий.</p><p>- Miter - острый угол</p><p>- Round - скругленный угол</p><p>- Bevel - диагональный угол</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Указывает горизонтальное смещение от местоположения точки к опорной точке фигуры.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Указывает вертикальное смещение от местоположения точки к опорной точке фигуры.|

### **Типы Геометрий**
` `Символизатор может применяться к геометриям любого типа.

|**Размерность Геометрии**|**Типы Геометрий**|**Поведение при Рендеринге**|
| :-: | :-: | :-: |
|**Точка**|Point, MultiPoint|Рисует небольшой квадратный ортогональный полигон.|
|**Линия**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Линия замыкается для заливки путем соединения ее конечной точки с начальной точкой. Только исходная линия обводится.|
|**Поверхность**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Рисует полигон.|

Для GeometryCollections поведение рендеринга определяется отдельно для каждой геометрии внутри коллекции. Слои с геометрией смешанного типа следуют логике для GeometryCollections.

Используйте MixedGeometrySymbolizer, чтобы ограничить символизатор определенными типами геометрий.

### **Примеры**
По умолчанию Simple Fill symbolizer рисует черную линию обводки и сплошную белую заливку:



Здесь показано, как изменить стиль:


|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

Вы также можете захотеть добавить метки к своим полигонам. Посетите [Примеры маркировки линий](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) для примеров того, как маркировать границу полигона, или [Примеры маркировки точек](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) на примерах того, как маркировать центры полигонов.
