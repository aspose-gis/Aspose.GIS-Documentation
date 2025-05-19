---
title: "Hoe lagen samen te voegen met behulp van geometrie of attribuut"
type: docs
url: /nl/how-to-join-layers
weight: 70
---

## Samenvatting

In GIS zijn joins een krachtig mechanisme om informatie uit verschillende lagen te combineren op basis van een gemeenschappelijk kenmerk of ruimtelijke relatie. Joins stellen u in staat om attribuutgegevens van één laag (de bronslaag) samen te voegen met een andere laag (de doellaag) met behulp van een gemeenschappelijk veld of een ruimtelijke locatie. De eerste is het samenvoegen van gegevens op basis van sleutel (attribuut in de tabel). Door gebruik te maken van een gemeenschappelijk veld, zoals een unieke sleutel, kunt u records in één tabel koppelen aan records in een andere tabel. De tweede benadering is het samenvoegen van gegevens op locatie (ruimtelijk). We ondersteunen beide benaderingen en bieden u de mogelijkheid om ze te gebruiken afhankelijk van uw behoeften.

Stel dat u gegevens heeft ontvangen die het percentage verandering in de populatie voor verschillende districten beschrijven, en u wilt op basis van deze informatie verschillende kaarten van de bevolkingsgroei genereren. Hoewel uw bevolkingsgegevens zijn opgeslagen in een tabel in uw database en een gemeenschappelijk veld delen met uw laag, kunt u deze gegevens samenvoegen met uw geografische objecten en aanvullende velden gebruiken voor het labelen, categoriseren, bevragen of analyseren van laageobjecten.

Doorgaans voert u data joins uit op basis van een veldwaarde die in beide tabellen bestaat. De veldnamen hoeven niet noodzakelijk overeen te komen, maar de gegevenstypen moeten hetzelfde zijn - getallen met getallen, strings met strings, enzovoort. U kunt de data join uitvoeren met behulp van het geoprocessing-gereedschap "Add Join". Bij het samenvoegen van attributen worden de samengevoegde velden dynamisch toegevoegd aan de bestaande tabel. Veldproperties zoals aliassen, zichtbaarheid en nummeropmaak blijven behouden bij het toevoegen of verwijderen van de join.

## Mogelijkheden om te joinen op sleutelveld

- Deze benadering stelt u in staat om **records uit verschillende tabellen** te koppelen op basis van een gemeenschappelijk sleutelveld. U kunt het sleutelveld specificeren dat gebruikt moet worden voor vergelijking om de relatie tussen records tot stand te brengen. Dit is vooral handig wanneer u gegevens wilt samenvoegen op basis van een identifier of ander uniek attribuut.

Het specificeren van de methode voor het vergelijken van gegevens op basis van het sleutelveld:

- U kunt **verschillende vergelijkingsmethoden** definiëren voor het sleutelveld bij het samenvoegen van gegevens. Zo kunt u kiezen voor een exacte overeenkomst, vergelijken op basis van een patroon of binnen een bereik van waarden. Dit maakt een nauwkeurigere bepaling van relaties tussen records mogelijk en geeft controle over het data-samenvoegingsproces.

Het specificeren van een lijst met attributennamen die moeten worden samengevoegd:

- Bij het samenvoegen van gegevens kunt u **specifieke attributen** specificeren die moeten worden samengevoegd. Dit stelt u in staat om alleen de noodzakelijke attributen te selecteren voor het samenvoegen en de structuur van de resulterende tabel te beheren.

## Mogelijkheden om te joinen met behulp van geometrie

- Deze benadering maakt het mogelijk om gegevens te koppelen op basis van hun **ruimtelijke locatie**. U kunt een zoekradius definiëren binnen welke de dichtstbijzijnde geometrische objecten worden gezocht voor samenvoeging. Dit is handig wanneer u gegevens wilt samenvoegen op basis van hun geografische positie.

Het regelen van de zoekradius voor het vinden van dichtstbijzijnde geometrische objecten:

