---
title: "Akışlar ve Uzak Depolama"
type: docs
url: /tr/net/streams-and-remote-storage/
weight: 70
---

## **Çok Dosyalı Formatlarla Çalışma**
Bazı CBS veri formatları içeriği birden fazla dosyaya böler. Örneğin, bir şekil dosyasının en az üç dosyası olmalıdır: *.shp, *.shx ve *.dbf. Bu formatlar, tüm dosyaların belirli bir dosya adı kalıbıyla birlikte belirli bir dizin yapısında depolanmasını gerektirir.

Aynı zamanda, dosyalar uzak bir sunucuda veya yalnızca akışlar aracılığıyla erişilebilen başka bir konumda saklanabilir. Akışlar, dosya adları ve dizin yapısı hakkında bilgi içermez ve bu da dosya formatı sürücülerinin verileri nasıl işleyeceğini belirlemesini imkansız hale getirir. Aspose.GIS bunu soyut yollar mekanizması sağlayarak çözer.

Soyut yol, bir dosya (veya dizin) için bazı dosya sistemi benzeri depolama alanındaki yolu temsil eder. Depolama alanı, arşivden FTP sunucusuna kadar dosya ve dizin kavramına sahip olan herhangi bir şey olabilir. Tipik dosya işlemleri, örneğin bir dosyayı açma veya bir dizini listeleme gibi işlemlerin nasıl gerçekleştirileceğini tanımlar.

Depolamanız için dosya işlemlerinin nasıl gerçekleştirileceğini belirtmek için [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) öğesinden türetilen bir sınıf uygulayarak ve soyut yöntemleri için uygulamalar sağlayarak tanımlarsınız.
## **Örnek: Azure Blob Depolama**
Aspose.GIS Örnekleri deposu, Azure Blob Depolama için özel bir soyut yolun tamamen işlevsel bir uygulamasını içeren bir örnek içerir. Bu gösteri, bir şekil dosyasını doğrudan Azure Blob Depolamadan nasıl okuyacağınızı gösterir. Bunu burada bulabilirsiniz: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **Tek dosyalı formatlar (GeoJSON, KML)**
GeoJSON ve KML gibi CBS veri formatları, bir katman için tüm verileri tek bir dosyada saklayabilir. Dosya için bir akış elde edebiliyorsanız, özel bir soyut yol uygulamayı atlayabilir ve [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) yöntemini kullanarak akış için bir soyut yol örneği oluşturabilirsiniz.
### **Akıştan dosya oku**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **Akışa dosya yaz**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
