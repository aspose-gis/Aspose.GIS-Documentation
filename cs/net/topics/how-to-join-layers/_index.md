---
title: "Jak spojovat vrstvy pomocí geometrie nebo atributů"
type: docs
url: /cs/net/how-to-join-layers
weight: 70
---

## Souhrn

V GIS jsou spojení výkonným mechanismem pro kombinování informací z různých vrstev na základě společného atributu nebo prostorového vztahu. Spojení vám umožňují sloučit datové atributy z jedné vrstvy (zdrojové vrstvy) s jinou vrstvou (cílovou vrstvou) pomocí společného pole nebo prostorového umístění. První je spojování dat podle klíče (atribut v tabulce). Pomocí společného pole, jako je jedinečný klíč, můžete propojit záznamy v jedné tabulce se záznamy v jiné tabulce. Druhý přístup je spojování dat podle umístění (prostorově). Podporujeme oba přístupy a nabízíme vám možnost je použít v závislosti na vašich potřebách.

Představme si, že jste obdrželi data popisující procentuální změnu populace pro různé okresy a chcete vytvořit několik map růstu populace na základě těchto informací. Zatímco vaše populační data jsou uložena v tabulce ve vaší databázi a sdílejí společné pole s vaší vrstvou, můžete tato data spojit se svými geografickými objekty a využít další pole pro označování, kategorizaci, dotazování nebo analýzu objektů vrstvy.

Typicky provádíte spojování dat na základě hodnoty pole, která existuje v obou tabulkách. Názvy polí nemusí být nutně shodné, ale datové typy by měly být stejné – čísla s čísly, řetězce s řetězci a tak dále. Spojení dat můžete provést pomocí geoprocessingového nástroje „Add Join“. Při spojování atributů jsou spojená pole dynamicky přidána do existující tabulky. Vlastnosti polí, jako jsou aliasy, viditelnost a formátování čísel, se zachovají při přidávání nebo odstraňování spojení.

## Možnosti spojování podle klíčového pole

- Tento přístup vám umožňuje **propojit záznamy z různých tabulek** na základě společného klíčového pole. Můžete určit klíčové pole, které se bude používat pro porovnání k vytvoření vztahu mezi záznamy. To je zvláště užitečné, když potřebujete sloučit data na základě identifikátoru nebo jiného jedinečného atributu.

Určení metody pro porovnávání dat na základě klíčového pole:

- Můžete definovat **různé metody porovnání** pro klíčové pole při slučování dat. Například si můžete vybrat přesnou shodu, porovnávat podle vzoru nebo v rámci rozsahu hodnot. To umožňuje přesnější určení vztahů mezi záznamy a dává kontrolu nad procesem slučování dat.

Určení seznamu názvů atributů, které se mají sloučit:

- Při slučování dat můžete určit **konkrétní atributy**, které by měly být sloučeny. To vám umožní vybrat pouze potřebné atributy pro slučování a spravovat strukturu výsledné tabulky.

## Možnosti spojování pomocí geometrie

- Tento přístup umožňuje propojit data na základě jejich **prostorového umístění**. Můžete definovat poloměr hledání, v rámci kterého se budou vyhledávat nejbližší geometrické objekty pro sloučení. To je užitečné, když potřebujete spojit data na základě jejich geografické pozice.

Řízení poloměru hledání pro nalezení nejbližších geometrických objektů:

- Můžete řídit **poloměr hledání** při slučování dat na základě umístění. Určením hodnoty poloměru určujete vzdálenost, v rámci které se budou vyhledávat nejbližší objekty pro sloučení. To dává kontrolu nad tím, které objekty se budou podílet na procesu slučování dat na základě jejich prostorového vztahu.

## Ukázkový projekt

Abychom lépe porozuměli funkcionalitě naší knihovny, zvažte [příklad jejího použití](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Layers.Join). Tento kód ilustruje, jak spojovat vektorové vrstvy podle atributů nebo geometrie.

Poskytnutý kód se skládá ze dvou metod JoinByIndex() a JoinByCoords(), které demonstrují operace spojování dat pomocí třídy LayerConstructor.

V metodě JoinByIndex():

- Vytvoří se seznamy geometrií s přidruženými atributy.

- Inicializuje se objekt LayerConstructor.

- Metoda vytvoří vektorovou vrstvu a geometrickou vrstvu pomocí poskytnutých geometrií.

- Geometrická vrstva je spojena na základě jedinečného identifikátoru ("Id") pomocí metody JoinLayersById().

- Vrácena je výsledná spojená vektorová vrstva.

V metodě JoinByCoords():

- Vytvoří se seznamy geometrií s přidruženými atributy.

- Inicializuje se objekt LayerConstructor.

- Vytvoří se geometrické vrstvy pomocí poskytnutých geometrií.

- Geometrické vrstvy jsou spojeny na základě shodných souřadnic pomocí metody JoinLayersByCoords().

- Vrácena je výsledná spojená vektorová vrstva.

Shrnuto, tyto metody ukazují dva různé přístupy ke spojování dat: jeden založený na jedinečném identifikátoru a druhý na shodných souřadnicích. Třída LayerConstructor usnadňuje tyto operace spojování dat.

## Možnosti spojení pro index

Třída JoinOptions poskytuje sadu možností pro konfiguraci spojování vrstev. Pojďme se hlouběji podívat do každé možnosti:

