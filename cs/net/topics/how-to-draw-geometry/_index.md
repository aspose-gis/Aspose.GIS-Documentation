---
title: "Jak kreslit geometrii na mapě"
type: docs
url: /cs/net/how-to-draw-geometry
weight: 70
---

Pro vytvoření a zobrazení geometrických objektů na mapě je třeba nejprve **vytvořit objekt geometrie**. Existují dvě metody, které můžete použít:

- **Konstruktor pro každý typ geometrického prvku**
Tato metoda zahrnuje použití vlastního konstruktoru pro každý typ geometrického prvku. Například pro vytvoření bodu byste použili následující kód:

```
Point point = new Point(40.7128, -74.006);
```

Tato metoda se však může stát náročnou a těžkopádnou při vytváření složitých objektů, jako jsou polylinky nebo kolekce. Výsledkem je, že vývojář možná bude muset přidat mnoho řádků kódu, což způsobí pokles čitelnosti kódu. Zajištění integrity dat během inicializace může být také obtížné. Například zvažte následující příklad, který vytváří polygon s dírou uvnitř:

```
Polygon polygon = new Polygon();

LinearRing ring = new LinearRing();
ring.AddPoint(50.02, 36.22);
ring.AddPoint(49.99, 36.26);
ring.AddPoint(49.97, 36.23);
ring.AddPoint(49.98, 36.17);
ring.AddPoint(50.02, 36.22);

LinearRing hole = new LinearRing();
hole.AddPoint(50.00, 36.22);
hole.AddPoint(49.99, 36.20);
hole.AddPoint(49.98, 36.23);
hole.AddPoint(50.00, 36.24);
hole.AddPoint(50.00, 36.22);

polygon.ExteriorRing = ring;
polygon.AddInteriorRing(hole);
```

Další nevýhodou tohoto přístupu je nedostatek uniformity dat pro inicializaci. Nemůžete vytvořit úložiště konstant nebo souborů ve svém projektu.

- **WKT (Well-Known Text)**
Tato metoda zahrnuje generování geometrie z WKT (Well-Known Text), které nabízí standardizovaný způsob vytváření geometrií. Následující kód demonstruje, jak vytvořit bod a čáru:

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

I když tento přístup může mírně snížit výkon kvůli potřebě parsovat řetězec, zjednodušuje vytváření složitějších objektů.

Více podrobností o WKT naleznete v následujícím článku: "Exporting and Importing Data from/to WKT and WKB." (Export a import dat do/z WKT a WKB.)

Zobrazení geometrických objektů na mapě
Jakmile jste vytvořili geometrický objekt, dalším krokem je jeho zobrazení na mapě. Zatímco mapa může zobrazovat vrstvy načtené z různých zdrojů a formátů, InMemoryLayer je vrstva, která nevyžaduje zdroj.

**Pro zobrazení vašeho geometrického objektu** můžete vytvořit InMemoryLayer a přidat do něj objekt:

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

Nyní můžete **zobrazit tuto vrstvu na mapě a vytvořit soubor v jednom z podporovaných formátů**, jako je SVG, pomocí následujícího kódu:

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

Jakmile jste přidali vrstvu a zobrazili ji na mapě, můžete ji uložit v jednom z podporovaných formátů. V tomto příkladu je vybrán formát SVG, aby se předešlo potenciálním problémům s podporou Bitmap. Je důležité poznamenat, že Net 6.0 má omezenou podporu Bitmap, což může mít za následek omezení, jako je neschopnost vykreslovat obrázky Bitmap pomocí Blazor WebAsm na straně klienta. Proto při výběru formátu pro uložení mapy je důležité zvážit omezení cílové platformy a vybrat formát, který je s ní kompatibilní.

Článek vysvětluje, jak vytvářet a zobrazovat geometrické objekty na mapě s výchozím, jednoduchým stylem. Knihovna Aspose však nabízí širokou škálu možností stylingu, které lze přizpůsobit vašim potřebám. Prozkoumání těchto možností doporučujeme v [dokumentaci Aspose.MapRendering](https://docs.aspose.com/gis/net/map-rendering/), která poskytuje podrobné informace o tom, jak používat různé techniky stylingu ke zvýšení vizuální přitažlivosti vaší mapy.

**Shrnutí**, pro vytvoření geometrických objektů na mapě můžete použít buď konstruktor pro každý typ geometrického prvku, nebo generovat geometrii z WKT. Pro zobrazení objektu jej umístěte na vrstvu a zobrazte vrstvu na mapě s výchozím stylem mapy. Uložte mapu v podporovaném formátu, jako je SVG, a použijte naši knihovnu prozkoumat možnosti stylingu. Kromě toho naše knihovna poskytuje příležitost vidět hotový příklad kliknutím na [odkaz](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer) uvedený v dokumentaci, který vám může pomoci pochopit, jak implementovat tyto techniky ve vašich vlastních projektech.
