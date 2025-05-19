---
title: "Streams en Remote Opslag"
type: docs
url: /nl/net/streams-and-remote-storage/
weight: 70
---

## **Werken met Multi-Bestandsformaten**
Sommige GIS-gegevensformaten splitsen de inhoud in meerdere bestanden. Bijvoorbeeld, een shapefile moet ten minste drie bestanden hebben: *.shp, *.shx en *.dbf. Deze formaten vereisen dat alle bestanden worden opgeslagen in een bepaalde directory structuur met een vooraf gedefinieerd patroon voor bestandsnamen.

Tegelijkertijd kunnen de bestanden op een externe server worden opgeslagen, of op een andere locatie die alleen toegankelijk is via streams. Streams bevatten geen informatie over bestandsnamen en directory structuren, waardoor het onmogelijk wordt voor file format drivers om te bepalen hoe de gegevens moeten worden verwerkt. Aspose.GIS lost dit op door het abstracte pad mechanisme te bieden.

Een abstract pad vertegenwoordigt een pad naar een bestand (of een directory) in een soort filesystem-achtige opslag. De opslag kan alles zijn dat een concept heeft van het bestand en de directory, van een archief tot een FTP-server. Het definieert hoe typische bestandsbewerkingen moeten worden uitgevoerd, zoals het openen van een bestand of het weergeven van een directory.

U kunt specificeren hoe bestandsbewerkingen voor uw opslag moeten worden uitgevoerd door een klasse te implementeren die overerft van [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) en implementaties te bieden voor de abstracte methoden ervan.
## **Showcase: Azure Blob Storage**
Het Aspose.GIS Examples repository bevat een voorbeeld van een volledig functionele implementatie van een aangepast abstract pad voor Azure Blob Storage. Deze showcase laat zien hoe je een shapefile direct vanuit Azure Blob Storage kunt lezen. Je vindt het hier: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **Single-file formaten (GeoJSON, KML)**
GIS-gegevensformaten zoals GeoJSON en KML kunnen alle gegevens voor een laag opslaan in één bestand. Als je een stream voor het bestand kunt verkrijgen, kun je het implementeren van een aangepast abstract pad overslaan en de methode [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) gebruiken om een abstract pad voor de stream te instantieren.
### **Lees een bestand van een stream**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **Schrijf een bestand naar een stream**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