- U kunt **de zoekradius** regelen bij het samenvoegen van gegevens op basis van locatie. Door een radiuswaarde te specificeren, bepaalt u de afstand binnen welke de dichtstbijzijnde objecten worden gezocht voor samenvoeging. Dit geeft controle over welke objecten zullen deelnemen aan het data-samenvoegingsproces op basis van hun ruimtelijke relatie.

## Demo Project

Om de functionaliteit van onze bibliotheek beter te begrijpen, kunt u [een voorbeeld van het gebruik](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Layers.Join) overwegen. Deze code illustreert hoe vectorlagen kunnen worden samengevoegd op basis van attributen of geometrie.

De meegeleverde code bestaat uit twee methoden, JoinByIndex() en JoinByCoords(), die data-samenvoegingsbewerkingen demonstreren met behulp van een LayerConstructor klasse.

In de JoinByIndex() methode:

- Er worden lijsten met geometrieën gemaakt met bijbehorende attributen.

- Een LayerConstructor object wordt geïnitialiseerd.

- De methode maakt een vectorlaag en een geometrie laag met behulp van de meegeleverde geometrieën.

- De geometrie laag wordt samengevoegd op basis van een unieke identifier ("Id") met behulp van de JoinLayersById() methode.

- De resulterende samengevoegde vectorlaag wordt geretourneerd.

In de JoinByCoords() methode:

- Er worden lijsten met geometrieën gemaakt met bijbehorende attributen.

- Een LayerConstructor object wordt geïnitialiseerd.

- Geometrie lagen worden gemaakt met behulp van de meegeleverde geometrieën.

- De geometrie lagen worden samengevoegd op basis van overeenkomende coördinaten met behulp van de JoinLayersByCoords() methode.

- De resulterende samengevoegde vectorlaag wordt geretourneerd.

Samenvattend tonen deze methoden twee verschillende benaderingen voor het samenvoegen van gegevens: één op basis van een unieke identifier en de andere op basis van overeenkomende coördinaten. De LayerConstructor klasse faciliteert deze data-samenvoegingsbewerkingen.

## Join Opties voor Index

De JoinOptions klasse biedt een reeks opties voor het configureren van lagen die worden samengevoegd. Laten we dieper ingaan op elke optie:

- **JoinAttributeName**: Met deze optie kunt u de attributennaam specificeren uit de samengevoegde laag waarvan de waarde wordt gebruikt in de vergelijkingsconditie. Het legt de verbinding tussen de twee lagen vast op basis van dit attribuut.

- **TargetAttributeName**: Hiermee kunt u de attributennaam specificeren uit de hoofdlaag die wordt vergeleken met het attribuut uit de samengevoegde laag. Dit helpt bij het bepalen van de overeenkomende features tussen de lagen.

- **JoinAttributeNames**: Met deze optie kunt u een lijst met attributennamen specificeren die u wilt samenvoegen. Als deze lijst leeg of op null wordt ingesteld, worden alle attributen uit de samengevoegde laag opgenomen in de join operatie. Door specifieke attributennamen te selecteren, kunt u echter wel controle uitoefenen op de attributen die worden samengevoegd, wat handig kan zijn voor het optimaliseren van het geheugensgebruik en de verwerkingstijd.

- **ConditionComparer**: Met deze optie kunt u een aangepaste logica definiëren voor het vergelijken van attribuutwaarden tussen de features van de twee lagen. Standaard wordt de EqualityComparer.Default comparer gebruikt, die controleert op gelijkheid. U kunt echter uw eigen aangepaste comparer leveren die IEqualityComparer implementeert voor meer gespecialiseerde vergelijkingsvereisten.

- **JoinedAttributesPrefix**: Met deze optie kunt u een prefixstring specificeren voor de attributennamen van de samengevoegde laag. De standaardwaarde is "joined_", wat betekent dat samengevoegde attributen worden geprefixeerd met "joined_" in de resulterende samengevoegde laag. Dit prefix helpt bij het onderscheiden van samengevoegde attributen van de oorspronkelijke attributen van de hoofdlaag.

De JoinOptions klasse biedt flexibiliteit en controle over verschillende aspecten van het lagen-samenvoegingsproces. U kunt de te joinen attributen specificeren, de vergelijkingslogica aanpassen en een prefix definiëren voor de resulterende samengevoegde attributen. Deze opties stellen u in staat om de samenvoegingsoperatie af te stemmen op uw specifieke behoeften en betekenisvolle inzichten te verkrijgen uit de samengevoegde lagen.

