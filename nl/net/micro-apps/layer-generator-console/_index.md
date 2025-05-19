---
title: "Laaggenerator Console Applicatie"
type: docs
url: /nl/net/layer-generator-console
weight: 50
---

## Samenvatting

Deze console applicatie is ontworpen om geometrische objecten van verschillende types te genereren en op te slaan in het gekozen formaat. Hiermee kunt u punten, polygonen en polylijnen maken, het aantal te genereren objecten specificeren en het uitvoerformaat voor opslag kiezen.

## Gebruik

Commandosyntaxis:

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

Argumenten:

```
-t, --type: Geometrie type. Een van de volgende: Punt, Poligoon, Polyline.

-c, --count: Vereist. Aantal objecten om te genereren. Bijvoorbeeld: 15.

-f, --fileName: Vereist. Bestandsnaam voor opslag. Specificeer de bestandsnaam en extensie. Bijvoorbeeld: test.json.

-o, --outputFormat: Uitvoerformaat. Zie de ondersteunde bestandsformaten hier.

--help: Toon hulp informatie voor het commando.

--version: Toon de applicatie versie informatie.
```

Een voorbeeldcommando om 15 willekeurige punten te maken en op te slaan in een bestand met het formaat "test.json":

```
app.exe -t Point -c 15 -f test.json -o json
```

## Installatie en Licenties

Als u de applicatie wilt gebruiken, moet u het archief downloaden en uitpakken. Volg de onderstaande link.

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

Hoewel Aspose.GIS Layer Generator Console Applicatie gratis is, wordt Aspose.GIS .NET op de gebruikelijke manier gelicenseerd, dus u kunt uw licentie via de applicatie hergebruiken of de applicatie evalueren met behulp van Aspose.GIS .NET in trial mode of een tijdelijke licentie aanvragen.

## Conclusie

De Geometric Objects Generator is een handige console applicatie die u helpt bij het maken van voorbeelden van geometrie van verschillende types en deze op te slaan in het gewenste formaat. Het is een nuttig hulpmiddel voor het werken met geodata en het ontwikkelen van geografische informatiesystemen.
