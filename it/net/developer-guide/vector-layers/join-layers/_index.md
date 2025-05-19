---
title: Unisci i layer vettoriali utilizzando la libreria GIS C#
linktitle: Unisci i layer
type: docs
url: /it/Join-layers/
weight: 52
description: I frammenti di codice forniti nell'articolo possono essere utilizzati per unire i layer vettoriali GIS utilizzando l'API C#.
---

## **Unisci i layer vettoriali**
L'API Aspose.GIS consente di unire i layer vettoriali come mostrato nel frammento di codice sottostante.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinByName.cs" >}}


## **Unisci i layer utilizzando pochi attributi**
L'API Aspose.GIS consente di unire alcuni attributi come mostrato nel frammento di codice sottostante.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinFewAttributes.cs" >}}

## **Unisci i layer utilizzando un comparatore personalizzato**
L'API Aspose.GIS consente di unire un layer utilizzando un comparatore personalizzato come mostrato nel frammento di codice sottostante. Questo approccio è utile quando è necessario unire i dati utilizzando stringhe non sensibili al maiuscolo/minuscolo.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-JoinWithConditionComparer.cs" >}}

Implementazione del comparatore.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-JoinedLayer-InsensitiveComparer.cs" >}}
