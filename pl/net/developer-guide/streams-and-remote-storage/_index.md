---
title: "Strumienie i Zdalne Przechowywanie"
type: docs
url: /pl/net/streams-and-remote-storage/
weight: 70
---

## **Praca z Formatami Wieloplilkowymi**
Niektóre formaty danych GIS dzielą zawartość na kilka plików. Na przykład plik shapefile musi mieć co najmniej trzy pliki: *.shp, *.shx i *.dbf. Formaty te wymagają przechowywania wszystkich plików w określonej strukturze katalogów z predefiniowanym wzorcem nazw plików.

Jednocześnie pliki mogą być przechowywane na zdalnym serwerze lub w innej lokalizacji dostępnej tylko za pośrednictwem strumieni. Strumienie nie zawierają informacji o nazwach plików i strukturze katalogów, co uniemożliwia sterownikom formatu plików określenie sposobu przetwarzania danych. Aspose.GIS rozwiązuje to, zapewniając mechanizm abstrakcyjnych ścieżek.

Abstrakcyjna ścieżka reprezentuje ścieżkę do pliku (lub katalogu) w pewnego rodzaju przestrzeni przechowywania podobnej do systemu plików. Przechowywanie może być czymkolwiek, co ma koncepcję pliku i katalogu, od archiwum po serwer FTP. Definiuje sposób wykonywania typowych operacji na plikach, takich jak otwieranie pliku lub wyświetlanie listy zawartości katalogu.

Możesz określić sposób wykonywania operacji na plikach dla swojego przechowywania, implementując klasę dziedziczącą z [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) i dostarczając implementacje jego metod abstrakcyjnych.
## **Przykład: Azure Blob Storage**
Repozytorium Aspose.GIS Examples zawiera przykład w pełni funkcjonalnej implementacji niestandardowej ścieżki abstrakcyjnej dla Azure Blob Storage. Ten pokaz demonstruje, jak odczytać plik shapefile bezpośrednio z Azure Blob Storage. Możesz go znaleźć tutaj: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **Formaty jednoplikowe (GeoJSON, KML)**
Formaty danych GIS takie jak GeoJSON i KML mogą przechowywać wszystkie dane dla warstwy w jednym pliku. Jeśli możesz uzyskać strumień do pliku, możesz pominąć implementację niestandardowej ścieżki abstrakcyjnej i użyć metody [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) aby utworzyć instancję ścieżki abstrakcyjnej dla strumienia.
### **Odczyt pliku ze strumienia**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **Zapis pliku do strumienia**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
