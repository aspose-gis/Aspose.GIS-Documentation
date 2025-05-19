---
title: "Come unire i layer utilizzando la geometria o gli attributi"
type: docs
url: /it/how-to-join-layers
weight: 70
---

## Riepilogo

Nei GIS, le join sono un meccanismo potente per combinare informazioni da diversi layer in base a un attributo comune o a una relazione spaziale. Le join consentono di unire i dati degli attributi da un layer (il layer sorgente) con un altro layer (il layer target) utilizzando un campo comune o una posizione spaziale. La prima è l'unione dei dati per chiave (attributo nella tabella). Utilizzando un campo comune, come una chiave univoca, è possibile collegare i record in una tabella con i record in un'altra tabella. Il secondo approccio è l'unione dei dati per posizione (spazialmente). Supportiamo entrambi gli approcci e ti offriamo la possibilità di utilizzarli a seconda delle tue esigenze.

Supponiamo che tu abbia ricevuto dati che descrivono la variazione percentuale della popolazione per diversi distretti e desideri generare diverse mappe della crescita demografica basate su queste informazioni. Mentre i tuoi dati sulla popolazione sono archiviati in una tabella nel tuo database e condividono un campo comune con il tuo layer, puoi unire questi dati ai tuoi oggetti geografici e utilizzare campi aggiuntivi per l'etichettatura, la categorizzazione, l'interrogazione o l'analisi degli oggetti layer.

In genere, esegui le join dei dati in base a un valore di campo che esiste in entrambe le tabelle. I nomi dei campi non devono necessariamente corrispondere, ma i tipi di dati dovrebbero essere gli stessi: numeri con numeri, stringhe con stringhe e così via. Puoi eseguire la join dei dati utilizzando lo strumento di geoprocessing "Add Join". Quando si uniscono gli attributi, i campi uniti vengono aggiunti dinamicamente alla tabella esistente. Le proprietà del campo come alias, visibilità e formattazione numerica vengono preservate quando si aggiunge o rimuove la join.

## Capacità di unirsi per campo chiave

- Questo approccio ti consente di **collegare record da tabelle diverse** in base a un campo chiave comune. Puoi specificare il campo chiave da utilizzare per il confronto per stabilire la relazione tra i record. Questo è particolarmente utile quando è necessario unire dati basati su un identificatore o un altro attributo univoco.

Specificando il metodo per confrontare i dati in base al campo chiave:

- Puoi definire **diversi metodi di confronto** per il campo chiave durante l'unione dei dati. Ad esempio, puoi scegliere di avere una corrispondenza esatta, confrontare in base a un modello o all'interno di un intervallo di valori. Ciò consente una determinazione più precisa delle relazioni tra i record e offre il controllo sul processo di unione dei dati.

Specificando un elenco di nomi degli attributi da unire:

- Quando si uniscono i dati, è possibile specificare **attributi specifici** che devono essere uniti. Questo ti consente di scegliere solo gli attributi necessari per l'unione e gestire la struttura della tabella risultante.

## Capacità di unirsi utilizzando la geometria

- Questo approccio ti consente di collegare dati in base alla loro **posizione spaziale**. Puoi definire un raggio di ricerca all'interno del quale verranno cercati gli oggetti geometrici più vicini per l'unione. Questo è utile quando è necessario unire i dati in base alla loro posizione geografica.

Controllo del raggio di ricerca per la ricerca di oggetti geometrici più vicini:

- Puoi controllare **il raggio di ricerca** durante l'unione dei dati in base alla posizione. Specificando un valore di raggio, determini la distanza entro cui verranno cercati gli oggetti più vicini per l'unione. Questo offre il controllo su quali oggetti parteciperanno al processo di unione dei dati in base alla loro relazione spaziale.

## Progetto Demo

Per comprendere meglio la funzionalità della nostra libreria, consideriamo [un esempio del suo utilizzo](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Layers.Join). Questo codice illustra come unire i layer vettoriali per attributi o geometria.

Il codice fornito è composto da due metodi, JoinByIndex() e JoinByCoords(), che dimostrano operazioni di join dei dati utilizzando una classe LayerConstructor.

Nel metodo JoinByIndex():

- Vengono create liste di geometrie con attributi associati.

- Viene inizializzato un oggetto LayerConstructor.

- Il metodo crea un layer vettoriale e un layer di geometria utilizzando le geometrie fornite.

- Il layer di geometria viene unito in base a un identificatore univoco ("Id") utilizzando il metodo JoinLayersById().

- Il layer vettoriale unito risultante viene restituito.

Nel metodo JoinByCoords():

- Vengono create liste di geometrie con attributi associati.

- Viene inizializzato un oggetto LayerConstructor.

- I layer di geometria vengono creati utilizzando le geometrie fornite.

- I layer di geometria vengono uniti in base alle coordinate corrispondenti utilizzando il metodo JoinLayersByCoords().

- Il layer vettoriale unito risultante viene restituito.

In sintesi, questi metodi mostrano due approcci diversi per l'unione dei dati: uno basato su un identificatore univoco e l'altro basato sulle coordinate corrispondenti. La classe LayerConstructor facilita queste operazioni di join dei dati.

## Opzioni di Join per Index

La classe JoinOptions fornisce una serie di opzioni per configurare le join dei layer. Approfondiamo ogni opzione:

