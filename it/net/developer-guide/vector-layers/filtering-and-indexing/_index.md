---
title: Filtraggio e indicizzazione di layer vettoriali GIS in C#
linktitle: Filtraggio e indicizzazione
second_title: Aspose.GIS per .NET
type: docs
url: /it/filtering-and-indexing/
weight: 30
description: Con la libreria o API GIS C# .NET, puoi filtrare i layer vettoriali GIS in base ai valori degli attributi o ai limiti spaziali. Puoi anche utilizzare gli indici per accelerare il filtraggio e le query spaziali.
---

Con Aspose.GIS per .NET puoi filtrare i layer in base ai valori degli attributi o ai limiti spaziali. Puoi anche usare gli indici per velocizzare il filtraggio e le query spaziali.
## **Indice degli attributi**
### **Filtro senza indice**
Ecco come filtrare un layer in base ai valori di un attributo:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **Filtro con indice**
Il codice precedente va bene finché il layer viene filtrato solo una volta. Ma, se il layer è suscettibile di essere interrogato più volte, possiamo beneficiare degli indici degli attributi. Richiede un po' di tempo per costruire l'indice degli attributi, ma può essere riutilizzato più volte per accelerare il filtraggio.

Il seguente esempio utilizza un file di indice degli attributi per velocizzare il filtraggio del layer in base ai valori dell'attributo:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **Salva le funzionalità filtrate**
Le funzionalità filtrate possono essere salvate nei layer:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **Renderizza le funzionalità filtrate**
È anche possibile renderizzare le funzionalità filtrate. Il seguente esempio utilizza l'indice degli attributi per selezionare rapidamente tutte le funzionalità con una popolazione superiore a 2000 e aggiungerle alla mappa:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **Indice spaziale**
Gli indici spaziali vengono utilizzati per accelerare le query spaziali. Proprio come gli indici degli attributi, gli indici spaziali vengono riutilizzati dopo la creazione.
### **Trova le funzionalità più vicine a un punto**
Ecco come utilizzare l'indice spaziale per velocizzare la ricerca della funzionalità più vicina a un determinato punto:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **Seleziona le funzionalità che intersecano con una geometria**
Il seguente esempio utilizza l'indice spaziale per velocizzare la selezione delle funzionalità che intersecano una geometria:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
