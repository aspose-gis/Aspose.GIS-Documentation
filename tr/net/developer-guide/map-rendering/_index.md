---
title: Harita Renderlamayı Görüntü SVG, PNG, JPG'ye Dönüştürme GIS C# Kütüphanesi
linktitle: "Harita Renderlama"
type: docs
url: /tr/net/map-rendering/
weight: 50
description: GIS C# API ile Shapefile, FileGDB, GeoJSON, KML formatlarından harita renderlayabilir, gelişmiş stil uygulamaları yapabilir ve raster formatlarından harita çizebilirsiniz.
---

## **Harita Renderlama Genel Bakışı**
Aspose.GIS for .NET C# API ile bir Shapefile, FileGDB, GeoJSON, KML veya diğer [desteklenen dosya formatlarından](/gis/net/supported-file-formats/) SVG, PNG, JPEG veya BMP'ye harita renderlayabilirsiniz.

İşte bir shapefile'dan varsayılan ayarlarla SVG'ye harita renderlamanın nasıl yapılacağını gösteren C# kodu:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



İşte sonuç:



![harita renderlama](map_rendering.png)

Koda daha yakından bakalım.

Önce bir [Harita ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map) nesnesi örneklendiriyoruz. Çeşitli kaynaklardan gelen katmanların koleksiyonunu temsil eder ve renderlanabilir. Bir Harita'nın, görüntülenmesi amaçlanan bir boyutu vardır. Burada haritayı 800 piksel genişliğinde ve 400 piksel yüksekliğinde ayarlıyoruz.

Haritanın using ifadesi içine alındığına dikkat edin. Bu gereklidir çünkü harita eklenen tüm kaynakları takip eder ve renderlama tamamlandığında ve Harita nesnesi imha edildiğinde bunları ortadan kaldırır.

Daha sonra bir dosyadan katmanı haritaya ekliyoruz. Her katman, eklendiği sıraya göre önceki katmanın üzerine renderlanır. Vektör katmanlarını nasıl açacağınız hakkında daha fazla ayrıntı için [burada](/gis/net/working-with-vector-layers/) bakın.

Son olarak, haritayı bir dosyaya renderlamak için [Harita.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) çağırıyoruz. Sonuç dosyasını kaydetmek istediğiniz yolu ve kullanmak istediğiniz renderlayıcıyı belirtiyoruz. [Renderlayıcılar ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) sınıfı, Aspose.GIS ile birlikte gelen tüm renderlayıcılara referanslar içerir. Örneğin, yukarıdaki örnekte haritayı PNG dosyasına renderlamak için Renderlayıcılar.Png'yi Renderlayıcılar.Svg yerine belirtebilirsiniz.

## **Gelişmiş Stil**
Aspose.GIS API ile istediğiniz görünümü elde etmek için renderlamayı ve özellik stillerini özelleştirebilirsiniz.

![gelişmiş stil](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}

## **Haritaya raster çizme**
Aspose.GIS for .NET ile raster formatlarından harita renderlayabilirsiniz.

### **Varsayılan ayarlarla renderlama**
İşte GeoTIFF'ten varsayılan ayarlarla SVG'ye bir haritanın nasıl renderlanacağına dair bir örnek:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![varsayılan raster](default_raster.png)

### **Eğik rasterları renderlama**
Aspose.GIS ile eğik raster hücreleri olan bir rasterı renderlayabilirsiniz.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![eğik raster](skew_raster.png)

### **Kutup koordinat referansında renderlama**
Aspose.GIS, harita renderleme sürecinde kutup koordinat referanslarını kullanmanıza olanak tanır.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![gnomonik ülkeler](gnomonic_countries.png)
