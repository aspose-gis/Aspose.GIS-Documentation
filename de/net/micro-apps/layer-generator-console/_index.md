---
title: "Layer-Generator Konsolenanwendung"
type: docs
url: /de/net/layer-generator-console
weight: 50
---

## Zusammenfassung

Diese Konsolenanwendung dient zur Erzeugung geometrischer Objekte verschiedener Typen und deren Speicherung im gewählten Format. Sie ermöglicht die Erstellung von Punkten, Polygonen und Polylinien, die Angabe der Anzahl zu erzeugender Objekte sowie die Wahl des Ausgabeformats für die Speicherung.

## Verwendung

Befehlssyntax:

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

Argumente:

```
-t, --type: Geometrietyp. Einer der folgenden: Punkt, Polygon, Polylinie.

-c, --count: Erforderlich. Anzahl der zu erzeugenden Objekte. Zum Beispiel: 15.

-f, --fileName: Erforderlich. Dateiname zum Speichern. Geben Sie den Dateinamen und die Erweiterung an. Zum Beispiel: test.json.

-o, --outputFormat: Ausgabeformat. Sehen Sie sich hier die unterstützten Dateiformate an.

--help: Zeigt Hilfsinformationen für den Befehl an.

--version: Zeigt die Versionsinformationen der Anwendung an.
```

Ein Beispielbefehl zum Erstellen von 15 zufälligen Punkten und Speichern in einer Datei im Format "test.json":

```
app.exe -t Point -c 15 -f test.json -o json
```

## Installation und Lizenzierung

Wenn Sie die Anwendung verwenden möchten, müssen Sie das Archiv herunterladen und extrahieren. Bitte folgen Sie dem untenstehenden Link.

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

Obwohl die Aspose.GIS Layer Generator Konsolenanwendung kostenlos ist, wird Aspose.GIS .NET wie üblich lizenziert, sodass Sie Ihre Lizenz über die Anwendung wiederverwenden oder die Anwendung mit Aspose.GIS .NET im Testmodus evaluieren oder eine temporäre Lizenz beantragen können.

## Fazit

Der Geometric Objects Generator ist eine praktische Konsolenanwendung, die Ihnen hilft, Beispiele für Geometrien verschiedener Typen zu erstellen und in dem gewünschten Format zu speichern. Es ist ein nützliches Werkzeug für die Arbeit mit georäumlichen Daten und die Entwicklung von Geoinformationssystemen.
