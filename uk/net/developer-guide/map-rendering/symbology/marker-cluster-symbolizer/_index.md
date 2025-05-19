---
title: "Маркерний кластерний символізатор"
type: docs
url: /uk/net/marker-cluster-symbolizer/
weight: 65
description: Маркерний кластерний символізатор у GIS C# бібліотеці або API дозволяє кластеризацію маркерів на вказаній відстані.
---

## **Маркерний кластерний символізатор**
Маркерний кластерний символізатор є одним з розширених символізаторів. Він дозволяє кластеризувати маркери на вказаній відстані.

У цьому прикладі C#, ми намалювали центри кластерів як червоні кола. Також, ми намалювали всі вкладені точки кластера, використовуючи різні кольори. Для цього ми використовували функцію FeaturesBasedConfiguration, яка налаштовує власний стиль для кожного кластера.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterMarkerSymbolizer.cs" >}}

Ось результат:

![points cluster](points-cluster.png)

## **Відображення загальної кількості елементів**

Цей приклад відображає загальну кількість елементів у кластері.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterTextSymbolizer.cs" >}}

Ось результат:

![digits cluster](digits-cluster.png)