- **JoinAttributeName**: Tato možnost vám umožňuje určit název atributu ze spojené vrstvy, jehož hodnota bude použita v podmínce porovnání. Vytváří spojení mezi dvěma vrstvami na základě tohoto atributu.

- **TargetAttributeName**: S touto možností můžete určit název atributu z hlavní vrstvy, který se bude porovnávat s atributem ze spojené vrstvy. Pomáhá to určit shodné prvky mezi vrstvami.

- **JoinAttributeNames**: Tato možnost vám umožňuje určit seznam názvů atributů, které chcete spojit. Pokud je tento seznam prázdný nebo nastaven na null, všechny atributy ze spojené vrstvy budou zahrnuty do operace spojení. Výběrem konkrétních názvů atributů však můžete řídit atributy, které jsou spojeny, což může být užitečné pro optimalizaci využití paměti a času zpracování.

- **ConditionComparer**: Tato možnost vám umožňuje definovat vlastní logiku pro porovnávání hodnot atributů mezi prvky dvou vrstev. Ve výchozím nastavení používá EqualityComparer.Default, který kontroluje rovnost. Můžete však poskytnout vlastní komparátor, který implementuje IEqualityComparer pro specializovanější požadavky na porovnání.

- **JoinedAttributesPrefix**: Tato možnost vám umožňuje určit předponu řetězce pro názvy atributů spojené vrstvy. Výchozí hodnota je „joined_“, což znamená, že spojené atributy budou mít předponu „joined_“ ve výsledné spojené vrstvě. Tato předpona pomáhá rozlišit spojené atributy od původních atributů hlavní vrstvy.

Třída JoinOptions poskytuje flexibilitu a kontrolu nad různými aspekty procesu spojování vrstev. Můžete určit atributy, které se mají spojit, přizpůsobit logiku porovnání a definovat předponu pro výsledné spojené atributy. Tyto možnosti vám umožní přizpůsobit operaci spojení podle vašich specifických potřeb a dosáhnout smysluplných poznatků ze sloučených vrstev.

## Možnosti spojení pro geometrii

Třída **JoinByGeometryOptions** představuje možnosti pro spojování vrstev na základě geometrie. Pojďme se podívat na funkčnost každé možnosti:

- **Radius**: Tato možnost určuje poloměr, v rámci kterého se bude vyhledávat spojená geometrie. Určuje blízkost, v rámci které budou prvky z hlavní vrstvy shodu s prvky ze spojené vrstvy na základě jejich prostorového vztahu.

- **ConditionComparer**: Tato možnost vám umožňuje definovat vlastní logiku pro porovnávání hodnot atributů z prvků dvou vrstev. Ve výchozím nastavení používá EqualityComparer.Default, který kontroluje rovnost. Můžete však poskytnout vlastní komparátor, který implementuje IEqualityComparer pro konkrétnější požadavky na porovnání.

- **JoinedAttributesPrefix**: Tato možnost vám umožňuje určit předponu řetězce pro názvy atributů spojené vrstvy. Výchozí hodnota je „joined_“, což znamená, že spojené atributy budou mít předponu „joined_“ ve výsledné spojené vrstvě. Tato předpona pomáhá rozlišit spojené atributy od původních atributů hlavní vrstvy.

Třída JoinByGeometryOptions poskytuje prostředky pro přizpůsobení procesu spojování vrstev na základě jejich prostorového vztahu. Určením poloměru hledání můžete řídit rozsah, v rámci kterého se budou geometrie shodovat. To umožňuje jemné doladění operace spojení na základě požadované blízkosti mezi prvky. Možnost poskytnout vlastní komparátor vám dává flexibilitu při porovnávání hodnot atributů a možnost předponit spojené atributy pomáhá je rozlišit ve výsledné spojené vrstvě.

Použitím těchto možností můžete provádět prostorově uvědoměné slučování dat a získat poznatky ze sloučených vrstev, které jsou založeny na jejich prostorové blízkosti a hodnotách atributů.

## Souhrn

Mechanismus spojování dat v GIS umožňuje kombinovat geometrické objekty s jejich příslušnými atributy z různých vrstev. To poskytuje možnost analyzovat a extrahovat informace na základě prostorových a atributových vztahů v datech. Dostupné možnosti umožňují přizpůsobení procesu spojení tak, aby vyhovovaly specifickým požadavkům a analytickým potřebám v GIS datech.

Spojování dat usnadňuje různé úkoly, včetně:

- Nalezení objektů, které splňují specifická prostorová kritéria, jako je identifikace všech budov v okruhu 500 metrů od konkrétního bodu.

- Kombinování geografických dat pro vytvoření komplexnějšího a informativnějšího přehledu o situaci.

- Analýza hodnot atributů objektů na základě specifických prostorových podmínek za účelem identifikace trendů a vzorců.

Možnosti spojení dat umožňují přesnou konfiguraci procesu shody objektů. Tyto možnosti zahrnují výběr atributů, které se mají spojit, definování vlastní logiky pro porovnání hodnot atributů a přidání předpony k názvům atributů spojených dat. Tyto možnosti poskytují flexibilitu a přizpůsobivost procesu spojení, uspokojující specifické požadavky a cíle analýzy dat v GIS.

Mechanismus spojování dat hraje významnou roli v integraci a analýze geografických dat, což vede k komplexnějšímu porozumění prostorové a atributové povaze zkoumaných objektů.