- **JoinAttributeName**: questa opzione ti consente di specificare il nome dell'attributo dal layer unito il cui valore verrà utilizzato nel confronto della condizione. Stabilisce la connessione tra i due layer in base a questo attributo.

- **TargetAttributeName**: con questa opzione, puoi specificare il nome dell'attributo dal layer principale che verrà confrontato con l'attributo dal layer unito. Aiuta a determinare le funzionalità corrispondenti tra i layer.

- **JoinAttributeNames**: questa opzione ti consente di specificare un elenco di nomi degli attributi che desideri unire. Se questo elenco viene lasciato vuoto o impostato su null, tutti gli attributi dal layer unito verranno inclusi nell'operazione di join. Tuttavia, selezionando nomi di attributi specifici, puoi controllare gli attributi che vengono uniti, il che può essere utile per ottimizzare l'utilizzo della memoria e i tempi di elaborazione.

- **ConditionComparer**: questa opzione ti consente di definire una logica personalizzata per confrontare i valori degli attributi tra le funzionalità dei due layer. Per impostazione predefinita, utilizza il comparatore EqualityComparer.Default, che verifica l'uguaglianza. Tuttavia, puoi fornire un tuo comparatore personalizzato che implementa IEqualityComparer per requisiti di confronto più specializzati.

- **JoinedAttributesPrefix**: questa opzione ti consente di specificare un prefisso stringa per i nomi degli attributi del layer unito. Il valore predefinito è "joined_", il che significa che gli attributi uniti saranno preceduti da "joined_" nel layer unito risultante. Questo prefisso aiuta a differenziare gli attributi uniti dagli attributi originali del layer principale.

La classe JoinOptions fornisce flessibilità e controllo su vari aspetti del processo di join dei layer. Puoi specificare gli attributi da unire, personalizzare la logica di confronto e definire un prefisso per gli attributi uniti risultanti. Queste opzioni ti consentono di adattare l'operazione di join in base alle tue esigenze specifiche e ottenere informazioni significative dai layer uniti.

## Opzioni di Join per Geometria

La classe **JoinByGeometryOptions** rappresenta le opzioni per unire i layer in base alla geometria. Esploriamo la funzionalità di ciascuna opzione:

- **Radius**: questa opzione specifica il raggio all'interno del quale verrà cercata la geometria unita. Determina la prossimità entro cui le funzionalità dal layer principale verranno abbinate alle funzionalità dal layer unito in base alla loro relazione spaziale.

- **ConditionComparer**: questa opzione ti consente di definire una logica personalizzata per confrontare i valori degli attributi dalle funzionalità dei due layer. Per impostazione predefinita, utilizza EqualityComparer.Default, che verifica l'uguaglianza. Tuttavia, puoi fornire un tuo comparatore personalizzato che implementa IEqualityComparer per requisiti di confronto più specifici.

- **JoinedAttributesPrefix**: questa opzione ti consente di specificare un prefisso stringa per i nomi degli attributi del layer unito. Il valore predefinito è "joined_", il che significa che gli attributi uniti saranno preceduti da "joined_" nel layer unito risultante. Questo prefisso aiuta a differenziare gli attributi uniti dagli attributi originali del layer principale.

La classe JoinByGeometryOptions fornisce i mezzi per personalizzare il processo di join dei layer in base alla loro relazione spaziale. Specificando un raggio di ricerca, puoi controllare l'estensione entro cui le geometrie verranno abbinate. Ciò consente una messa a punto precisa dell'operazione di join in base alla prossimità desiderata tra le funzionalità. L'opzione per fornire un comparatore personalizzato ti offre flessibilità nel confronto dei valori degli attributi e l'opzione per prefissare gli attributi uniti aiuta a differenziarli nel layer unito risultante.

Utilizzando queste opzioni, puoi eseguire la fusione di dati consapevole dello spazio e ottenere informazioni dai layer uniti che si basano sulla loro prossimità spaziale e sui valori degli attributi.

## Riepilogo

Il meccanismo di join dei dati nei GIS consente di combinare oggetti geometrici con i rispettivi attributi da diversi layer. Questo fornisce la possibilità di analizzare ed estrarre informazioni in base alle relazioni spaziali e degli attributi all'interno dei dati. Le opzioni disponibili consentono la personalizzazione del processo di join per soddisfare requisiti specifici e le esigenze di analisi nei dati GIS.

L'unione dei dati facilita varie attività, tra cui:

- Ricerca di oggetti che soddisfano criteri spaziali specifici, come l'identificazione di tutti gli edifici entro un raggio di 500 metri da un punto specifico.

- Combinazione di dati geografici per creare una panoramica più completa e informativa di una situazione.

- Analisi dei valori degli attributi degli oggetti in base a condizioni spaziali specifiche per identificare tendenze e modelli.

Le opzioni di join dei dati consentono la configurazione precisa del processo di corrispondenza degli oggetti. Queste opzioni includono la selezione degli attributi da unire, la definizione di una logica personalizzata per il confronto dei valori degli attributi e l'aggiunta di un prefisso ai nomi degli attributi dei dati uniti. Queste opzioni forniscono flessibilità e adattabilità al processo di join, soddisfacendo requisiti specifici e gli obiettivi dell'analisi dei dati nei GIS.

Il meccanismo di join dei dati svolge un ruolo significativo nell'integrazione e nell'analisi dei dati geografici, producendo una comprensione più completa della natura spaziale e degli attributi degli oggetti in esame.