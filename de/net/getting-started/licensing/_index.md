---
title: "Lizenzierung"
second_title: Aspose.GIS for .NET
type: docs
url: /de/net/licensing/
weight: 50
keywords: c# gis library, .net gis library
description: Evaluieren Sie die C#- .NET-GIS-Bibliothek oder API mit einigen Einschränkungen. Wenden Sie eine Lizenz mithilfe eines Datei- oder Streamobjekts oder als eingebettete Ressource an.
---

## **Evaluieren von Aspose.GIS für .NET**
Sie können Aspose.GIS für .NET kostenlos herunterladen. Bevor Sie eine Lizenz anwenden, funktioniert die Komponente im Evaluierungsmodus. Wenn Sie eine Lizenz erwerben und ein paar Codezeilen hinzufügen, um die Lizenz anzuwenden, werden die Evaluierungseinschränkungen aufgehoben.

{{% alert color="primary" %}} Wenn Sie Aspose.GIS ohne Einschränkungen des Evaluierungsmodus testen möchten, können Sie eine 30-Tage-Testlizenz anfordern. Bitte beachten Sie [Eine temporäre Lizenz erhalten](https://purchase.aspose.com/temporary-license). {{% /alert %}}
### **Einschränkungen des Evaluierungsmodus**
Wenn im Evaluierungsmodus (ohne angewendete Lizenz) ausgeführt wird, bietet Aspose.GIS die vollständige Produktfunktionalität mit Ausnahme einiger Evaluierungseinschränkungen.

1. Nicht mehr als **15 Dokumente** können pro Stunde geöffnet und/oder erstellt werden.
2. Nicht mehr als **100 Features** können in jedem Dokument (lesen oder schreiben) zugegriffen werden.
3. Nicht mehr als **10 000 Rasterdaten** können in jedem Dokument (lesen oder schreiben) zugegriffen werden.
4. Die maximal zulässige Anzahl von Features in einem Dokument für Konvertierungsvorgänge beträgt **50**.

Wenn im lizenzierten Modus ausgeführt wird, können Sie eine unbegrenzte Anzahl von Dokumenten und Features verarbeiten.
## **Anwenden einer Lizenz**
Die Lizenz ist eine Klartext-XML-Datei, die Details wie den Produktnamen, die Anzahl der Entwickler, für die sie lizenziert ist, das Ablaufdatum des Abonnements usw. enthält. Die Datei ist digital signiert, ändern Sie die Datei also nicht. Selbst das unbeabsichtigte Hinzufügen eines zusätzlichen Zeilenumbruchs in die Datei macht diese ungültig.

Sie müssen eine Lizenz festlegen, bevor Sie Aspose.GIS verwenden, um seine Evaluierungseinschränkungen zu vermeiden. Es ist nur erforderlich, eine Lizenz einmal pro Anwendung (oder Prozess) festzulegen.
### **Festlegen einer Lizenz in Aspose.GIS für .NET**
In Aspose.GIS kann die Lizenz aus einer Datei, einem Stream oder einer eingebetteten Ressource geladen werden. Aspose.GIS versucht, die Lizenz an den folgenden Speicherorten zu finden:

- Expliziter Pfad
- Der Ordner, der Aspose.GIS.dll enthält
- Der Ordner, der die Assembly enthält, die Aspose.GIS.dll aufgerufen hat
- Der Ordner, der die Entry Assembly (Ihre .exe) enthält
- Eine eingebettete Ressource in der Assembly, die Aspose.GIS.dll aufgerufen hat. Es gibt zwei gängige Methoden zum Festlegen der Lizenz, die unten erläutert werden:
### **Lizenz mit Datei oder Streamobjekt anwenden**
Der einfachste Weg, eine Lizenz festzulegen, besteht darin, die Lizenzdatei in denselben Ordner wie Aspose.GIS.dll zu legen und nur den Dateinamen ohne Pfad anzugeben.

{{< highlight java >}}

 // Instanziieren Sie eine Instanz der Lizenz und setzen Sie die Lizenzdatei über ihren Pfad
 
Aspose.Gis.License license = new Aspose.Gis.License();
 
license.SetLicense("Aspose.GIS.lic");
 
{{< /highlight >}}

{{< highlight java >}}

 // Instanziieren Sie eine Instanz der Lizenz und setzen Sie die Lizenz über einen Stream
 
Aspose.Gis.License license = new Aspose.Gis.License();
 
license.SetLicense(myStream);
 
{{< /highlight >}}

Wenn Sie die Methode SetLicense aufrufen, sollte der Name der Lizenz mit dem Namen Ihrer Lizenzdatei übereinstimmen. Wenn Sie beispielsweise den Namen der Lizenzdatei in "Aspose.GIS.lic.xml" ändern, sollten Sie im Code den geänderten Lizenznamen (d. h. Aspose.GIS.lic.xml) für die Methode SetLicense verwenden.

## **Lizenzdatei als eingebettete Ressource einschließen**
Eine weitere elegante Möglichkeit, die Lizenz mit Ihrer Anwendung zu verpacken und sicherzustellen, dass sie nicht verloren geht, besteht darin, sie als eingebettete Ressource in eine der Assemblies einzuschließen, die die DLL der Komponente aufrufen (in Aspose.GIS enthalten). Um die Lizenzdatei als eingebettete Ressource einzuschließen, führen Sie die folgenden Schritte aus:

- Fügen Sie die Lizenz (.lic)-Datei in Visual Studio über das Menü Datei | Vorhandenes Element hinzufügen... in Ihr Projekt ein
- Wählen Sie die Datei im Projektmappen-Explorer aus und setzen Sie Buildaktion im Eigenschaftenfenster auf Eingebettete Ressource.
- Um auf die eingebettete Lizenz in der Assembly zuzugreifen (als eingebettete Ressource), ist es nicht erforderlich, die Methoden GetExecutingAssembly und GetManifestResourceStream der Klasse System.Reflection.Assembly des Microsoft .NET Frameworks aufzurufen. Alles, was Sie tun müssen, ist, die Lizenzdatei als eingebettete Ressource zu Ihrem Projekt hinzuzufügen und den Namen der Lizenzdatei an die Methode License.SetLicense zu übergeben. Die License-Klasse findet die Lizenzdatei automatisch in den eingebetteten Ressourcen.

Bitte lesen Sie das folgende Beispiel, um diese Methode zum Festlegen der Lizenz (eingebettet) in Ihren Anwendungen zu verstehen.

{{< highlight java >}}

 // Instanziieren Sie die License-Klasse
 
Aspose.Gis.License license = new Aspose.Gis.License();
 
// Übergeben Sie nur den Namen der Lizenzdatei, die in die Assembly eingebettet ist
 
license.SetLicense("Aspose.GIS.lic");
 
{{< /highlight >}}

## **Metered Key anwenden**
[Aspose.Gis for .NET API](/gis/net/) ermöglicht Entwicklern das Anwenden eines Metered Keys. Es handelt sich um einen neuen Lizenzierungsmechanismus. Der neue Lizenzierungsmechanismus wird zusammen mit der bestehenden Lizenzierungsmethode verwendet. Kunden, die für die Nutzung der API-Funktionen abrechnen möchten, können die metered Lizenzierung nutzen. Weitere Details finden Sie im Abschnitt [FAQ zur Metered Lizenzierung](https://purchase.aspose.com/faqs/licensing/metered).

Eine neue Klasse **Metered** wurde eingeführt, um den Metered Key anzuwenden. Im Folgenden finden Sie ein Beispiel für Code, der zeigt, wie man den öffentlichen und privaten Metered Key festlegt.

**[C#]**

{{< highlight csharp >}}

 // Legen Sie die öffentlichen und privaten Metered Keys fest
 
Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();
 
// Greifen Sie auf die Eigenschaft setMeteredKey zu und übergeben Sie öffentliche und private Keys als Parameter
 
metered.SetMeteredKey("*****", "*****");
 
// VERARBEITUNG DURCHFÜHREN
 
// Menge des verbrauchten Guthabens abrufen
 
decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();
 
// Informationen anzeigen
 
Console.WriteLine("Verbrauchtes Guthaben: " + amount.ToString());
 

{{< /highlight >}}
