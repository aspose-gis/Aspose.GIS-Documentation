---
title: "Lisanslama"
second_title: Aspose.GIS for .NET
type: docs
url: /tr/net/licensing/
weight: 50
keywords: c# gis kütüphanesi, .net gis kütüphanesi
description: C# .NET GIS kütüphanesini veya API'sini bazı sınırlamalarla değerlendirin. Lisansı Dosya veya Akış Nesnesi olarak veya Gömülü Kaynak olarak uygulayın.
---

## **Aspose.GIS for .NET'i Değerlendirme**

Aspose.GIS for .NET'i ücretsiz olarak indirebilirsiniz. Bir lisans uygulamadan önce, bileşen değerlendirme modunda çalışır. Lisans satın aldığınızda ve lisansı uygulamak için birkaç satır kod eklediğinizde, değerlendirme sınırlamaları kaldırılır.

{{% alert color="primary" %}} Aspose.GIS'i değerlendirme modu sınırlamaları olmadan test etmek istiyorsanız, 30 günlük Geçici Lisans talep edebilirsiniz. Lütfen [Geçici Lisans Al](https://purchase.aspose.com/temporary-license) bölümüne bakın. {{% /alert %}} 
### **Değerlendirme Modu Sınırlamaları**

Lisans uygulanmadan (değerlendirme modunda) çalıştırıldığında, Aspose.GIS bazı değerlendirme sınırlamaları dışında tam ürün işlevselliği sağlar.

1. Saatte en fazla **15 belge** açılabilir ve/veya oluşturulabilir
2. Her belgede (okuma veya yazma) en fazla **100 özellik** erişilebilir
3. Her belgede (okuma veya yazma) en fazla **10 000 raster veri** erişilebilir.
4. Dönüşüm işlemleri için bir belgedeki izin verilen maksimum özellik sayısı **50**'dir

Lisanslı modda çalıştırıldığında, sınırsız sayıda belge ve özelliği işleyebilirsiniz.
## **Lisans Uygulama**

Lisans, ürün adını, lisanslandığı geliştirici sayısını, abonelik sona erme tarihini vb. ayrıntıları içeren düz bir metin XML dosyasıdır. Dosya dijital olarak imzalanmıştır, bu nedenle dosyayı değiştirmeyin. Hatta dosyaya yanlışlıkla eklenen fazladan bir satır bile geçersiz kılacaktır.

Aspose.GIS'in değerlendirme sınırlamalarından kaçınmak istiyorsanız, Aspose.GIS kullanmadan önce bir lisans ayarlamanız gerekir. Lisansı yalnızca uygulama (veya işlem) başına bir kez ayarlamak yeterlidir.
### **Aspose.GIS for .NET'te Lisans Ayarlama**

Aspose.GIS'de lisans bir dosyadan, akıştan veya gömülü kaynaktan yüklenebilir. Aspose.GIS, lisansı aşağıdaki konumlarda aramaya çalışır:

- Açık yol
- Aspose.GIS.dll içeren klasör
- Aspose.GIS.dll'i çağıran derlemeyi içeren klasör
- Giriş derlemesini (exe'niz) içeren klasör
- Aspose.GIS.dll'i çağıran derlemeye gömülü bir kaynak. Lisansı ayarlamanın iki yaygın yöntemi aşağıda tartışılmıştır:
### **Dosya veya Akış Nesnesi kullanarak Lisans Uygulama**

Lisansı ayarlamanın en kolay yolu, lisans dosyasını Aspose.GIS.dll ile aynı klasöre koymak ve dosyanın yolunu belirtmeden yalnızca dosya adını belirtmektir.

{{< highlight java >}}

 // Lisans örneği oluşturun ve lisans dosyasının yolunu kullanarak ayarlayın

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // Lisans örneği oluşturun ve lisansı bir akış aracılığıyla ayarlayın

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}

SetLicense yöntemini çağırdığınızda, lisans adı lisans dosyanızın adıyla aynı olmalıdır. Örneğin, lisans dosyasının adını "Aspose.GIS.lic.xml" olarak değiştirebilirsiniz. Daha sonra kodunuzda SetLicense yöntemi için değiştirilmiş lisans adını (yani Aspose.GIS.lic.xml) kullanmalısınız.

## **Lisans Dosyasını Gömülü Kaynak Olarak Dahil Etme**

Lisansı uygulamanızla paketlemenin ve kaybolmamasını sağlamanın başka bir yolu da onu bileşenin DLL'sine (Aspose.GIS'e dahil edilen) çağrı yapan derlemelerden birine gömülü kaynak olarak dahil etmektir. Lisans dosyasını gömülü kaynak olarak dahil etmek için aşağıdaki adımları izleyin:

- Visual Studio'da lisans (.lic) dosyasını Menü | Mevcut Öğeyi Ekle... kullanarak projeye ekleyin
- Çözüm Gezgini'nde dosyayı seçin ve Özellikler penceresinde Derleme Eylemini Gömülü Kaynak olarak ayarlayın
- Microsoft .NET Framework'ün System.Reflection.Assembly sınıfının GetExecutingAssembly ve GetManifestResourceStream yöntemlerini çağırmanıza gerek yoktur, montaja gömülmüş lisansı erişmek için. Yapmanız gereken tek şey, lisans dosyasını projenize gömülü kaynak olarak eklemek ve lisans dosyasının adını License.SetLicense yöntemine geçirmektir. Lisans sınıfı otomatik olarak lisansı gömülü kaynaklarda bulacaktır.

Bu yöntemin lisansınızı (gömülü) uygulamalarınızda ayarlamasını anlamak için aşağıdaki örneği inceleyin lütfen.

{{< highlight java >}}

 // Lisans sınıfını örnekleyin

Aspose.Gis.License license = new Aspose.Gis.License();

// Montaja gömülmüş lisans dosyasının adını geçirin

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **Ölçülü Anahtar Uygulama**

[Aspose.GIS for .NET API](/gis/net/) geliştiricilerin ölçülü anahtar uygulamasına izin verir. Yeni bir lisanslama mekanizmasıdır. Yeni lisanslama mekanizması mevcut lisanslama yöntemiyle birlikte kullanılacaktır. API özelliklerinin kullanımına göre faturalandırılmak isteyen müşteriler ölçülü lisanslamayı kullanabilirler. Daha fazla ayrıntı için lütfen [Ölçülü Lisanslama SSS](https://purchase.aspose.com/faqs/licensing/metered) bölümüne bakın.

Yeni bir **Metered** sınıfı, ölçülü anahtarı uygulamak için tanıtılmıştır. Ölçülü genel ve özel anahtarın nasıl ayarlanacağını gösteren örnek kod aşağıdadır.

**[C#]**

{{< highlight csharp >}}

 // ölçülü genel ve özel anahtarları ayarlayın

Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();

// setMeteredKey özelliğine erişin ve genel ve özel anahtarları parametre olarak geçirin

metered.SetMeteredKey("*****", "*****");

// İŞLEM YAPIN

// ölçülü veri miktarını alın

decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();

// Bilgileri görüntüleyin

Console.WriteLine("Tüketilen Miktar : " + amount.ToString());


{{< /highlight >}}
