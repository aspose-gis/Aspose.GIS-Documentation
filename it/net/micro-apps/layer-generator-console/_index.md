---
title: "Applicazione Console Generatore di Livelli"
type: docs
url: /it/net/layer-generator-console
weight: 50
---

## Riepilogo

Questa applicazione console è progettata per generare oggetti geometrici di vari tipi e salvarli nel formato scelto. Permette di creare punti, poligoni e polilinee, specificare il numero di oggetti da generare e scegliere il formato di output per il salvataggio.

## Utilizzo

Sintassi del comando:

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

Argomenti:

```
-t, --type: Tipo di geometria. Uno dei seguenti: Point, Polygon, Polyline.

-c, --count: Obbligatorio. Numero di oggetti da generare. Ad esempio: 15.

-f, --fileName: Obbligatorio. Nome del file per il salvataggio. Specificare il nome del file e l'estensione. Ad esempio: test.json.

-o, --outputFormat: Formato di output. Vedere i formati di file supportati qui.

--help: Visualizza le informazioni di aiuto per il comando.

--version: Visualizza le informazioni sulla versione dell'applicazione.
```

Un esempio di comando per creare 15 punti casuali e salvarli in un file con il formato "test.json":

```
app.exe -t Point -c 15 -f test.json -o json
```

## Installazione e Licenza

Se si desidera utilizzare l'applicazione, è necessario scaricare l'archivio ed estrarlo. Seguire il link sottostante.

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

Sebbene l'Applicazione Console Generatore di Livelli Aspose.GIS sia gratuita, Aspose.GIS .NET è concesso in licenza come al solito, quindi è possibile riutilizzare la propria licenza tramite l'applicazione o valutare l'applicazione utilizzando Aspose.GIS .NET in modalità trial oppure richiedere una licenza temporanea.

## Conclusione

Il Generatore di Oggetti Geometrici è una comoda applicazione console che aiuta a creare campioni di geometria di vari tipi e salvarli nel formato desiderato. È uno strumento utile per lavorare con dati geospaziali e sviluppare sistemi di informazione geografica.
