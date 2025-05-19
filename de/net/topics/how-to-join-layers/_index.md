---
title: "So verbinden Sie Layer mithilfe von Geometrie oder Attributen"
type: docs
url: /de/net/how-to-join-layers
weight: 70
---

## Zusammenfassung

In GIS sind Joins ein leistungsstarkes Werkzeug, um Informationen aus verschiedenen Layern basierend auf einem gemeinsamen Attribut oder einer räumlichen Beziehung zu kombinieren. Mit Joins können Sie Attributdaten von einem Layer (dem Quelllayer) mit einem anderen Layer (dem Ziellayer) mithilfe eines gemeinsamen Feldes oder eines räumlichen Standorts zusammenführen. Der erste ist die Datenverknüpfung nach Schlüssel (Attribut in der Tabelle). Mithilfe eines gemeinsamen Feldes, wie z. B. eines eindeutigen Schlüssels, können Sie Datensätze in einer Tabelle mit Datensätzen in einer anderen Tabelle verknüpfen. Der zweite Ansatz ist die Datenverknüpfung nach Standort (räumlich). Wir unterstützen beide Ansätze und bieten Ihnen die Möglichkeit, sie je nach Ihren Bedürfnissen zu nutzen.

Nehmen wir an, Sie haben Daten erhalten, die den prozentualen Bevölkerungsänderungen für verschiedene Bezirke beschreiben, und möchten auf dieser Grundlage mehrere Karten des Bevölkerungswachstums erstellen. Während Ihre Bevölkerungsdaten in einer Tabelle in Ihrer Datenbank gespeichert sind und ein gemeinsames Feld mit Ihrem Layer teilen, können Sie diese Daten Ihren geografischen Objekten zuordnen und zusätzliche Felder zur Kennzeichnung, Kategorisierung, Abfrage oder Analyse von Layeroobjekten nutzen.

In der Regel führen Sie Datenjoins basierend auf einem Feldwert durch, der in beiden Tabellen vorhanden ist. Die Feldnamen müssen nicht unbedingt übereinstimmen, aber die Datentypen sollten gleich sein – Zahlen mit Zahlen, Zeichenketten mit Zeichenketten usw. Sie können den Datenjoin mithilfe des Geoverarbeitungswerkzeugs "Join hinzufügen" ausführen. Beim Verknüpfen von Attributen werden die verknüpften Felder dynamisch zur vorhandenen Tabelle hinzugefügt. Feld Eigenschaften wie Aliase, Sichtbarkeit und Zahlenformatierung bleiben beim Hinzufügen oder Entfernen des Joins erhalten.

## Möglichkeiten zum Joinen nach Schlüsselfeld

- Dieser Ansatz ermöglicht es Ihnen, **Datensätze aus verschiedenen Tabellen** basierend auf einem gemeinsamen Schlüsselfeld zu verknüpfen. Sie können das Schlüsselfeld angeben, das für den Vergleich verwendet werden soll, um die Beziehung zwischen Datensätzen herzustellen. Dies ist besonders nützlich, wenn Sie Daten anhand eines Identifikators oder eines anderen eindeutigen Attributs zusammenführen müssen.

Festlegen der Methode zum Vergleichen von Daten basierend auf dem Schlüsselfeld:

- Sie können **verschiedene Vergleichsmethoden** für das Schlüsselfeld beim Zusammenführen von Daten definieren. Beispielsweise können Sie einen exakten Übereinstimmungstyp wählen, anhand eines Musters vergleichen oder innerhalb eines Wertebereichs liegen. Dies ermöglicht eine präzisere Bestimmung der Beziehungen zwischen Datensätzen und gibt Ihnen die Kontrolle über den Datenzusammenführungsprozess.

Festlegen einer Liste von Attributnamen, die zusammengeführt werden sollen:

- Beim Zusammenführen von Daten können Sie **bestimmte Attribute** angeben, die zusammengeführt werden sollen. Dadurch können Sie nur die erforderlichen Attribute zum Zusammenführen auswählen und die Struktur der resultierenden Tabelle verwalten.

## Möglichkeiten zum Joinen mithilfe von Geometrie

- Dieser Ansatz ermöglicht es Ihnen, Daten basierend auf ihrem **räumlichen Standort** zu verknüpfen. Sie können einen Suchradius definieren, innerhalb dessen nach den nächstgelegenen geometrischen Objekten gesucht wird, um sie zusammenzuführen. Dies ist nützlich, wenn Sie Daten anhand ihrer geografischen Position verknüpfen müssen.

Steuerung des Suchradius zum Finden der nächstgelegenen geometrischen Objekte:

