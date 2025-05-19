---
title: Об’єднання векторних шарів за допомогою GIS C# бібліотеки
linktitle: Об'єднати шари
type: docs
url: /uk/net/Join-layers/
weight: 52
description: Код, наведений у статті, можна використовувати для об’єднання векторних шарів ГІС за допомогою C# API.
---

## **Об’єднання векторних шарів**
Aspose.GIS API дозволяє об'єднувати векторні шари, як показано в наведеному нижче фрагменті коду.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinByName.cs" >}}


## **Об’єднання шару за допомогою кількох атрибутів**
Aspose.GIS API дозволяє об'єднати кілька атрибутів, як показано в наведеному нижче фрагменті коду.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinFewAttributes.cs" >}}

## **Об’єднання шару за допомогою власного Comparer**
Aspose.GIS API дозволяє об'єднати шар, використовуючи власний Comparer, як показано в наведеному нижче фрагменті коду. Цей підхід добре підходить, коли потрібно об’єднувати дані, використовуючи нечутливі до регістру рядки.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinWithConditionComparer.cs" >}}

Реалізація Comparer.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-InsensitiveComparer.cs" >}}
