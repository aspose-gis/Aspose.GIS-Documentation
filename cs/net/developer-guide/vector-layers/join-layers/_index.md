---
title: Spojování vektorových vrstev pomocí knihovny GIS C#
linktitle: Spojení vrstev
type: docs
url: /cs/net/Join-layers/
weight: 52
description: Úryvky kódu uvedené v článku lze použít ke spojování GIS vektorových vrstev pomocí C# API.
---

## **Spojování vektorových vrstev**
API Aspose.GIS vám umožňuje spojovat vektorové vrstvy, jak je ukázáno v následujícím úryvku kódu.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinByName.cs" >}}


## **Spojení vrstvy pomocí několika atributů**
API Aspose.GIS vám umožňuje spojit několik atributů, jak je ukázáno v následujícím úryvku kódu.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinFewAttributes.cs" >}}

## **Spojení vrstvy pomocí vlastního komparátoru**
API Aspose.GIS vám umožňuje spojit vrstvu pomocí vlastního komparátoru, jak je ukázáno v následujícím úryvku kódu. Tento přístup je dobrý, když potřebujete spojovat data pomocí necitlivých řetězců.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinWithConditionComparer.cs" >}}

Implementace komparátoru.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-InsensitiveComparer.cs" >}}
