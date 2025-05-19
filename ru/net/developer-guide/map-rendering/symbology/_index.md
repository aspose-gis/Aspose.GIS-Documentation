---
title: Символика - C# GIS API
linktitle: "Символика"
type: docs
url: /ru/net/symbology/
weight: 10
description: GIS C# Библиотека или API поддерживает символизаторы для рисования геометрии объектов, таких как Маркер, Линия, Заливка и комбинирование символизаторов для создания более сложных визуализаций.
---

Символизатор - это способ отрисовки геометрии объекта на карте.

|** **|**Символизатор**|**API Класс**|**Описание**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**Маркер**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Рисует предопределенную форму с настраиваемой заливкой и обводкой.|
|![todo:image_alt_text](symbology_2.png)|**Линия**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Рисует линию с настраиваемым стилем.|
|![todo:image_alt_text](symbology_3.png)|**Заливка**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Заполняет многоугольник или область, ограниченную линией, с настраиваемой заливкой и обводкой.|
В дополнение к символизаторам, которые выполняют фактическое рисование, существует ряд других символизаторов, позволяющих комбинировать другие символизаторы для создания более сложных визуализаций.

|**Символизатор**|**API Класс**|**Описание**|
| :- | :- | :- |
|**Многослойный Символизатор**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Рисует объект с несколькими символизаторами друг над другом|
|**Символизатор Смешанной Геометрии**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Рисует объекты из слоев, содержащих геометрию смешанных типов, с определенным символизатором для каждого типа геометрии|
|**Символизатор на основе правил**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Выбирает символизатор для применения к объекту по правилам, указанным пользователем.|
|**Символизатор Кластеров Маркеров**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|Рисует кластеризацию маркеров, группировку этих элементов.|
|**Символизатор Генератора Геометрии**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Позволяет заменить геометрию объекта перед рендерингом.|
|**Нулевой Символизатор**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|Ничего не рисует. Полезен при комбинировании с другими символизаторами, такими как символизатор на основе правил.|
