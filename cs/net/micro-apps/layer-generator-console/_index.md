---
title: "Konzolová aplikace Generátoru vrstev"
type: docs
url: /cs/net/layer-generator-console
weight: 50
---

## Souhrn

Tato konzolová aplikace je navržena pro generování geometrických objektů různých typů a jejich ukládání do zvoleného formátu. Umožňuje vytvářet body, polygony a polylinky, specifikovat počet objektů k vygenerování a vybrat výstupní formát pro uložení.

## Použití

Syntaxe příkazu:

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

Argumenty:

```
-t, --type: Typ geometrie. Jeden z následujících: Point, Polygon, Polyline.

-c, --count: Povinné. Počet objektů k vygenerování. Například: 15.

-f, --fileName: Povinné. Název souboru pro uložení. Zadejte název souboru a příponu. Například: test.json.

-o, --outputFormat: Výstupní formát. Podporované formáty naleznete zde.

--help: Zobrazí pomocné informace k příkazu.

--version: Zobrazí informace o verzi aplikace.
```

Příklad příkazu pro vytvoření 15 náhodných bodů a jejich uložení do souboru s formátem "test.json":

```
app.exe -t Point -c 15 -f test.json -o json
```

## Instalace a licencování

Pokud chcete aplikaci používat, musíte stáhnout archiv a rozbalit jej. Postupujte podle odkazu níže.

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

Ačkoli je konzolová aplikace Generátoru vrstev Aspose.GIS zdarma, Aspose.GIS .NET je licencováno obvyklým způsobem, takže můžete znovu použít svou licenci prostřednictvím aplikace nebo vyhodnotit aplikaci pomocí Aspose.GIS .NET v zkušebním režimu nebo požádat o dočasnou licenci.

## Závěr

Generátor geometrických objektů je pohodlná konzolová aplikace, která vám pomůže vytvářet vzorky geometrie různých typů a ukládat je do požadovaného formátu. Je to užitečný nástroj pro práci s geodata a vývoj geo informačních systémů.
