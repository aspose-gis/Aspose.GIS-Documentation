---
title: Łączenie warstw wektorowych za pomocą biblioteki GIS C#
linktitle: Połącz warstwy
type: docs
url: /pl/Join-layers/
weight: 52
description: Fragmenty kodu zawarte w artykule mogą być wykorzystywane do łączenia warstw wektorowych GIS przy użyciu API C#.
---

## **Łączenie warstw wektorowych**
API Aspose.GIS umożliwia łączenie warstw wektorowych, jak pokazano w poniższym fragmencie kodu.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinByName.cs" >}}


## **Łączenie warstwy przy użyciu kilku atrybutów**
API Aspose.GIS umożliwia łączenie kilku atrybutów, jak pokazano w poniższym fragmencie kodu.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinFewAttributes.cs" >}}

## **Łączenie warstwy przy użyciu własnego komparatora**
API Aspose.GIS umożliwia łączenie warstwy przy użyciu własnego komparatora, jak pokazano w poniższym fragmencie kodu. To podejście jest dobre, gdy potrzebujesz połączyć dane za pomocą ciągów znaków bez uwzględniania wielkości liter.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinWithConditionComparer.cs" >}}

Implementacja komparatora.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-InsensitiveComparer.cs" >}}
