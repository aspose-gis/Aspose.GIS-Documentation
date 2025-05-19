---
title: "Optimale Padzoeker"
type: docs
url: /nl/optimal-path-finder
weight: 70
---

## Samenvatting

Het zoeken naar het kortste pad op een wegennetwerk is een analyseproces dat tot doel heeft de meest efficiënte manier te bepalen om tussen punten op een kaart te reizen. Dit hulpmiddel kan nuttig zijn bij het creëren van optimale routes met meerdere stops of bij het meten van de afstand en reistijd tussen verschillende locaties. Bij elke oproep kan onze technologie optimale routes vinden voor één of meerdere voertuigen. Het kan bijvoorbeeld bestuurders helpen de optimale routes te vinden voor het bezorgen van goederen of de optimale woon-werk afstand voor verschillende passagiers te bepalen.

## Algoritme Capaciteiten

Onze bibliotheek biedt de mogelijkheid om de meest **optimale route tussen twee punten** op een kaart te bouwen. Het heeft de volgende belangrijkste functies:

1. Zoeken naar het optimale pad op de kaart, rekening houdend met paden en obstakels: We houden niet alleen rekening met wegen, maar ook met off-road paden zoals routes, voetgangerspaden en obstakels die de keuze van het optimale pad kunnen beïnvloeden.

2. Zoeken naar het optimale pad uitsluitend op wegen: Als je een route uitsluitend op wegen wilt vinden, bieden we deze mogelijkheid. Dit is bijvoorbeeld nuttig voor voertuigen die beperkt zijn tot reizen op wegen.

3. Instellen van verschillende snelheden voor wegen: We hebben de mogelijkheid om verschillende snelheden toe te wijzen aan verschillende wegen. Hogere snelheden kunnen bijvoorbeeld worden ingesteld voor belangrijke snelwegen en lagere snelheden voor smalle rijstroken.

4. Instellen van rechthoekige obstakels: Je kunt rechthoekige obstakels op de kaart definiëren die moeten worden meegenomen bij het bouwen van het optimale pad. Dit is nuttig wanneer er bekende obstakels zijn, zoals gebouwen of meren (hun benadering).

5. Beperken van de zoekradius voor wegen: Je kunt de zoekradius voor wegen beperken om de zoektijd te verkorten en je alleen op een specifiek gebied te concentreren.

6. Prestatie- en nauwkeurigheidscontrole: We bieden de mogelijkheid om de prestaties en nauwkeurigheid van het algoritme te regelen. Je kunt het afstemmen om de gewenste balans tussen zoeksnelheid en routeconstructienauwkeurigheid te bereiken.

Vervolgens zullen we een gedetailleerdere beschrijving geven van elk van deze functies en voorbeelden bekijken van hun toepassingen.

## Benadering van Oplossing

Hoewel padvinding een niet-triviale taak is, zijn er verschillende goede en betrouwbare algoritmen die worden erkend in de ontwikkelgemeenschap.

In onze implementatie hebben we een gemodificeerd Lee's algoritme gebruikt. We hebben een raster van cellen op het vlak. Vanaf het startpunt verspreidt zich een golf in 8 richtingen (inclusief diagonalen) naar naburige cellen, waarbij de tijd wordt berekend die nodig is om elk ervan te bereiken. Een naburige cel kan een obstakel of een weg bevatten. Wegen kunnen verschillende snelheids coëfficiënten hebben. Zo "markeren" we ons raster met de tijd die het kost om elke cel vanuit de startcel binnen een bepaalde straal of tot het bereiken van het eindpunt te bereiken. Als we het eindpunt bereiken, bouwen we een omgekeerd pad met behulp van ons raster.