## Join Opties voor Geometrie

De **JoinByGeometryOptions** klasse vertegenwoordigt opties voor het samenvoegen van lagen op basis van geometrie. Laten we de functionaliteit van elke optie verkennen:

- **Radius**: Deze optie specificeert de radius binnen welke de samengevoegde geometrie wordt gezocht. Het bepaalt de nabijheid binnen welke features uit de hoofdlaag worden gematcht met features uit de samengevoegde laag op basis van hun ruimtelijke relatie.

- **ConditionComparer**: Met deze optie kunt u een aangepaste logica definiëren voor het vergelijken van attribuutwaarden van de features van de twee lagen. Standaard wordt de EqualityComparer.Default gebruikt, die controleert op gelijkheid. U kunt echter uw eigen aangepaste comparer leveren die IEqualityComparer implementeert voor meer specifieke vergelijkingsvereisten.

- **JoinedAttributesPrefix**: Met deze optie kunt u een prefixstring specificeren voor de attributennamen van de samengevoegde laag. De standaardwaarde is "joined_", wat betekent dat samengevoegde attributen worden geprefixeerd met "joined_" in de resulterende samengevoegde laag. Dit prefix helpt bij het onderscheiden van samengevoegde attributen van de oorspronkelijke attributen van de hoofdlaag.

De JoinByGeometryOptions klasse biedt de middelen om het proces van het samenvoegen van lagen op basis van hun ruimtelijke relatie aan te passen. Door een zoekradius te specificeren, kunt u controleren in welke mate geometrieën worden gematcht. Dit maakt het mogelijk om de samenvoegingsoperatie af te stemmen op de gewenste nabijheid tussen features. De optie om een aangepaste comparer te leveren geeft u flexibiliteit bij het vergelijken van attribuutwaarden, en de optie om samengevoegde attributen te prefixeren helpt ze te onderscheiden in de resulterende samengevoegde laag.

Door deze opties te gebruiken, kunt u ruimtelijk bewust data samenvoegen en inzichten verkrijgen uit de samengevoegde lagen die gebaseerd zijn op hun ruimtelijke nabijheid en attribuutwaarden.

## Samenvatting

Het mechanisme voor het samenvoegen van gegevens in GIS maakt het mogelijk om geometrische objecten te combineren met hun respectievelijke attributen uit verschillende lagen. Dit biedt de mogelijkheid om te analyseren en informatie te extraheren op basis van ruimtelijke en attribuutrelaties binnen de data. De beschikbare opties maken aanpassing van het samenvoegingsproces mogelijk om te voldoen aan specifieke vereisten en analysebehoeften in GIS-data.

Het samenvoegen van gegevens vergemakkelijkt verschillende taken, waaronder:

- Het vinden van objecten die voldoen aan specifieke ruimtelijke criteria, zoals het identificeren van alle gebouwen binnen een straal van 500 meter rond een specifiek punt.

- Het combineren van geografische data om een ​​uitgebreider en informatief overzicht van een situatie te creëren.

- Het analyseren van attribuutwaarden van objecten op basis van specifieke ruimtelijke voorwaarden om trends en patronen te identificeren.

De opties voor het samenvoegen van gegevens maken een nauwkeurige configuratie mogelijk van het proces voor het matchen van objecten. Deze opties omvatten het selecteren van de attributen die moeten worden samengevoegd, het definiëren van aangepaste logica voor het vergelijken van attribuutwaarden en het toevoegen van een prefix aan de attributennamen van de samengevoegde data. Deze opties bieden flexibiliteit en aanpassingsvermogen aan het samenvoegingsproces, die aansluiten bij specifieke vereisten en de doelen van data-analyse in GIS.

Het mechanisme voor het samenvoegen van gegevens speelt een belangrijke rol bij het integreren en analyseren van geografische data, wat resulteert in een uitgebreider begrip van de ruimtelijke en attribuut aard van de onderzochte objecten.