- Sie können **den Suchradius** beim Zusammenführen von Daten basierend auf dem Standort steuern. Durch Angabe eines Radiuswertes bestimmen Sie den Abstand, innerhalb dessen nach den nächstgelegenen Objekten gesucht wird, um sie zusammenzuführen. Dies gibt Ihnen die Kontrolle darüber, welche Objekte am Datenzusammenführungsprozess basierend auf ihrer räumlichen Beziehung teilnehmen.

## Demoprojekt

Um die Funktionalität unserer Bibliothek besser zu verstehen, betrachten wir [ein Beispiel für ihre Verwendung](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Layers.Join). Dieser Code veranschaulicht, wie Vektorlayer nach Attributen oder Geometrie zusammengeführt werden können.

Der bereitgestellte Code besteht aus zwei Methoden, JoinByIndex() und JoinByCoords(), die Datenjoin-Operationen mithilfe einer LayerConstructor-Klasse demonstrieren.

In der Methode JoinByIndex():

- Listen von Geometrien mit zugehörigen Attributen werden erstellt.

- Ein LayerConstructor-Objekt wird initialisiert.

- Die Methode erstellt einen Vektorlayer und einen Geometrielayer unter Verwendung der bereitgestellten Geometrien.

- Der Geometrielayer wird anhand eines eindeutigen Identifikators ("Id") mithilfe der Methode JoinLayersById() zusammengeführt.

- Der resultierende zusammengeführte Vektorlayer wird zurückgegeben.

In der Methode JoinByCoords():

- Listen von Geometrien mit zugehörigen Attributen werden erstellt.

- Ein LayerConstructor-Objekt wird initialisiert.

- Geometrielayer werden unter Verwendung der bereitgestellten Geometrien erstellt.

- Die Geometrielayer werden anhand übereinstimmender Koordinaten mithilfe der Methode JoinLayersByCoords() zusammengeführt.

- Der resultierende zusammengeführte Vektorlayer wird zurückgegeben.

Zusammenfassend zeigen diese Methoden zwei verschiedene Ansätze zum Verknüpfen von Daten: einen basierend auf einem eindeutigen Identifikator und den anderen basierend auf übereinstimmenden Koordinaten. Die LayerConstructor-Klasse erleichtert diese Datenjoin-Operationen.

## Join-Optionen für Index

Die Klasse JoinOptions bietet eine Reihe von Optionen zum Konfigurieren des Layernjoins. Tauchen wir tiefer in jede Option ein:

- **JoinAttributeName**: Mit dieser Option können Sie den Attributnamen aus dem zusammengeführten Layer angeben, dessen Wert in der Bedingungsvergleichung verwendet wird. Dies stellt die Verbindung zwischen den beiden Layern basierend auf diesem Attribut her.

- **TargetAttributeName**: Mit dieser Option können Sie den Attributnamen aus dem Hauptlayer angeben, der mit dem Attribut aus dem zusammengeführten Layer verglichen werden soll. Dies hilft bei der Bestimmung der übereinstimmenden Features zwischen den Layern.

- **JoinAttributeNames**: Mit dieser Option können Sie eine Liste von Attributnamen angeben, die Sie verknüpfen möchten. Wenn diese Liste leer oder auf null gesetzt ist, werden alle Attribute aus dem zusammengeführten Layer in die Join-Operation einbezogen. Indem Sie jedoch bestimmte Attributnamen auswählen, können Sie die Attribute steuern, die zusammengeführt werden, was für die Optimierung der Speichernutzung und der Verarbeitungszeit nützlich sein kann.

- **ConditionComparer**: Mit dieser Option können Sie eine benutzerdefinierte Logik zum Vergleichen von Attributwerten zwischen den Features der beiden Layer definieren. Standardmäßig wird der EqualityComparer.Default-Vergleicher verwendet, der auf Gleichheit prüft. Sie können jedoch Ihren eigenen benutzerdefinierten Vergleicher bereitstellen, der IEqualityComparer implementiert, für spezialisiertere Vergleichsanforderungen.

- **JoinedAttributesPrefix**: Mit dieser Option können Sie ein Präfix für die Attributnamen des zusammengeführten Layers angeben. Der Standardwert ist "joined_", was bedeutet, dass den zusammengeführten Attributen im resultierenden zusammengeführten Layer das Präfix "joined_" vorangestellt wird. Dieses Präfix hilft dabei, die zusammengeführten Attribute von den ursprünglichen Attributen des Hauptlayers zu unterscheiden.