Om de optimale route op het wegennetwerk te bepalen, moeten verschillende stappen worden genomen. Eerst moet je de wegen definiëren en de snelheid van beweging op elk ervan specificeren. Je moet ook rekening houden met de aanwezigheid van kunstmatige en natuurlijke obstakels die het pad kunnen beïnvloeden. Daarna moet je de start- en eindpunten van de zoekopdracht specificeren. Zodra deze voorbereidende stappen zijn voltooid, kun je overgaan tot de daadwerkelijke padvinding. Het resultaat is een pad dat bijvoorbeeld wordt weergegeven als een lijst met coördinaten van punten.

Het is belangrijk op te merken dat het optimale pad kan afhangen van de gekozen vervoerswijze, aangezien de snelheid van beweging en de set obstakels kunnen variëren. Daarom moeten verschillende sets wegen en obstakels worden gebruikt voor elk type transport bij het zoeken naar het optimale pad.

## Demo Project op GitHub

Om de functionaliteit van onze bibliotheek beter te begrijpen, bekijk [een voorbeeld van het gebruik](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths). Deze code illustreert hoe je wegen en obstakels kunt instellen in het padvindingsalgoritme en de optimale route kunt vinden.

Het voorbeeld bestaat uit de volgende stappen:

1. Het maken van een lijst met weg informatie (RoadInfo), die informatie bevat over het wegsegment (Segment) en de snelheid van beweging (Velocity).
2. Snelwegen toevoegen aan de lijst.
3. Langzame ringwegen toevoegen aan de lijst.
4. Een way layer generator (WayLayerGenerator) maken en wegen toevoegen aan de generator.
5. Zoeken naar meerdere paden vanaf het startpunt (startPoint) naar de eindpunten (goalPoint01, goalPoint02, goalPoint03) met behulp van de gespecificeerde radius (radius).
6. Een roads layer (roadsLayer) voorbereiden om op de kaart weer te geven en wegobjecten toevoegen.
7. Een way layer (wayLayer) voorbereiden om op de kaart weer te geven en geometrische objecten maken voor elk gevonden pad.
8. [De kaart weergeven](https://docs.aspose.com/gis/net/how-to-draw-geometry/) met behulp van de ShowMap functie, waarbij de kaart wordt opgeslagen op het gespecificeerde pad.

Deze code bouwt en toont wegpaden op de kaart voor gespecificeerde punten met behulp van weg informatie en de way layer generator.

## Zoekopties

Padvinding wordt uitgevoerd met behulp van de **WayLayerGenerator** klasse in de Aspose.Gis.GeoTools.WayAnalyzer namespace.

De WayLayerGenerator klasse heeft de **FindTheWay methode** voor het vinden van het pad van het startpunt naar het doel. Om een instantie van de WayLayerGenerator klasse te maken, geven we WayOptions als parameters door (alle parameters zijn optioneel):

- StartPoint: Het startpunt

- GoalPoint: Het doel punt

- Radius: De zoekradius

- Scale: De schaal van het raster

- IsMoveOnlyRoad: Of er alleen op wegen gezocht moet worden

Het opvallende kenmerk hier is de Scale parameter. Als deze in de constructor wordt gespecificeerd, fixeren we een constante schaal voor latere zoekopdrachten. Als de Scale parameter niet is ingesteld maar StartPoint en GoalPoint zijn ingesteld, berekenen we de schaal als de afstand tussen het start- en eindpunt gedeeld door 100. In alle andere gevallen is de standaardwaarde van Scale 1. Voor ervaren gebruikers is het beter om Scale in te stellen of StartPoint en GoalPoint direct in te stellen om wegen en obstakels het meest efficiënt op het raster weer te geven (vooral als er veel zijn).

Om de FindTheWay methode te gebruiken, moeten we de start- en eindpunten specificeren. We kunnen ook de zoekradius instellen (de afstand tot waar de golf zich voortplant). Standaard wordt de radius berekend als de afstand tussen het start- en eindpunt vermenigvuldigd met 3. De start- en eindpunten kunnen dicht bij elkaar of ver van elkaar verwijderd zijn, dus op basis van de afstand tussen hen berekenen we de schaal van ons raster. Als de huidige schaal niet overeenkomt met de vorige, berekenen we het raster opnieuw. De schaal kan worden vastgesteld met behulp van de Scale parameter. In dat geval wordt deze niet berekend en wordt het raster niet herberekend.

Voordat u begint met zoeken, moet u de weg- en obstakelkaart definiëren met behulp van de bijbehorende AddRoad en AddBlock methoden van de WayLayerGenerator klasse.

Voor de **AddRoad methode** moeten we specificeren:

- startPoint: Het beginpunt van de weg

- endPoint: Het eindpunt van de weg

- velocity: De snelheid van beweging op de weg

Voor de **AddBlock methode** moeten we specificeren:

- x: De x-coördinaat van de linkerbovenhoek van de blokkade

- y: De y-coördinaat van de linkerbovenhoek van de blokkade

- sizeX: De grootte in de x-as

- sizeY: De grootte in de y-as

Deze methoden stellen ons in staat om de weg- en obstakelkaart te definiëren voordat we beginnen met het padvindingsproces.

## Code voorbeelden

Hier zijn enkele codevoorbeelden die illustreren hoe je wegen en obstakels kunt instellen in het padvindingsalgoritme en de optimale route kunt vinden.

Voorbeeld 1: Een pad vinden tussen start- en eindpunten.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Voorbeeld 2**: De scale parameter instellen en negatieve coördinaten voor het punt hebben.

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Voorbeeld 3**: De IsMoveOnlyRoad parameter en zoekradius instellen.

```
WayOptions mapGeneratorOptions = new WayOptions();
mapGeneratorOptions.IsMoveOnlyRoad = true;
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddRoad(new Point(100, 100), new Point(140, 150), 10);
generator.AddRoad(new Point(140, 150), new Point(190, 100), 10);
Point startPoint = new Point(100, 100);
Point goalPoint = new Point(190, 100);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 100);
```

**Voorbeeld 4**: De scale parameter instellen voor sneller zoeken.

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**Voorbeeld 5**: Meerdere zoekvoorbeeld.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddBlock(200, 1700, 1500, 100, 0);
generator.AddBlock(1700, 200, 100, 1600, 0);
generator.AddBlock(200, 200, 1500, 100, 0);
generator.AddRoad(new Point(1000, 1150), new Point(200, 600), 10);
generator.AddRoad(new Point(50, 450), new Point(150, 1850), 10);

Point startPoint = new Point(1000, 1000);
Point goalPoint = new Point(1900, 1000);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 3500);

