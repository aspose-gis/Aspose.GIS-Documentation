---
title: "Potoky a vzdálené úložiště"
type: docs
url: /cs/net/streams-and-remote-storage/
weight: 70
---

## **Práce s více souborovými formáty**
Některé GIS datové formáty rozdělují obsah do několika souborů. Například shapefile musí mít alespoň tři soubory: *.shp, *.shx a *.dbf. Tyto formáty vyžadují, aby všechny soubory byly uloženy v určité adresářové struktuře s předdefinovaným vzorem pro názvy souborů.

Současně mohou být soubory uloženy na vzdáleném serveru nebo jiném místě přístupném pouze prostřednictvím toků (streams). Toky postrádají informace o názvech souborů a adresářové struktuře, což znemožňuje ovladačům formátů souborů určit, jak zpracovat data. Aspose.GIS to řeší poskytováním mechanismu abstraktních cest.

Abstraktní cesta představuje cestu k souboru (nebo adresáři) v nějakém úložišti podobném systému souborů. Úložiště může být cokoli, co má koncept souboru a adresáře, od archivu po FTP server. Definuje, jak provádět typické operace se soubory, jako je otevření souboru nebo výpis adresáře.

Můžete určit, jak provádět operace se soubory pro vaše úložiště implementací třídy, která dědí [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) a poskytnutím implementací pro její abstraktní metody.
## **Ukázka: Azure Blob Storage**
Repozitář Aspose.GIS Examples obsahuje příklad plně funkční implementace vlastní abstraktní cesty pro Azure Blob Storage. Tato ukázka ukazuje, jak číst shapefile přímo z Azure Blob Storage. Najdete ji zde: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **Formáty jednoho souboru (GeoJSON, KML)**
GIS datové formáty jako GeoJSON a KML mohou ukládat všechna data pro vrstvu do jediného souboru. Pokud můžete získat tok pro soubor, můžete přeskočit implementaci vlastní abstraktní cesty a použít metodu [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) k vytvoření instance abstraktní cesty pro tok.
### **Přečtení souboru z toku**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **Zápis souboru do toku**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
