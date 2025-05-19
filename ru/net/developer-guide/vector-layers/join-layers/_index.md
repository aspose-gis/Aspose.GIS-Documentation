---
title: Объединение векторных слоев с использованием библиотеки GIS C#
linktitle: Объединить слои
type: docs
url: /ru/net/Join-layers/
weight: 52
description: Приведенные в статье фрагменты кода можно использовать для объединения векторных слоев ГИС с помощью API C#.
---

## **Объединение векторных слоев**
API Aspose.GIS позволяет объединять векторные слои, как показано на примере кода ниже.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinByName.cs" >}}


## **Объединение слоя с использованием нескольких атрибутов**
API Aspose.GIS позволяет объединять несколько атрибутов, как показано на примере кода ниже.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinFewAttributes.cs" >}}

## **Объединение слоя с использованием собственного компаратора**
API Aspose.GIS позволяет объединять слой, используя собственный компаратор, как показано на примере кода ниже. Этот подход хорош, когда необходимо объединять данные, используя нечувствительные к регистру строки.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinWithConditionComparer.cs" >}}

Реализация компаратора.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-InsensitiveComparer.cs" >}}
