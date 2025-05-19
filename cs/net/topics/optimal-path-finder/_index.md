---
title: "Optimal Path Finder"
type: docs
url: /cs/net/optimal-path-finder
weight: 70
---

## Summary

Hledání nejkratší cesty v silniční síti je proces analýzy zaměřený na určení nejefektivnějšího způsobu cestování mezi body na mapě. Tento nástroj může být užitečný pro vytváření optimálních tras s více zastávkami nebo měření vzdálenosti a doby jízdy mezi různými místy. S každým voláním naše technologie dokáže najít optimální trasy pro jedno nebo více vozidel. Například, může pomoci řidičům nalézt optimální trasy pro doručování zboží nebo určit optimální dojezdovou vzdálenost z domova do práce pro různé cestující.

## Algorithm Capabilities

Naše knihovna poskytuje možnost vytvořit nej**optimálnější trasu mezi dvěma body** na mapě. Má následující hlavní funkce:

1. Hledání optimální cesty na mapě, s ohledem na stezky a překážky: Zohledňujeme nejen silnice, ale také terénní cesty, jako jsou turistické trasy, chodníky a překážky, které mohou ovlivnit výběr optimální cesty.

2. Hledání optimální cesty pouze po silnicích: Pokud potřebujete najít trasu výhradně po silnicích, poskytujeme tuto možnost. To je užitečné například pro vozidla omezená na cestování pouze po silnicích.

3. Nastavení různých rychlostí pro silnice: Máme možnost přiřadit různé rychlosti různým silnicím. Například vyšší rychlosti lze nastavit pro hlavní dálnice a nižší rychlosti pro úzké uličky.

4. Nastavení obdélníkových překážek: Můžete definovat obdélníkové překážky na mapě, které je třeba zohlednit při vytváření optimální cesty. To je užitečné, když existují známé překážky, jako jsou budovy nebo jezera (jejich aproximace).

5. Omezení rozsahu hledání pro silnice: Můžete omezit rozsah hledání pro silnice, abyste snížili dobu hledání a zaměřili se pouze na určitou oblast.

6. Kontrola výkonu a přesnosti: Poskytujeme možnost kontrolovat výkon a přesnost algoritmu. Můžete jej vyladit tak, aby dosáhl požadované rovnováhy mezi rychlostí vyhledávání a přesností konstrukce trasy.

Dále poskytneme podrobnější popis každé z těchto funkcí a prozkoumáme příklady jejich aplikací.

## Approach to Solution

I když hledání cesty je netriviální úkol, existuje několik dobrých a spolehlivých algoritmů, které jsou uznávány v komunitě vývojářů.

V naší implementaci jsme použili modifikovaný Leeho algoritmus. Máme mřížku buněk na rovině. Z počátečního bodu se šíří vlna v 8 směrech (včetně diagonál) do sousedních buněk, vypočítává čas potřebný k dosažení každé z nich. Sousední buňka může obsahovat překážku nebo silnici. Silnice mohou mít různé koeficienty rychlosti. Tímto způsobem „označujeme“ naši mřížku časem potřebným k dosažení každé buňky z počáteční buňky v určitém poloměru nebo do dosažení cílového bodu. Pokud dosáhneme cílového bodu, sestavíme obrácenou cestu pomocí naší mřížky.

Pro určení optimální trasy v silniční síti je třeba provést několik kroků. Nejprve musíte definovat silnice a určit rychlost pohybu na každé z nich. Měli byste také zvážit přítomnost umělých a přírodních překážek, které mohou ovlivnit průchod cestou. Poté musíte specifikovat počáteční a cílový bod hledání. Jakmile jsou tyto předběžné kroky dokončeny, můžete pokračovat ke skutečnému hledání cesty. Výsledkem bude cesta reprezentovaná například jako seznam souřadnic bodů.

Je důležité poznamenat, že optimální cesta může záviset na zvoleném způsobu dopravy, protože rychlost pohybu a sada překážek se mohou lišit. Proto by měly být pro každý typ dopravy použity různé sady silnic a překážek při hledání optimální cesty.

## Demo Project on GitHub

Abychom lépe porozuměli funkčnosti naší knihovny, podívejme se na [příklad jejího použití](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths). Tento kód ilustruje, jak nastavit silnice a překážky v algoritmu hledání cesty a najít optimální trasu.

Příklad se skládá z následujících kroků:

