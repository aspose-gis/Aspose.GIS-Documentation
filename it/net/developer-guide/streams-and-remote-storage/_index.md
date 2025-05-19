---
title: "Flussi e Archiviazione Remota"
type: docs
url: /it/net/streams-and-remote-storage/
weight: 70
---

## **Lavorare con Formati Multi-File**
Alcuni formati di dati GIS dividono il contenuto in più file. Ad esempio, un shapefile deve avere almeno tre file: *.shp, *.shx e *.dbf. Questi formati richiedono che tutti i file siano archiviati in una particolare struttura di directory con uno schema predefinito per i nomi dei file.

Allo stesso tempo, i file possono essere archiviati su un server remoto o in un'altra posizione accessibile solo tramite flussi. I flussi mancano di informazioni sui nomi dei file e sulla struttura delle directory, rendendo impossibile ai driver del formato file determinare come elaborare i dati. Aspose.GIS risolve questo problema fornendo il meccanismo dei percorsi astratti.

Un percorso astratto rappresenta un percorso verso un file (o una directory) in uno storage simile a un filesystem. Lo storage può essere qualsiasi cosa che abbia un concetto di file e directory, da un archivio a un server FTP. Definisce come eseguire operazioni tipiche sui file, come l'apertura di un file o l'elenco di una directory.

È possibile specificare come eseguire le operazioni sui file per il proprio storage implementando una classe che eredita [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) e fornendo implementazioni per i suoi metodi astratti.
## **Esempio: Azure Blob Storage**
Il repository Aspose.GIS Examples contiene un esempio di un'implementazione completamente funzionale di un percorso astratto personalizzato per Azure Blob Storage. Questo showcase mostra come leggere uno shapefile direttamente da Azure Blob Storage. Puoi trovarlo qui: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **Formati a file singolo (GeoJSON, KML)**
I formati di dati GIS come GeoJSON e KML possono archiviare tutti i dati per un layer in un unico file. Se è possibile ottenere un flusso per il file, è possibile saltare l'implementazione di un percorso astratto personalizzato e utilizzare il metodo [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) per istanziare un percorso astratto per il flusso.
### **Leggi un file da un flusso**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **Scrivi un file su un flusso**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
