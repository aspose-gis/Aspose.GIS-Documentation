---
title: Символіка - C# GIS API
linktitle: "Символіка"
type: docs
url: /uk/net/symbology/
weight: 10
description: GIS C# Бібліотека або API підтримує символізатори для малювання геометрії об'єктів, таких як Маркер, Лінія, Заповнення та комбінування символізаторів для створення більш складних візуалізацій.
---

Символізатор - це спосіб малювання геометрії об’єкта на карті.

|** **|**Символізатор**|**Клас API**|**Опис**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**Маркер**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Малює попередньо визначену форму з настроюваним заповненням та обведенням.|
|![todo:image_alt_text](symbology_2.png)|**Лінія**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Малює лінію з настроюваним стилем.|
|![todo:image_alt_text](symbology_3.png)|**Заповнення**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Заповнює полігон або область, обмежену лінією, настроюваним заповненням та обведенням.|
На додаток до символізаторів, які виконують фактичне малювання, існує ряд інших символізаторів, які дозволяють комбінувати інші символізатори для створення більш складних візуалізацій.

|**Символізатор**|**Клас API**|**Опис**|
| :- | :- | :- |
|**Багатошаровий Символізатор**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Малює об’єкт з кількома символізаторами один на одного|
|**Символізатор Змішаної Геометрії**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Малює об’єкти з шарів, які містять геометрію змішаних типів, із певним символізатором для кожного типу геометрії|
|**Символізатор на основі правил**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Вибирає символізатор, який потрібно застосувати до об’єкта за правилами, визначеними користувачем.|
|**Символізатор Кластерів Маркерів**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|Малює кластеризацію маркерів, групування цих елементів.|
|**Символізатор Генератора Геометрії**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Дозволяє замінити геометрію об’єкта перед рендерингом.|
|**Нульовий Символізатор**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|Нічого не малює. Корисно при комбінуванні з іншими символізаторами, такими як символізатор на основі правил.|
