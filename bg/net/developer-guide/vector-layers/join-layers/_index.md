---
title: Обединяване на векторни слоеве с помощта на GIS C# библиотека
linktitle: Обединяване на слоеве
type: docs
url: /bg/net/Join-layers/
weight: 52
description: Кодните фрагменти, предоставени в статията, могат да бъдат използвани за обединяване на GIS векторни слоеве с помощта на C# API.
---

## **Обединяване на векторни слоеве**
API на Aspose.GIS ви позволява да обедините векторните слоеве, както е показано в кода по-долу.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinByName.cs" >}}


## **Обединяване на слой с няколко атрибута**
API на Aspose.GIS ви позволява да обедините няколко атрибута, както е показано в кода по-долу.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinFewAttributes.cs" >}}

## **Обединяване на слой с помощта на собствен Comparer**
API на Aspose.GIS ви позволява да обедините слой, използвайки собствен Comparer, както е показано в кода по-долу. Този подход е добър, когато трябва да обедините данни, използвайки нечувствителни към регистъра низове.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinWithConditionComparer.cs" >}}

Реализация на Comparer.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-InsensitiveComparer.cs" >}}
