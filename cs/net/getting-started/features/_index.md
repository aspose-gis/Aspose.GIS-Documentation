---
title: "Funkce"
second_title: Aspose.GIS pro .NET
type: docs
url: /cs/net/features/
weight: 30
keywords: GIS C# knihovna, GIS C# API, čtení ShapeFile v C#
description: GIS C#.NET knihovna nebo API podporuje formáty Shapefile, GeoJSON, FileGDB, GML, KML, SVG, PostGis, Sql Server, GeoTIFF. Může číst, zapisovat, převádět a vizualizovat vektorová data, manipulovat s geometriemi, provádět analýzy a vyhledávat prostorové referenční systémy podle SRID.
---

Aspose.GIS pro .NET poskytuje bohatou sadu funkcí pro práci s daty uloženými v běžných GIS souborových formátech. Můžete číst a zapisovat vektorová GIS data, převádět mezi GIS souborovými formáty, vytvářet a analyzovat prvky geometrie a vykreslovat mapy do SVG.
# **Podporované Formáty**
Hlavní podporované souborové formáty jsou:

- Shapefile
- GeoJSON
- ESRI File Geodatabase (FileGDB)
- Geography Markup Language (GML)
- Keyhole Markup Language (KML)
- Scalable Vector Graphics (SVG)
- Databáze (PostGis, Sql Server)
- GeoTIFF

Viz [Podporované Souborové Formáty](/gis/cs/net/supported-file-formats/) pro úplný seznam.
# **Čtení a Zápis Vektorových Dat**
- Čtení vektorových dat
  - Iterace přes prvky vrstvy
  - Čtení prvků vrstvy podle indexu
  - Získávání metadat o vektorových vrstvách
- Zapisování vektorových dat
  - Vytváření nových vrstev a datasetů
- Práce s vícevrstvými datasety
  - Výpis existujících vrstev
  - Přidávání nových vrstev
  - Odstraňování vrstev z datasetu
- Budování prostorových indexů pro urychlení prostorových dotazů.
# **Převod Vektorových Dat**
- Převod dat do libovolného podporovaného formátu
- Provádění reprojekce při převodu dat
- Úprava atributů prvků během převodu
# **Vizualizace Dat**
- Vykreslování map do SVG, PNG, JPEG nebo BMP
- Přizpůsobení stylu pro každý typ geometrie
- Kombinování několika symbolizátorů pro provádění složitého kreslení
- Řízení vizuální reprezentace prvku pomocí pravidel vykreslování vrstvy
- Výpočet parametrů stylu prvku na základě hodnot jeho atributů

Viz [Vykreslování Map](/gis/cs/net/map-rendering/) pro podrobnosti.
# **Manipulace s Geometriemi**
- Vytváření bodů, čar a polygonů od základu
- Úprava existujících geometrií
- Označování objektů na mapě.
- Budování nelineárních geometrií (křivek)
- Linearizace nelineárních geometrií (křivek)
- Import a export geometrií z/do WKT a WKB
- Řízení modelu přesnosti výpočtů
# **Provádění Analýzy Vektorových Dat**
- Určení, zda se dvě geometrie navzájem protínají.
- Testování, zda se geometrie překrývají, dotýkají hran, protínají a další vztahy mezi geometriemi.
- Nalezení vzdáleností mezi geometriemi
- Výpočet konvexních obalů, centroidů a pufrových ploch geometrií
- Výpočet průniku, sjednocení nebo rozdílu libovolných geometrií.
# **Používání Prostorových Referenčních Systémů**
- Vyhledávání prostorových referenčních systémů podle SRID
- Čtení informací o SRS ze souborů dat
- Přiřazení SRS k datům, která vytváříte
- Reprojekce jednotlivých geometrií a celých vrstev
- Import prostorových referenčních systémů z WKT, export prostorových referenčních systémů do WKT
