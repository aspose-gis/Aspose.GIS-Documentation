---
title: "Licenties"
second_title: Aspose.GIS voor .NET
type: docs
url: /nl/net/licensing/
weight: 50
keywords: c# gis bibliotheek, .net gis bibliotheek
description: Evalueer de C# .NET GIS-bibliotheek of API met enkele beperkingen. Pas een licentie toe met behulp van een Bestand of Stream Object of als een ingesloten bron.
---

## **Evalueer Aspose.GIS voor .NET**
U kunt Aspose.GIS voor .NET gratis downloaden. Voordat u een licentie toepast, werkt de component in evaluatiemodus. Wanneer u een licentie koopt en een paar regels code toevoegt om de licentie toe te passen, worden de evaluatiebeperkingen verwijderd.

{{% alert color="primary" %}} Als u Aspose.GIS wilt testen zonder beperkingen van de evaluatiemodus, kunt u een tijdelijke licentie van 30 dagen aanvragen. Raadpleeg [Een tijdelijke licentie verkrijgen](https://purchase.aspose.com/temporary-license). {{% /alert %}}
### **Beperkingen van de evaluatiemodus**
Wanneer u in de evaluatiemodus werkt (zonder een toegepaste licentie), biedt Aspose.GIS volledige productfunctionaliteit, behalve enkele evaluatiebeperkingen.

1. Niet meer dan **15 documenten** kunnen per uur worden geopend en/of gemaakt
2. Niet meer dan **100 functies** kunnen in elk document worden gebruikt (lezen of schrijven)
3. Niet meer dan **10 000 rastergegevens** kunnen in elk document worden gebruikt (lezen of schrijven).
4. Het maximale toegestane aantal functies in een document voor conversiebewerkingen is **50**

Wanneer u in de gelicentieerde modus werkt, kunt u een onbeperkt aantal documenten en functies verwerken.
## **Een licentie toepassen**
De licentie is een plat XML-bestand dat details bevat zoals de productnaam, het aantal ontwikkelaars waarvoor deze is gelicenseerd, de abonnementsverloopdatum enzovoort. Het bestand is digitaal ondertekend, dus wijzig het bestand niet. Zelfs onbedoelde toevoeging van een extra regeleinde in het bestand maakt het ongeldig.

U moet een licentie instellen voordat u Aspose.GIS gebruikt als u de evaluatiebeperkingen wilt vermijden. Het is slechts één keer per applicatie (of proces) vereist om een licentie in te stellen.
### **Een licentie instellen in Aspose.GIS voor .NET**
In Aspose.GIS kan een licentie worden geladen vanuit een bestand, stream of ingesloten bron. Aspose.GIS probeert de licentie op de volgende locaties te vinden:

- Expliciet pad
- De map die Aspose.GIS.dll bevat
- De map die de assembly bevat die Aspose.GIS.dll heeft aangeroepen
- De map die de entry assembly (uw .exe) bevat
- Een ingesloten bron in de assembly die Aspose.GIS.dll heeft aangeroepen. Er zijn twee veelvoorkomende methoden om de licentie in te stellen, die hieronder worden besproken:
### **Licentie toepassen met behulp van Bestand of Stream Object**
De gemakkelijkste manier om een licentie in te stellen, is door het licentiebestand in dezelfde map als Aspose.GIS.dll te plaatsen en alleen de bestandsnaam zonder het pad op te geven.

{{< highlight java >}}

 // Instantieer een instantie van licentie en stel het licentiebestand in via het pad

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // Instantieer een instantie van licentie en stel de licentie in via een stream

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}

Wanneer u de methode SetLicense aanroept, moet de licentienaam hetzelfde zijn als de naam van uw licentiebestand. U kunt bijvoorbeeld de bestandsnaam van de licentie wijzigen in "Aspose.GIS.lic.xml". Vervolgens moet u in uw code de gewijzigde licentienaam (dat wil zeggen Aspose.GIS.lic.xml) gebruiken voor de methode SetLicense.

## **Licentiebestand opnemen als ingesloten bron**
Een andere nette manier om de licentie met uw applicatie te verpakken en ervoor te zorgen dat deze niet verloren gaat, is door deze als een ingesloten bron in een van de assemblies op te nemen die de dll van de component aanroept (inbegrepen in Aspose.GIS). Om het licentiebestand als een ingesloten bron op te nemen, voert u de volgende stappen uit:

- Neem in Visual Studio het licentiebestand (.lic) op in het project met behulp van het menu Bestand | Item bestaand toevoegen...
- Selecteer het bestand in Solution Explorer en stel Build Action in op Embedded Resource in het venster Eigenschappen
- Om toegang te krijgen tot de licentie die is ingesloten in de assembly (als ingesloten bron), hoeft u geen GetExecutingAssembly en GetManifestResourceStream methoden van de klasse System.Reflection.Assembly van Microsoft .NET Framework aan te roepen. Alles wat nodig is, is om het licentiebestand als een ingesloten bron toe te voegen aan uw project en de naam van het licentiebestand door te geven aan de methode License.SetLicense. De License-klasse vindt automatisch het licentiebestand in de ingesloten bronnen.

Bekijk het onderstaande voorbeeld om dit methoden voor het instellen van een licentie (ingesloten) in uw applicaties te begrijpen.

{{< highlight java >}}

 // Instantieer de klasse Licentie

Aspose.Gis.License license = new Aspose.Gis.License();

// Geef alleen de naam van het licentiebestand door dat is ingesloten in de assembly

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **Metered Key toepassen**
[Aspose.Gis voor .NET API](/gis/net/) staat ontwikkelaars toe om een gemeten sleutel toe te passen. Het is een nieuw licentiemechanisme. Het nieuwe licentiemechanisme wordt samen met de bestaande licentiemethode gebruikt. Klanten die op basis van het gebruik van de API-functies gefactureerd willen worden, kunnen de gemeten licentie gebruiken. Raadpleeg voor meer informatie de sectie [Veelgestelde vragen over gemeten licenties](https://purchase.aspose.com/faqs/licensing/metered).

Er is een nieuwe klasse **Metered** geïntroduceerd om een gemeten sleutel toe te passen. Hieronder volgt voorbeeldcode die laat zien hoe u een openbare en private gemeten sleutel instelt.

**[C#]**

{{< highlight csharp >}}

 // stel de gemeten publieke en private sleutels in
 
Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();
 
// Toegang tot de setMeteredKey-eigenschap en geef openbare en private sleutels door als parameters
 
metered.SetMeteredKey("*****", "*****");
 
// DOE VERWERKING
 
// haal het verbruikte hoeveelheid gegevens op
 
decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();
 
// Geef informatie weer
 
Console.WriteLine("Verbruikt bedrag: " + amount.ToString());

{{< /highlight >}}