Die Klasse JoinOptions bietet Flexibilität und Kontrolle über verschiedene Aspekte des Layernjoin-Prozesses. Sie können die zu verknüpfenden Attribute angeben, die Vergleichslogik anpassen und ein Präfix für die resultierenden zusammengeführten Attribute definieren. Diese Optionen ermöglichen es Ihnen, die Join-Operation an Ihre spezifischen Bedürfnisse anzupassen und aussagekräftige Erkenntnisse aus den zusammengeführten Layern zu gewinnen.

## Join-Optionen für Geometrie

Die Klasse **JoinByGeometryOptions** stellt Optionen zum Verknüpfen von Layern basierend auf der Geometrie dar. Lassen Sie uns die Funktionalität jeder Option untersuchen:

- **Radius**: Diese Option gibt den Radius an, innerhalb dessen nach der zusammengeführten Geometrie gesucht wird. Dies bestimmt die Nähe, innerhalb derer Features aus dem Hauptlayer mit Features aus dem zusammengeführten Layer basierend auf ihrer räumlichen Beziehung abgeglichen werden.

- **ConditionComparer**: Mit dieser Option können Sie eine benutzerdefinierte Logik zum Vergleichen von Attributwerten aus den Features der beiden Layer definieren. Standardmäßig wird EqualityComparer.Default verwendet, das auf Gleichheit prüft. Sie können jedoch Ihren eigenen benutzerdefinierten Vergleicher bereitstellen, der IEqualityComparer für spezifischere Vergleichsanforderungen implementiert.

- **JoinedAttributesPrefix**: Mit dieser Option können Sie ein Präfix für die Attributnamen des zusammengeführten Layers angeben. Der Standardwert ist "joined_", was bedeutet, dass den zusammengeführten Attributen im resultierenden zusammengeführten Layer das Präfix "joined_" vorangestellt wird. Dieses Präfix hilft dabei, die zusammengeführten Attribute von den ursprünglichen Attributen des Hauptlayers zu unterscheiden.

Die Klasse JoinByGeometryOptions bietet die Möglichkeit, den Prozess zum Verknüpfen von Layern basierend auf ihrer räumlichen Beziehung anzupassen. Indem Sie einen Suchradius angeben, können Sie steuern, innerhalb welcher Geometrien abgeglichen werden. Dies ermöglicht eine Feinabstimmung der Join-Operation basierend auf der gewünschten Nähe zwischen Features. Die Option zur Bereitstellung eines benutzerdefinierten Vergleichers gibt Ihnen Flexibilität beim Vergleichen von Attributwerten, und die Option zum Voranstellen zusammengeführter Attribute hilft dabei, sie im resultierenden zusammengeführten Layer zu unterscheiden.

Mit diesen Optionen können Sie räumlich bewusst Daten zusammenführen und Erkenntnisse aus den zusammengeführten Layern gewinnen, die auf ihrer räumlichen Nähe und ihren Attributwerten basieren.

## Zusammenfassung

Der Datenjoin-Mechanismus in GIS ermöglicht das Kombinieren geometrischer Objekte mit ihren jeweiligen Attributen aus verschiedenen Layern. Dies bietet die Möglichkeit, Informationen basierend auf räumlichen und attributiven Beziehungen innerhalb der Daten zu analysieren und zu extrahieren. Die verfügbaren Optionen ermöglichen eine Anpassung des Join-Prozesses an spezifische Anforderungen und Analysebedürfnisse in GIS-Daten.

Die Datenverknüpfung erleichtert verschiedene Aufgaben, darunter:

- Finden von Objekten, die bestimmte räumliche Kriterien erfüllen, z. B. das Identifizieren aller Gebäude innerhalb eines Radius von 500 Metern um einen bestimmten Punkt.

- Kombinieren geografischer Daten, um eine umfassendere und informativere Übersicht über eine Situation zu erhalten.

- Analysieren der Attributwerte von Objekten basierend auf spezifischen räumlichen Bedingungen, um Trends und Muster zu identifizieren.

Die Datenjoin-Optionen ermöglichen die präzise Konfiguration des Objektabgleichsprozesses. Zu diesen Optionen gehören das Auswählen der zu verknüpfenden Attribute, das Definieren einer benutzerdefinierten Logik zum Vergleichen von Attributwerten und das Hinzufügen eines Präfixes zu den Attributnamen der zusammengeführten Daten. Diese Optionen bieten Flexibilität und Anpassungsfähigkeit an den Join-Prozess und berücksichtigen die spezifischen Anforderungen und Ziele der Datenanalyse in GIS.

Der Datenjoin-Mechanismus spielt eine wichtige Rolle bei der Integration und Analyse geografischer Daten und führt zu einem umfassenderen Verständnis der räumlichen und attributiven Natur der untersuchten Objekte.