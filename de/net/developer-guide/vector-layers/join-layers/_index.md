---
title: Vektorlayer mithilfe der GIS C#-Bibliothek zusammenführen
linktitle: Layer zusammenführen
type: docs
url: /de/Join-layers/
weight: 52
description: Die in dem Artikel bereitgestellten Codeausschnitte können verwendet werden, um GIS-Vektorlayer mit der C#-API zusammenzuführen.
---

## **Vektorlayer zusammenführen**
Die Aspose.GIS API ermöglicht es Ihnen, die Vektorlayer wie im folgenden Codeausschnitt gezeigt zusammenzuführen.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinByName.cs" >}}


## **Layer mithilfe weniger Attribute zusammenführen**
Die Aspose.GIS API ermöglicht es Ihnen, einige Attribute wie im folgenden Codeausschnitt gezeigt zusammenzuführen.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinFewAttributes.cs" >}}

## **Layer mithilfe eines eigenen Comparers zusammenführen**
Die Aspose.GIS API ermöglicht es Ihnen, einen Layer mit einem eigenen Comparer wie im folgenden Codeausschnitt gezeigt zusammenzuführen. Dieser Ansatz ist gut, wenn Sie Daten mithilfe von nicht zwischen Groß- und Kleinschreibung unterscheidenden Zeichenfolgen zusammenführen müssen.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinWithConditionComparer.cs" >}}

Implementierung des Comparers.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-InsensitiveComparer.cs" >}}
