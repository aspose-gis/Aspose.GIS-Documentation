---
title: "Символизатор на клъстерни маркери"
type: docs
url: /bg/net/marker-cluster-symbolizer/
weight: 65
description: Символизаторът на клъстерни маркери в GIS C# Библиотека или API позволява групирането на маркери на определено разстояние.
---

## **Символизатор на клъстерни маркери**
Символизаторът на клъстерни маркери е един от усъвършенстваните символизатори. Той позволява групирането на маркери на определено разстояние.

В този C# пример, центровете на клъстерите са изобразени като червени кръгове. Също така, всички вложени точки на клъстери са изобразени с помощта на различни цветове. За да направим това, използвахме функцията FeaturesBasedConfiguration, която настройва собствен стил за всеки клъстер.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterMarkerSymbolizer.cs" >}}

Ето резултата:

![points cluster](points-cluster.png)

## **Изобразяване на общия брой елементи**

Този пример показва общия брой елементи в клъстера.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ClusterTextSymbolizer.cs" >}}

Ето резултата:

![digits cluster](digits-cluster.png)
