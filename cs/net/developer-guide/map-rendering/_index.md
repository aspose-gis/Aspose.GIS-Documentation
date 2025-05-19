---
title: Zobrazení mapy do obrazu SVG, PNG, JPG pomocí knihovny GIS C#
linktitle: "Zobrazení mapy"
type: docs
url: /cs/net/map-rendering/
weight: 50
description: S API GIS C# můžete vykreslit mapu ze souborů Shapefile, FileGDB, GeoJSON, KML, provádět pokročilé stylování a kreslit mapy z rastrových formátů.
---

## **Přehled vykreslování map**
S API Aspose.GIS for .NET C# můžete vykreslit mapu ze souboru Shapefile, FileGDB, GeoJSON, KML nebo jiných [podporovaných formátů souborů](/gis/net/supported-file-formats/) do SVG, PNG, JPEG nebo BMP.

Zde je kód C#, který ilustruje vykreslení mapy ze shapefilu do SVG pomocí výchozího nastavení:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



Zde je výsledek:



![zobrazení mapy](map_rendering.png)

Pojďme se podívat na kód blíže.

Nejprve instancujeme objekt [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map). Představuje kolekci vrstev z různých zdrojů, které lze vykreslit. Mapa má velikost, ve které má být zobrazena. Zde nastavíme mapu na 800 pixelů širokou a 400 pixelů vysokou.

Všimněte si, že mapa je uzavřena do příkazu using. To je nezbytné, protože mapa sleduje všechny zdroje k ní přidané a uvolní je po dokončení vykreslování a objekt Map je uvolněn.

Dále přidáme vrstvu ze souboru do mapy. Každá vrstva se vykresluje nad předchozí vrstvou v pořadí, v jakém byly do mapy přidány. Další podrobnosti o tom, jak otevřít vektorové vrstvy, naleznete [zde](/gis/net/working-with-vector-layers/).

Nakonec zavoláme [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) pro vykreslení mapy do souboru. Určíme cestu, kam uložit výsledný soubor, a renderer k použití. Třída [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers)obsahuje odkazy na všechny renderery obsažené v Aspose.GIS. Například můžete zadat Renderers.Png místo Renderers.Svg v uvedeném příkladu a vykreslit mapu do souboru PNG

## **Pokročilé stylování**
S API Aspose.GIS můžete přizpůsobit vykreslování a styly prvků, abyste dosáhli požadovaného vzhledu. 

![pokročilé stylování](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **Kreslení rastru v mapě**
S Aspose.GIS for .NET můžete vykreslit mapu z rastrových formátů.
### **Vykreslení s výchozím nastavením**
Zde je postup pro vykreslení mapy ze souboru GeoTIFF do SVG pomocí výchozího nastavení:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![výchozí rastr](default_raster.png)
### **Vykreslení zkosených rastrů**
S Aspose.GIS můžete vykreslit rastr se zkosenými rastrovými buňkami.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![zkosený rastr](skew_raster.png)
### **Vykreslení v polárním prostorovém referenčním systému**
Aspose.GIS vám umožní používat polární prostorové reference v procesu vykreslování mapy.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![gnomonické země](gnomonic_countries.png)
