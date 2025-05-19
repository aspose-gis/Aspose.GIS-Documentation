---
title: "Licenze"
second_title: Aspose.GIS for .NET
type: docs
url: /it/net/licensing/
weight: 50
keywords: c# gis library, .net gis library
description: Valuta la libreria GIS C# .NET o l'API con alcune limitazioni. Applica una licenza utilizzando un oggetto File o Stream oppure come Risorsa Incorporata.
---

## **Valuta Aspose.GIS per .NET**
Puoi scaricare gratuitamente Aspose.GIS per .NET. Prima di applicare una licenza, il componente funziona in modalità di valutazione. Quando acquisti una licenza e aggiungi alcune righe di codice per applicarla, le limitazioni della valutazione vengono rimosse.

{{% alert color="primary" %}} Se desideri testare Aspose.GIS senza limitazioni della modalità di valutazione, puoi richiedere una Licenza Temporanea di 30 giorni. Consulta [Ottieni una licenza temporanea](https://purchase.aspose.com/temporary-license). {{% /alert %}}
### **Limitazioni della Modalità di Valutazione**
Quando si esegue in modalità di valutazione (senza una licenza applicata), Aspose.GIS fornisce la piena funzionalità del prodotto ad eccezione di alcune limitazioni della valutazione.

1. Non più di **15 documenti** possono essere aperti e/o creati **per ora**.
1. Non più di **100 elementi** possono essere accessibili in ogni documento (lettura o scrittura).
1. Non più di **10.000 dati raster** possono essere accessibili in ogni documento (lettura o scrittura).
1. Il numero massimo consentito di elementi in un documento per le operazioni di conversione è **50**.

Quando si esegue in modalità con licenza, puoi elaborare un numero illimitato di documenti e funzionalità.
## **Applicazione di una Licenza**
La licenza è un file XML semplice che contiene dettagli come il nome del prodotto, il numero di sviluppatori a cui è concessa in licenza, la data di scadenza dell'abbonamento e così via. Il file è firmato digitalmente, quindi non modificarlo. Anche l'aggiunta involontaria di un'interruzione di riga extra al file lo invaliderà.

È necessario impostare una licenza prima di utilizzare Aspose.GIS se si desidera evitare le sue limitazioni della valutazione. È richiesto impostare una licenza solo una volta per applicazione (o processo).
### **Impostazione di una Licenza in Aspose.GIS per .NET**
In Aspose.GIS, la licenza può essere caricata da un file, stream o risorsa incorporata. Aspose.GIS tenta di trovare la licenza nelle seguenti posizioni:

- Percorso esplicito
- La cartella che contiene Aspose.GIS.dll
- La cartella che contiene l'assembly che ha chiamato Aspose.GIS.dll
- La cartella che contiene l'assembly di ingresso (il tuo .exe)
- Una risorsa incorporata nell'assembly che ha chiamato Aspose.GIS.dll. Esistono due metodi comuni per impostare la licenza, che vengono discussi di seguito:
### **Applica Licenza utilizzando File o Oggetto Stream**
Il modo più semplice per impostare una licenza è inserire il file di licenza nella stessa cartella di Aspose.GIS.dll e specificare solo il nome del file senza il suo percorso.

{{< highlight java >}}

 // Instanzia un'istanza della licenza e imposta il file di licenza tramite il suo percorso

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // Instanzia un'istanza della licenza e imposta la licenza tramite uno stream

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}

Quando chiami il metodo SetLicense, il nome della licenza deve essere lo stesso del nome del tuo file di licenza. Ad esempio, potresti modificare il nome del file di licenza in "Aspose.GIS.lic.xml". Quindi nel tuo codice, dovresti utilizzare il nome della licenza modificato (ovvero Aspose.GIS.lic.xml) per il metodo SetLicense.

## **Inclusione del File di Licenza come Risorsa Incorporata**
Un altro modo pratico per impacchettare la licenza con la tua applicazione e assicurarti che non vada persa è includerla come risorsa incorporata in uno degli assembly che chiama la dll del componente (incluso in Aspose.GIS). Per includere il file di licenza come risorsa incorporata, segui i seguenti passaggi:

- In Visual Studio, includi il file di licenza (.lic) nel progetto utilizzando il menu File | Aggiungi elemento esistente...
- Seleziona il file nell'Esplora soluzioni e imposta Azione di compilazione su Risorsa incorporata nella finestra Proprietà
- Per accedere alla licenza incorporata nell'assembly (come risorsa incorporata), non è necessario chiamare i metodi GetExecutingAssembly e GetManifestResourceStream della classe System.Reflection.Assembly di Microsoft .NET Framework. Tutto ciò che devi fare è aggiungere il file di licenza come risorsa incorporata al tuo progetto e passare il nome del file di licenza al metodo License.SetLicense. La classe License troverà automaticamente il file di licenza nelle risorse incorporate.

Consulta l'esempio seguente per comprendere questo metodo di impostazione della licenza (incorporata) nelle tue applicazioni.

{{< highlight java >}}

 // Instanzia la classe Licenza

Aspose.Gis.License license = new Aspose.Gis.License();

// Passa solo il nome del file di licenza incorporato nell'assembly

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **Applicazione della Chiave Misurata**
[L'API di Aspose.GIS per .NET](/gis/net/) consente agli sviluppatori di applicare una chiave misurata. È un nuovo meccanismo di licenza. Il nuovo meccanismo di licenza verrà utilizzato insieme al metodo di licenza esistente. Quei clienti che desiderano essere fatturati in base all'utilizzo delle funzionalità dell'API possono utilizzare la licenza misurata. Per maggiori dettagli, consulta la sezione [FAQ sulla licenza misurata](https://purchase.aspose.com/faqs/licensing/metered).

È stata introdotta una nuova classe **Metered** per applicare la chiave misurata. Di seguito è riportato il codice di esempio che dimostra come impostare la chiave pubblica e privata misurata.

**[C#]**

{{< highlight csharp >}}

 // imposta le chiavi pubbliche e private misurate
 
Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();
 
// Accedi alla proprietà setMeteredKey e passa le chiavi pubblica e privata come parametri
 
metered.SetMeteredKey("*****", "*****");
 
// ESEGUI ELABORAZIONE
 
// ottieni l'importo dei dati misurati
 
decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();
 
// Visualizza le informazioni
 
Console.WriteLine("Importo Consumato : " + amount.ToString());

{{< /highlight >}}
