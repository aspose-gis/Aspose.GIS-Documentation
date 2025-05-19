---
title: Символика - C# GIS API
linktitle: "Символика"
type: docs
url: /bg/net/symbology/
weight: 10
description: GIS C# Библиотека или API поддържа символизатори за рисуване на геометрия на обекти като Маркер, Линия, Запълване и комбиниране на символизатори за създаване на по-сложни визуализации.
---

Символизатор е начин да се изобрази геометрията на обект върху карта.

|** **|**Символизатор**|**API Клас**|**Описание**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**Маркер**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Рисува предварително дефинирана форма с персонализируемо запълване и контур. |
|![todo:image_alt_text](symbology_2.png)|**Линия**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Рисува линия с персонализируемо стилизиране.|
|![todo:image_alt_text](symbology_3.png)|**Запълване**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Запълва полигон или област, ограничена от линия с персонализируемо запълване и контур.|
В допълнение към символизаторите, които извършват действително рисуване, има редица други символизатори, които позволяват комбиниране на други символизатори за създаване на по-сложни визуализации.

|**Символизатор**|**API Клас**|**Описание**|
| :- | :- | :- |
|**Наслоен Символизатор**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Рисува обект с няколко символизатора един върху друг|
|**Смесен Геометричен Символизатор**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Рисува обекти от слоеве, които съдържат геометрии от смесени типове със специфичен символизатор за всеки тип геометрия|
|**Базиран на Правила Символизатор**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Избира символизатор, който да се приложи към обект според правила, посочени от потребителя.|
|**Символизатор на Клъстер Маркери**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|Рисува клъстериране на маркери, групиране на тези елементи.|
|**Символизатор за Генериране на Геометрия**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Позволява да се замести геометрията на обекта преди рендиране.|
|**Нулев Символизатор**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|Не рисува нищо. Полезен, когато се комбинира с други символизатори, като например базиран на правила символизатор.|
