---
title: "Символ линии"
type: docs
url: /ru/net/line-symbolizer/
weight: 20
description: GIS C# Библиотека или API поддерживает простой символ линии для одномерных геометрий линий и может применяться к геометриям любого типа, таких как Точка, Линия, Поверхность.
---

## **Символ линии**
Простой символ линии рисует линию с настраиваемым стилем. Это символ по умолчанию для одномерных геометрий (линий). 

Поддерживаемые параметры стиля:

|**Свойство**|**Описание**|
| :- | :- |
|[Color](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|Указывает цвет и прозрачность линии.|
|[Width](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|Указывает ширину линии|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|Определяет, как линии отображаются в точках пересечения сегментов линий.|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|Указывает, как следует рисовать символьную линию.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|Указывает массив расстояний, определяющих длины чередующихся тире и пробелов в пунктирных линиях.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|Указывает расстояние от начала линии до начала шаблона штрихов.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>Указывает, как отображаются линии на их концах.</p><p>- Butt - острый квадратный край</p><p>- Round - округлый край</p><p>- Square - слегка удлиненный квадратный край</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|Указывает смещение от исходной линии. Для положительного расстояния смещение будет слева от входной линии (относительно направления линии). Для отрицательного расстояния оно будет справа.|

### **Типы геометрий**
` `Символ может применяться к геометриям любого типа.

|**Размерность геометрии**|**Типы геометрий**|**Поведение при рендеринге**|
| :-: | :-: | :-: |
|**Точка**|Point, MultiPoint|Рисует линию небольшой длины с горизонтальной ориентацией, центрированную на точке, с двумя концевыми заглушками.|
|**Линия**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Рисует линию.|
|**Поверхность**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Закрытый контур геометрии используется в качестве линии (без концевых заглушек)|

Для GeometryCollections поведение рендеринга определяется отдельно для каждой геометрии внутри коллекции. Слои с типом Mixed geometry следуют логике для GeometryCollections.

Используйте MixedGeometrySymbolizer, чтобы ограничить символ определенными типами геометрий.

### **Примеры**
По умолчанию символ линии рисует черные линии:



Здесь показано, как изменить цвет линии на синий:



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

Для более сложных сценариев может потребоваться динамически корректировать стиль линии на основе значений атрибутов объектов. Вот как это сделать:



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |



Вы также можете добавить метки к своим линиям. Посетите [Примеры маркировки линий](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) для примеров.
