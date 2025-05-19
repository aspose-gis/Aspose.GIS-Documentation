---
title: "Draw a map. A sliding map with tiles."
type: docs
url: /vi/net/showcases/sliding-map-with-tiles/
description: "How to draw tiles and build a sliding map from them."
weight: 80
aliases:
 - /vi/net/showcases/tiles/
---
# Draw a map. A sliding map with tiles.
In this article, we want to show how, using the [Aspose.GIS](https://www.nuget.org/packages/Aspose.GIS/) library and public data, you can build a sliding map that will be generated in real-time. Thanks to the new library feature, we can now query GIS data from the database via SQL query. Here is what we should get as a result:

![Result](result.png)

Repository source code [here](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest).

## Data preparation.

First of all, we will need geospatial information that we can load into the database. One of the popular sources of such information is `OpenStreetMap`, so let's use it. The most convenient way, in my opinion, is to extract data in pbf format from the public resource https://download.geofabrik.de/ . For example, let's download [Hungary](https://download.geofabrik.de/europe/hungary-latest.osm.pbf).

At the next stage, we need a working instance of `PostGIS`. Of course, you can use a locally installed version of `PostgreSQL`, but I find it very convenient to use Docker containers. Let's install PostGIS using a docker compose file:

```yaml
services:
  postgis:
    image: postgis/postgis
    environment:
      - POSTGRES_DB=gis
      - POSTGRES_USER=gis
      - POSTGRES_PASSWORD=password
    ports:
      - 5432:5432
    volumes:
      - d:\\local_folder:/usr/share/gisdata
```

The volume `d:\local_folder:/usr/share/gisdata` is needed to load GIS data from the local machine.

Next, let's run our container:

```bash
docker compose up
```

Connect to the database instance using `pgAdmin` and create the Hungary database there:

![Create DB](create_db.png)

or through the SQL command:

```sql
CREATE DATABASE Hungary;
```

Add the necessary extensions to this database:

![Extentions](add_extention.png)

These will be the `postgis` and `hstore` extensions. hstore is an extension that allows you to use the key-value data type. OpenStreetMap widely uses this type to describe attributes that do not fall into the category of main ones, and therefore no separate fields are created for them, but they are stored in the tags field.

There is also an SQL-like version of the commands:

```sql
CREATE EXTENSION IF NOT EXISTS hstore;
CREATE EXTENSION IF NOT EXISTS postgis;
```

Now let's connect to the container, in my case it is `local_folder-postgis-1`:

```bash
docker exec -it local_folder-postgis-1 sh
```

And install the program that will import data from the `pbf` file into the database:

```bash
apt-get update && apt-get install -y osm2pgsql
```

Make sure that the `hungary-latest.osm.pbf` file is located in your `local_folder` folder and then run the import command:

```bash
osm2pgsql --create --database=Hungary --user=gis --password --host=localhost --port=5432 --hstore /usr/share/gisdata/hungary-latest.osm.pbf
```

In the case of Hungary, it took me one and a half minutes to complete this command. The `--create` option means the simple creation mode of a new database. By the way, besides everything else, there is also the `--append` mode, which allows updating the data if they have changed:

```bash
osm2pgsql --append --slim OSMFILE
```

The `--hstore` option tells the application to additionally create a `tags` field of the hstore type to store additional information about features and geometries.

## Back-end

So, our data is ready to use. The next step on the way to creating a map is creating the back-end. The goal of our back-end is to generate special `tiles`, usually sized `256*256`, from which, like a mosaic, the map will be assembled in the browser. Each tile is uniquely identified by a combination of such parameters as Z, which is the degree of zooming in/out of the map, X is the row in the tile array, and Y is the column. You can read more about the nature of tiles [here](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames).

Our backend will be on ASP.NET Core accordingly, so let's get started with creating the project. So let's create a project based on pre-installed `ASP.NET Core MVC` template in `Visual Studio`.

Next, install the NuGet package `Aspose.GIS` into the project that will generate the tiles:

```cmd
dotnet add package Aspose.GIS --version 24.6.0
```

Clean the project from unnecessary files. So that the structure looks approximately as pictured below:

![Solution explorer](project.png)

Then delete the contents of the wwwroot/lib folder, as we will be installing our dependencies through `libman`. Below is the structure of the `libman.json` file:
```json
{
  "version": "1.0",
  "defaultProvider": "cdnjs",
  "libraries": [
    {
      "library": "leaflet@1.9.4",
      "destination": "wwwroot/lib/leaflet/"
    },
    {
      "library": "bootstrap@5.3.3",
      "destination": "wwwroot/lib/bootstrap/",
      "files": [
        "css/bootstrap-reboot.min.css"
      ]
    }
  ]
}
```


Added the client dependencies in the `_Layout.cshtml` file:

```razor
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>@ViewData["Title"] - Aspose.GIS.TilesTest</title>
    <link href="~/lib/bootstrap/css/bootstrap-reboot.min.css" rel="stylesheet" />
    @await RenderSectionAsync("Styles", required: false)
</head>
<body>
    @RenderBody()
    @await RenderSectionAsync("Scripts", required: false)
</body>
</html>
```

And also edit `Index.cshtml`:

```razor
@{
    ViewData["Title"] = "Home Page";
}

<div id="map"></div>

@section Styles {
    <link href="~/lib/leaflet/leaflet.min.css" rel="stylesheet" />
    <link href="~/css/map.css" rel="stylesheet" asp-append-version="true"/>
}

@section Scripts {
    <script src="~/lib/leaflet/leaflet.min.js"></script>
    <script src="~/js/map.js" asp-append-version="true"></script>
}
```

In this case, `bootstrap-reboot.min.css` resets the default style settings, and `leaflet.min.js` is responsible for rendering the map, i.e., assembling the pieces from the tiles into a map.
Let's set the height of the map block to the full height of the visible area in the `map.css` file:

```css
#map {
    min-height: 100vh;
}
```

The content of the `map.js` file is also quite simple, but a little more interesting:

```javascript
var map = L.map('map').setView([47.59995, 19.36623], 13);
const tiles = L.tileLayer('/tiles/{z}/{x}/{y}.png', {
    maxZoom: 19,
    minZoom: 11
}).addTo(map);
```

Here we use the API of the leaflet library, where we specify the id of the map block `'map'`, then in the `setView` method we set the coordinates of the place from which the initial map loading will start, and also the scale, for example, 13. Note the `tileLayer` method, it accepts a pattern string for the tile request to the server. This address can be either absolute for accessing third-party tile servers or relative as in our case. The route `'/tiles/{z}/{x}/{y}.png'` has not yet been implemented by us, and this is the most important part of our narrative that we have yet to implement.

To implement the request handler for generating tiles, let's first define a separate route in the `Program.cs` file:

```csharp
app.MapControllerRoute(name: "tiles",
  pattern: "tiles/{z}/{x}/{y}.png",
  defaults: new { controller = "Tiles", action = "Index" });

app.MapControllerRoute(
  name: "default",
  pattern: "{controller=Home}/{action=Index}/{id?}");
```

Here, two routes are defined, the first one for the tiles and the second one is the standard one. In the case of `MapControllerRoute`, order matters, so to avoid unexpected behavior, it is worth placing the route for the tiles before the standard route.

Next, let's move on to the handler itself. Create the `TilesController.cs` controller. It will have a single action of the following type:

```csharp
public async Task<ActionResult> Index(int z, int x, int y)
```

And so, now we have all the necessary data to calculate the bounding box covered by the tile in the corresponding coordinate system. In the current implementation, our data in the database is stored in the Web Mercator coordinate system. OpenStreetMap by default provides data in this coordinate system. Web Mercator is `projection`(coordinate system form) is most often used for mapping in various popular services because it covers almost the entire earth, and distances are measured in meters, which simplifies calculations, unlike, for example, `WGS 84`, since it will already be embedded in the geometry information. For these purposes, we use the `ST_AsEWKB` function.

A very important point is that at the current stage of database integration, the library can read geometries in `WKB` format, but it is better to use `EWKB`, i.e., Extended Well-Known Binary. 

We pre-calculate the bounding box for a tile through `ST_MakeEnvelope` function that will be used in all join queries and store the result in the `envelope` variable.

We specify that the passed coordinates correspond to the 3857 coordinate system (Web Mercator).

In the `WHERE` expression, we specify that we want to retrieve all geometries in the table that intersect with the envelope area using the `ST_Intersects` function.
> [!WARNING]
> A very important point is that at the current stage of database integration, the library can read geometries in `WKB` format, but it is better to use `EWKB`, i.e., Extended Well-Known Binary, then there will be no need to pass the spatial coordinate system information as a separate field since it will already be embedded in the geometry information. For these purposes, we use the `ST_AsEWKB` function.

The `ST_ClipByBox2D` function is used to clip geometries that go beyond the boundaries of the bounding box.

Well, now is the key moment, how to execute the query and get a layer with a set of features that will be rendered on the tile. It's quite simple:

```csharp
VectorLayer inputLayer;
using (var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary"))
{
  var builder = new DatabaseDataSourceBuilder();

  builder
    .FromQuery(query)
    .GeometryField("way")
    .AddAttribute("osm_id", AttributeDataType.Long)
    .AddAttribute("addr:housenumber", AttributeDataType.String)
    .AddAttribute("building", AttributeDataType.String)
    .AddAttribute("name", AttributeDataType.String)
    .AddAttribute("source", AttributeDataType.String)
    .AddAttribute("admin_level", AttributeDataType.Integer)
    .AddAttribute("place", AttributeDataType.String)
    .AddAttribute("landuse", AttributeDataType.String)
    .AddAttribute("water", AttributeDataType.String);
  conn.Open();

  var inputLayer = await builder.Build().ReadAsync(conn);
}
```

We have received one layer that contains all the geometries intersecting with our tile.

Okay, now we can color the map a little bit, like cities, water bodies, or forests. To do this, we need to break our single layer into separate independent ones that will match specific criteria, such as forests or rivers. Here's an example:

```csharp
var cities = inputLayer.Where(x => x.GetValue<string>("place") == "city");
citiesLayer = CopyToNewLayer(cities, inputLayer);

var forest = inputLayer.Where(x => x.GetValue<string>("landuse") == "forest");
forestLayer = CopyToNewLayer(forest, inputLayer);

var water = inputLayer.Where(x => !x.IsValueNull("water"));
waterLayer = CopyToNewLayer(water, inputLayer);
```

Below you will see how we will use these layers. The `CopyToNewLayer` function is auxiliary, it helps create new layers; for this article, it is not of great importance, you can look at its implementation in the repository that I referenced at the beginning of the article.

And now we just need to render all this into a PNG tile and return it to the client. This is a sample code:

```csharp
using var map = new Map(256, 256);
var pngStream = new MemoryStream();
var labeling = new RuleBasedLabeling
{
  { x => x.GetValue<string>("source") == "polygon",  new SimpleLabeling("addr:housenumber") },
  LabelingRule.CreateElseRule(new SimpleLabeling("name"))
};

map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);            
map.Add(citiesLayer, new SimpleFill { FillColor = Color.PeachPuff }, labeling);
map.Add(forestLayer, new SimpleFill { FillColor = Color.PaleGreen }, labeling);
map.Add(waterLayer, new SimpleFill { FillColor = Color.SkyBlue }, labeling);
map.Add(buildingsLayer, new SimpleFill { FillColor = Color.SandyBrown }, labeling);
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

pngStream.Seek(0, SeekOrigin.Begin);

return File(pngStream, "image/png");
```

Here, a `Map` object is created with the standard tile size of 256x256. Essentially, a `Map` is a canvas for rendering the tile. Next, we initialize a special object for labeling, to which rules for rendering text on the drawn geometric shapes are passed, for example, house numbers, street names, etc. In this case, if it is not a polygon and/or the `addr:housenumber` attribute is empty, the data will be taken from the `name` attribute.

An important point is that the Map object needs to explicitly specify the coordinate system in which it will render:

```csharp
map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
```

Next, we need to set the real area of the tile that should be rendered, not the expanded area that we requested from the database. To do this, we explicitly set the rendering area through the `Extent` property:

```csharp
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);
```

And then we sequentially add layers to the tile. The first one is added below all, and the last one is on top.

And finally we just need to render the tile as a byte stream in memory, then reset the stream to the beginning, and pass the stream to the ASP.NET Core platform for further transfer to the client:

```csharp
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

pngStream.Seek(0, SeekOrigin.Begin);

return File(pngStream, "image/png");
```

Hopefully we were able to pass on the basic ideas and techniques of map building to you. We wish you good luck in your experiments.