Point startPoint = new Point(50, 50);
Point goalPoint = new Point(70, 70);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

Deze codevoorbeelden bouwen en tonen wegpaden op de kaart voor gespecificeerde punten met behulp van weg informatie en way layer generator.

**Samenvattend**, is de optimale padzoeker een krachtig hulpmiddel voor het analyseren van wegennetwerken en het bepalen van de meest efficiënte routes tussen punten op een kaart. Het houdt rekening met verschillende factoren zoals wegentypes, obstakels en verschillende snelheden om het optimale pad te berekenen. Met de mogelijkheid om te zoeken naar paden zowel op wegen als off-road paden, evenals de zoekradius te beheersen en de prestaties en nauwkeurigheid aan te passen, biedt dit algoritme een veelzijdige oplossing voor routeoptimalisatie. Door verschillende vervoerswijzen in overweging te nemen en de weg- en obstakelsets dienovereenkomstig aan te passen, kan het worden gebruikt in verschillende scenario's zoals leveringsplanning of woon-werk optimalisatie. De codevoorbeelden en uitleg die zijn verstrekt demonstreren de mogelijkheden van het algoritme en de stappen die betrokken zijn bij het gebruik ervan. Uiteindelijk biedt de optimale padzoeker een robuuste manier om de meest efficiënte routes te vinden en navigatie in een wegennetwerk te verbeteren.