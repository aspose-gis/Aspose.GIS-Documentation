---
title: "Streams und Remote-Speicher"
type: docs
url: /de/net/streams-and-remote-storage/
weight: 70
---

## **Arbeiten mit Mehrdateiformaten**
Einige GIS-Datenformate teilen den Inhalt in mehrere Dateien auf. Beispielsweise muss eine Shapefile mindestens drei Dateien haben: *.shp, *.shx und *.dbf. Diese Formate erfordern, dass alle Dateien in einer bestimmten Verzeichnisstruktur mit einem vordefinierten Muster für Dateinamen gespeichert werden.

Gleichzeitig können sich die Dateien auf einem Remote-Server oder an einem anderen Ort befinden, der nur über Streams zugänglich ist. Streams verfügen nicht über Informationen zu Dateinamen und Verzeichnisstrukturen, was es für Dateiformat-Treiber unmöglich macht, zu bestimmen, wie Daten verarbeitet werden sollen. Aspose.GIS löst dies durch die Bereitstellung des Mechanismus für abstrakte Pfade.

Ein abstrakter Pfad stellt einen Pfad zu einer Datei (oder einem Verzeichnis) in einem dateisystemähnlichen Speicher dar. Der Speicher kann alles sein, das ein Konzept von Datei und Verzeichnis hat, von einem Archiv bis zu einem FTP-Server. Er definiert, wie typische Dateivorgänge ausgeführt werden, z. B. das Öffnen einer Datei oder das Auflisten eines Verzeichnisses.

Sie können festlegen, wie Dateivorgänge für Ihren Speicher durchgeführt werden, indem Sie eine Klasse implementieren, die von [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) erbt und Implementierungen für ihre abstrakten Methoden bereitstellt.
## **Showcase: Azure Blob Storage**
Das Aspose.GIS-Beispielrepository enthält ein Beispiel für eine voll funktionsfähige Implementierung eines benutzerdefinierten abstrakten Pfads für Azure Blob Storage. Dieses Showcase zeigt, wie man eine Shapefile direkt aus Azure Blob Storage liest. Sie finden es hier: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **Single-file Formate (GeoJSON, KML)**
GIS-Datenformate wie GeoJSON und KML können alle Daten für eine Ebene in einer einzigen Datei speichern. Wenn Sie einen Stream für die Datei erhalten können, können Sie das Implementieren eines benutzerdefinierten abstrakten Pfads überspringen und die Methode [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) verwenden, um einen abstrakten Pfad für den Stream zu instanziieren.
### **Lesen einer Datei aus einem Stream**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **Schreiben einer Datei in einen Stream**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
