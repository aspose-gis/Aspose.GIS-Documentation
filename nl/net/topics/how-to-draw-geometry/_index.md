---
title: "Hoe geometrie op een kaart te tekenen"
type: docs
url: /nl/how-to-draw-geometry
weight: 70
---

Om geometrische objecten op een kaart te maken en weer te geven, moet u beginnen met het **creëren van een geometrieobject**. Er zijn twee methoden die u kunt gebruiken:

- **Constructor voor elk geometrisch kenmerktype**
Deze methode omvat het gebruik van een aangepaste constructor voor elk geometrisch kenmerktype. Om bijvoorbeeld een punt te maken, gebruikt u de volgende code:

```
Point point = new Point(40.7128, -74.006);
```

Deze methode kan echter uitdagend en omslachtig worden om te beheren bij het maken van complexe objecten zoals polylijnen of collecties. Als gevolg hiervan moet de ontwikkelaar mogelijk veel regels code toevoegen, waardoor de leesbaarheid van de code afneemt. Het waarborgen van dataintegriteit tijdens initialisatie kan ook moeilijk zijn. Overweeg bijvoorbeeld het volgende voorbeeld dat een polygoon met een gat binnenin maakt:

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

Een ander nadeel van deze aanpak is het gebrek aan uniformiteit van de data voor initialisatie. U kunt geen repository met constanten of bestanden binnen uw project maken.

- **WKT (Well-Known Text)**
Deze methode omvat het genereren van geometrie vanuit WKT (Well-Known Text), wat een gestandaardiseerde manier biedt om geometrieën te maken. De volgende code demonstreert hoe u een punt en een lijn kunt maken:

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

Hoewel deze aanpak de prestaties enigszins kan verminderen vanwege de noodzaak om de string te parseren, vereenvoudigt het de creatie van complexere objecten.

U kunt meer details over WKT vinden in het volgende artikel: "Exporteren en importeren van gegevens naar/van WKT en WKB."

Weergeven van geometrische objecten op de kaart
Nadat u een geometrisch object hebt gemaakt, is de volgende stap om het op de kaart weer te geven. Hoewel de kaart lagen kan weergeven die uit verschillende bronnen en formaten zijn geladen, is de InMemoryLayer een laag die geen bron vereist.

**Om uw geometrische object weer te geven**, kunt u een InMemoryLayer maken en het object eraan toevoegen:

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

Nu kunt u **deze laag op de kaart weergeven en een bestand maken in een van de ondersteunde formaten**, zoals SVG, met de volgende code:

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

Nadat u de laag hebt toegevoegd en deze op de kaart hebt weergegeven, kunt u deze opslaan in een van de ondersteunde formaten. In dit voorbeeld is het SVG-formaat gekozen om potentiële problemen met Bitmap-ondersteuning te vermijden. Het is belangrijk op te merken dat Net 6.0 beperkte Bitmap-ondersteuning heeft, wat kan resulteren in beperkingen zoals het onvermogen om Bitmap-afbeeldingen weer te geven met Blazor WebAsm aan de clientzijde. Daarom is het bij het kiezen van een formaat om uw kaart op te slaan belangrijk om rekening te houden met de beperkingen van het doelplatform en een formaat te selecteren dat ermee compatibel is.

Het artikel legt uit hoe u geometrische objecten op een kaart kunt maken en weergeven met een standaard, eenvoudige stijl. De Aspose-bibliotheek biedt echter een breed scala aan stylingopties die kunnen worden aangepast aan uw behoeften. Om deze opties te verkennen, raden we u aan de [Aspose.MapRendering documentatie](https://docs.aspose.com/gis/net/map-rendering/) te raadplegen, die gedetailleerde informatie bevat over hoe u verschillende stylingtechnieken kunt gebruiken om de visuele aantrekkingskracht van uw kaart te verbeteren.

**Samenvattend**, om geometrische objecten op een kaart te maken, kunt u ofwel een constructor voor elk geometrisch kenmerktype gebruiken ofwel geometrie genereren vanuit WKT. Om het object weer te geven, plaatst u het op een laag en geeft u de laag weer op een kaart in standaardkaartstyling. Bewaar de kaart in een ondersteund formaat, zoals SVG, en gebruik onze bibliotheek om stylingopties te verkennen. Bovendien biedt onze bibliotheek de mogelijkheid om een ​​afgewerkt voorbeeld te bekijken door op de [link](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer) in de documentatie te klikken, wat u kan helpen bij het implementeren van deze technieken in uw eigen projecten.
