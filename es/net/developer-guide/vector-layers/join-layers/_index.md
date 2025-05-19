---
title: Unir capas vectoriales usando la biblioteca GIS C#
linktitle: Unir capas
type: docs
url: /es/net/Join-layers/
weight: 52
description: Los fragmentos de código proporcionados en el artículo se pueden utilizar para unir capas vectoriales GIS utilizando la API C#.
---

## **Unir capas vectoriales**
La API de Aspose.GIS le permite unir las capas vectoriales como se muestra en el fragmento de código a continuación.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinByName.cs" >}}


## **Unir capa usando pocos atributos**
La API de Aspose.GIS le permite unir unos pocos atributos como se muestra en el fragmento de código a continuación.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinFewAttributes.cs" >}}

## **Unir capa usando un comparador propio**
La API de Aspose.GIS le permite unir una capa utilizando su propio comparador como se muestra en el fragmento de código a continuación. Este enfoque es bueno cuando necesita unir datos utilizando cadenas que no distinguen entre mayúsculas y minúsculas.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinWithConditionComparer.cs" >}}

Implementación del comparador.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-InsensitiveComparer.cs" >}}