1. Vytvoření seznamu informací o silnicích (RoadInfo), který zahrnuje informace o segmentu silnice (Segment) a rychlosti pohybu (Velocity).
2. Přidání rychlých silnic do seznamu.
3. Přidání pomalých okružních silnic do seznamu.
4. Vytvoření generátoru vrstev cest (WayLayerGenerator) a přidání silnic do generátoru.
5. Hledání více cest z počátečního bodu (startPoint) do cílových bodů (goalPoint01, goalPoint02, goalPoint03) pomocí určeného poloměru (radius).
6. Příprava vrstvy silnic (roadsLayer) pro zobrazení na mapě a přidání objektů silnic.
7. Příprava vrstvy cest (wayLayer) pro zobrazení na mapě a vytvoření geometrických objektů pro každou nalezenou cestu.
8. [Zobrazení mapy](https://docs.aspose.com/gis/net/how-to-draw-geometry/) pomocí funkce ShowMap, uložení mapy na určené místo.

Tento kód sestavuje a zobrazuje cesty silnic na mapě pro zadané body pomocí informací o silnicích a generátoru vrstev cest.

## Search Options

Hledání cesty se provádí pomocí třídy **WayLayerGenerator** umístěné v oborovém jménu Aspose.Gis.GeoTools.WayAnalyzer.

Třída WayLayerGenerator má metodu **FindTheWay** pro nalezení cesty z počátečního bodu do cíle. Pro vytvoření instance třídy WayLayerGenerator předáváme parametry WayOptions (všechny parametry jsou volitelné):

- StartPoint: Počáteční bod

- GoalPoint: Cílový bod

- Radius: Poloměr hledání

- Scale: Měřítko mřížky

- IsMoveOnlyRoad: Zda se má hledat cesta pouze po silnicích

Pozoruhodným rysem je parametr Scale. Pokud je specifikován v konstruktoru, fixujeme konstantní měřítko pro následné vyhledávání. Pokud parametr Scale není nastaven, ale StartPoint a GoalPoint jsou nastaveny, vypočítáme měřítko jako vzdálenost mezi počátečním a cílovým bodem dělenou 100. Ve všech ostatních případech je výchozí hodnota Scale 1. Pro zkušené uživatele je lepší nastavit Scale nebo přímo nastavit StartPoint a GoalPoint, aby se silnice a překážky nejefektivněji reprezentovaly na mřížce (zejména pokud jich je mnoho).

Pro použití metody FindTheWay musíme specifikovat počáteční a cílový bod. Můžeme také nastavit poloměr hledání (vzdálenost, do které se vlna šíří). Ve výchozím nastavení se poloměr vypočítá jako vzdálenost mezi počátečním a cílovým bodem vynásobená 3. Počáteční a cílový body mohou být blízko nebo velmi daleko od sebe, takže na základě vzdálenosti mezi nimi vypočítáme měřítko naší mřížky. Pokud se aktuální měřítko neshoduje s předchozím, znovu vypočítáme mřížku. Měřítko lze fixovat pomocí parametru Scale. V tomto případě se nevypočítává a mřížka se nepřepočítává.

Před zahájením hledání musíme definovat mapu silnic a překážek pomocí odpovídajících metod AddRoad a AddBlock třídy WayLayerGenerator.

Pro metodu **AddRoad** musíme specifikovat:

- startPoint: Počáteční bod silnice

- endPoint: Koncový bod silnice

- velocity: Rychlost pohybu na silnici

Pro metodu **AddBlock** musíme specifikovat:

- x: X souřadnice levého horního rohu bloku

- y: Y souřadnice levého horního rohu bloku

- sizeX: Velikost v ose x

- sizeY: Velikost v ose y

Tyto metody nám umožňují definovat mapu silnic a překážek před zahájením procesu hledání cesty.

## Code examples

Zde jsou některé příklady kódu, které ilustrují, jak nastavit silnice a překážky v algoritmu hledání cesty a najít optimální trasu.

**Příklad 1**: Nalezení cesty mezi počátečním a cílovým bodem.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Příklad 2**: Nastavení parametru měřítka a negativních souřadnic pro bod.

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Příklad 3**: Nastavení parametru IsMoveOnlyRoad a rozsahu hledání.

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

**Příklad 4**: Nastavení parametru měřítka pro rychlejší vyhledávání.

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**Příklad 5**: Příklady více vyhledávání.

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

Tyto příklady kódu sestavují a zobrazují cesty silnic na mapě pro zadané body pomocí informací o silnicích a generátoru vrstev cest.

**Shrnuto**, optimalizátor cesty je výkonný nástroj pro analýzu silničních sítí a určení nejefektivnějších tras mezi body na mapě. Zohledňuje různé faktory, jako jsou typy silnic, překážky a různé rychlosti, aby vypočítal optimální cestu. S možností hledání cest jak po silnicích, tak i mimo ně, stejně jako kontrola rozsahu hledání a úprava výkonu a přesnosti poskytuje všestranné řešení pro optimalizaci tras. Zvažováním různých způsobů dopravy a úpravou sad silnic a překážek podle toho může být použit v různých scénářích, jako je plánování doručování nebo optimalizace dojíždění. Poskytnuté příklady kódu a vysvětlení demonstrují možnosti algoritmu a kroky zapojené do jeho používání. V konečném důsledku nabízí optimalizátor cesty robustní způsob, jak najít nejefektivnější trasy a zlepšit navigaci v silniční síti.