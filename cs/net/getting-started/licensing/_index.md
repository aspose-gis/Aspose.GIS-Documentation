---
title: "Licencování"
second_title: Aspose.GIS for .NET
type: docs
url: /cs/net/licensing/
weight: 50
keywords: c# gis knihovna, .net gis knihovna
description: Vyhodnoťte C# .NET GIS knihovnu nebo API s určitými omezeními. Aplikujte licenci pomocí souboru nebo Stream objektu nebo jako vložený zdroj.
---

## **Vyhodnocení Aspose.GIS for .NET**
Můžete si zdarma stáhnout Aspose.GIS for .NET. Před aplikací licence komponent funguje v režimu vyhodnocování. Po zakoupení licence a přidání několika řádků kódu pro její aplikaci jsou omezení vyhodnocení odstraněna.

{{% alert color="primary" %}} Pokud chcete testovat Aspose.GIS bez omezení režimu vyhodnocování, můžete požádat o 30denní dočasnou licenci. Přečtěte si [Získání dočasné licence](https://purchase.aspose.com/temporary-license). {{% /alert %}} 
### **Omezení režimu vyhodnocování**
Při spuštění v režimu vyhodnocování (bez aplikované licence) poskytuje Aspose.GIS plnou funkčnost produktu kromě některých omezení vyhodnocení.

1. Lze otevřít a/nebo vytvořit maximálně **15 dokumentů za hodinu**
1. V každém dokumentu lze přistupovat k maximálně **100 prvkům** (čtení nebo zápis)
1. V každém dokumentu lze přistupovat k maximálně **10 000 rastrových dat** (čtení nebo zápis).
1. Maximální povolený počet prvků v dokumentu pro konverzní operace je **50**

Při spuštění v licencovaném režimu můžete zpracovávat neomezený počet dokumentů a prvků.
## **Aplikování licence**
Licence je prostý textový XML soubor, který obsahuje podrobnosti jako název produktu, počet vývojářů, pro které je licencován, datum vypršení předplatného a tak dále. Soubor je digitálně podepsán, proto jej neměňte. I neúmyslné přidání dalšího řádku do souboru ho zneplatní.

Abyste se vyhnuli omezením vyhodnocování, musíte nastavit licenci před použitím Aspose.GIS. Licenci je nutné nastavit pouze jednou pro aplikaci (nebo proces).
### **Nastavení licence v Aspose.GIS for .NET**
V Aspose.GIS lze načíst licenci ze souboru, streamu nebo vloženého zdroje. Aspose.GIS se pokusí najít licenci na následujících místech:

- Explicitní cesta
- Složka obsahující Aspose.GIS.dll
- Složka obsahující sestavení, které volalo Aspose.GIS.dll
- Složka obsahující vstupní sestavu (váš .exe)
- Vložený zdroj v sestavení, které volalo Aspose.GIS.dll. Existují dvě běžné metody nastavení licence, které jsou popsány níže:
### **Aplikace licence pomocí souboru nebo Stream objektu**
Nejjednodušší způsob, jak nastavit licenci, je umístit licenční soubor do stejné složky jako Aspose.GIS.dll a zadat pouze název souboru bez jeho cesty.

{{< highlight java >}}

 // Vytvoření instance licence a nastavení licenčního souboru prostřednictvím jeho cesty

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // Vytvoření instance licence a nastavení licence prostřednictvím streamu

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}

Když voláte metodu SetLicense, název licence by měl být stejný jako název vašeho licenčního souboru. Například můžete změnit název licenčního souboru na "Aspose.GIS.lic.xml". Potom ve svém kódu byste měli použít upravený název licence (tj. Aspose.GIS.lic.xml) pro metodu SetLicense.

## **Zahrnutí licenčního souboru jako vloženého zdroje**
Dalším elegantním způsobem balení licence s vaší aplikací a zajištění jejího neztracení je zahrnout ji jako vložený zdroj do jednoho ze sestavení, které volá knihovnu komponenty (zahrnuté v Aspose.GIS). Chcete-li zahrnout licenční soubor jako vložený zdroj, postupujte podle následujících kroků:

- Ve Visual Studiu zahrňte licenční (.lic) soubor do projektu pomocí nabídky Soubor | Přidat existující položku...
- Vyberte soubor v Průzkumníku řešení a nastavte akci sestavení na Vložený zdroj v okně Vlastnosti
- Pro přístup k licenci vložené do sestavy (jako vloženému zdroji) není třeba volat metody GetExecutingAssembly a GetManifestResourceStream třídy System.Reflection.Assembly .NET Frameworku Microsoftu. Jediné, co je potřeba udělat, je přidat licenční soubor jako vložený zdroj do projektu a předat název licenčního souboru metodě License.SetLicense. Třída Licence automaticky najde licenční soubor ve vložených zdrojích.

Prohlédněte si níže uvedený příklad, abyste pochopili tuto metodu nastavení licence (vložené) ve svých aplikacích.

{{< highlight java >}}

 // Vytvoření instance třídy Licence

Aspose.Gis.License license = new Aspose.Gis.License();

// Předání pouze názvu licenčního souboru vloženého do sestavy

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **Aplikování měřeného klíče**
[API Aspose.GIS for .NET](/gis/net/) umožňuje vývojářům aplikovat měřený klíč. Jedná se o nový licenční mechanismus. Nový licenční mechanismus bude používán spolu s existující metodou licencování. Zákazníci, kteří chtějí být fakturováni na základě využití funkcí API, mohou použít měřené licencování. Podrobnosti naleznete v části [FAQ k měřenému licencování](https://purchase.aspose.com/faqs/licensing/metered).

Byla zavedena nová třída **Metered** pro aplikaci měřeného klíče. Následuje ukázkový kód, který demonstruje, jak nastavit veřejný a soukromý měřený klíč.

**[C#]**

{{< highlight csharp >}}

 // Nastavení měřených veřejných a soukromých klíčů
 
Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();
 
// Přístup k vlastnosti setMeteredKey a předání veřejných a soukromých klíčů jako parametrů
 
metered.SetMeteredKey("*****", "*****");
 
// PROVEDENÍ ZPRACOVÁNÍ
 
// získání množství spotřebovaných měřených dat
 
decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();
 
// Zobrazení informací
 
Console.WriteLine("Spotřebované množství: " + amount.ToString());

{{< /highlight >}}
