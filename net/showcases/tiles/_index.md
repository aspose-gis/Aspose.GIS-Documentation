In this article, we want to show how, using the Aspose.GIS library and public data, you can build a sliding map that will be generated in real-time. Thanks to the new library feature, we can now query GIS data from the database via SQL query. Here is what we should get as a result:
 
Repository address with source code: https://git.dev.dynabic.com/roman.charnashei/aspose.gis.tilestest 
First of all, we will need geospatial information that we can load into the database. One of the popular sources of such information is OpenStreetMap, so let's use it. The most convenient way, in my opinion, is to extract data in pbf format from the public resource https://download.geofabrik.de/ . For example, let's download Hungary https://download.geofabrik.de/europe/hungary-latest.osm.pbf .
At the next stage, we need a working instance of PostGIS. Of course, you can use a locally installed version of PostgreSQL, but I find it very convenient to use Docker containers. Let's install PostGIS using a docker compose file:
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
      - d:\\local¬_folder:/usr/share/gisdata


The volume d:\local_folder:/usr/share/gisdata is needed to load GIS data from the local machine. Next, let's run our container:
docker compose up

Connect to the instance using pgAdmin and create the Hungary database there:
 
Or the command:
CREATE DATABASE Hungary;

Add the necessary extensions to this database:
 
These will be the postgis and hstore extensions. hstore is an extension that allows you to use the key-value data type. OSM widely uses this type to describe attributes that do not fall into the category of main ones, and therefore no separate fields are created for them, but they are stored in the tags field. There is also an SQL-like version of the commands:

CREATE EXTENSION IF NOT EXISTS hstore;
CREATE EXTENSION IF NOT EXISTS postgis;

Now let's connect to the container, in my case to local_folder-postgis-1:
docker exec -it local_folder-postgis-1 sh

And install the program that will import data from the pbf file into the database:
apt-get update && apt-get install -y osm2pgsql

Make sure that the hungary-latest.osm.pbf file is located in our local_folder folder and run the import command:
osm2pgsql --create --database=Hungary --user=gis --password --host=localhost --port=5432 --hstore /usr/share/gisdata/hungary-latest.osm.pbf

In the case of Hungary, it took me one and a half minutes to complete this command. The --create option means the simple creation mode of a new database. By the way, besides everything else, there is also the --append mode, which allows updating the data if they have changed:

osm2pgsql --append --slim OSMFILE

The --hstore option tells the application to additionally create a tags field of the hstore type to store additional information about features and geometries.

So, our data is ready to use. The next step on the way to creating a map is creating the backend. The task of our backend is to generate special tiles, usually sized 256*256, from which, like a mosaic, the map will be assembled in the browser. Each tile is uniquely identified by a combination of such parameters as Z, which is the degree of zooming in/out of the map, X is the row in the tile array, and Y is the column. You can read more about the nature of tiles here: https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames. 
Our backend will be on ASP.NET Core accordingly, so let's get started with creating the project. Create a pre-installed template in Visual Studio 2022 ASP.NET Core MVC.
Install the Aspose.GIS package:

dotnet add package Aspose.GIS --version 24.6.0

Clean the project from unnecessary files. So that the structure looks approximately as in the image on the left.
Then delete the contents of the wwwroot/lib folder, as we will be installing our dependencies through libman.json. Below is the structure of the libman.json file:
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


Added the client dependencies in the _Layout.cshtml file:
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

And also edit Index.cshtml:

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

In this case, bootstrap-reboot.min.css resets the default style settings, and leaflet.min.js is responsible for rendering the map, i.e., assembling the pieces from the tiles into a map.
Let's set the height of the map block to the full height of the visible area in the map.css file:

#map {
    min-height: 100vh;
}

The content of the map.js file is also quite simple, but a little more interesting:

var map = L.map('map').setView([47.59995, 19.36623], 13);
const tiles = L.tileLayer('/tiles/{z}/{x}/{y}.png', {
    maxZoom: 19,
    minZoom: 11
}).addTo(map);

Here we use the API of the leaflet library, where we specify the id of the map block 'map', then in the setView method we set the coordinates of the place from which the initial map loading will start, and also the scale, for example, 13. Note the tileLayer method, it accepts a pattern string for the tile request to the server. This address can be either absolute for accessing third-party tile servers or relative as in our case. The route '/tiles/{z}/{x}/{y}.png' has not yet been implemented by us, and this is the most important part of our narrative that we have yet to implement.
To implement the request handler for generating tiles, let's first define a separate route in the Program.cs file:
app.MapControllerRoute(name: "tiles",
pattern: "tiles/{z}/{x}/{y}.png",
      defaults: new { controller = "Tiles", action = "Index" });

app.MapControllerRoute(
name: "default",
      pattern: "{controller=Home}/{action=Index}/{id?}");

Here, two routes are defined: the first one for the tiles and the second one is the standard one. In the case of MapControllerRoute, order matters, so to avoid unexpected behavior, it is worth placing the route for the tiles before the standard route.
Next, let's move on to the handler itself. Create the TilesController.cs controller. It will have a single action of the following type:
public async Task<ActionResult> Index(int z, int x, int y)

And so, now we have all the necessary data to calculate the bounding box covered by the tile in the corresponding coordinate system. In the current implementation, our data in the database is stored in the Web Mercator coordinate system. OSM by default provides data in this coordinate system. This projection is most often used for mapping in various popular services because it covers almost the entire earth, and distances are measured in meters, which simplifies calculations, unlike, for example, WGS 84, where distances are measured in angles, making calculations significantly more complex. Define the 'half of the world' constant, which is needed to calculate the tile coordinates; remember, distances are measured in meters:
private const double _halfOfWorld = 20037508.34;
The calculation of coordinates is as follows:
double worldSize = _halfOfWorld * 2;
double tileSize = worldSize / Math.Pow(2, z);

double min_x = x * tileSize - _halfOfWorld;
double max_x = (x + 1) * tileSize - _halfOfWorld;
double min_y = _halfOfWorld - (y + 1) * tileSize;
double max_y = _halfOfWorld - y * tileSize;

min_x = Math.Round(min_x, 10);
max_x = Math.Round(max_x, 10);
min_y = Math.Round(min_y, 10);
max_y = Math.Round(max_y, 10);

double ext_min_x = min_x - (max_x - min_x) * 0.05;
double ext_max_x = max_x + (max_x - min_x) * 0.05;
double ext_min_y = min_y - (max_y - min_y) * 0.05;
double ext_max_y = max_y + (max_y - min_y) * 0.05;

In the Web Mercator projection, the "world" is a square rectangle, so Y and X have the same lengths. Note that there are min_x, max_x, min_y, max_y values; these are the real sizes of the tile, but there is an extended version with the ext_ prefix, which has sides extended by 5%. This is done intentionally, and this is the bounding box that will actually be substituted into the query. The trick is that we extract an area slightly larger than necessary, but during rendering, we specify exactly the area we need. It is necessary for that when we will draw a tile that the rendering engine did not draw the boundaries of cut shapes, it creates an undesirable effect of the presence of stacks at the tiles.
Next, let's consider what the query looks like:
var cult = CultureInfo.InvariantCulture; // for dot decimal separator
string query = $@"WITH envelope (box) AS (
VALUES(ST_MakeEnvelope({ext_min_x.ToString(cult)}, {ext_min_y.ToString(cult)}, {ext_max_x.ToString(cult)}, {ext_max_y.ToString(cult)}, 3857)))
SELECT osm_id, ""addr:housename"", ""addr:housenumber"", 'polygon' as ""source"", building, admin_level, place, landuse, water, name, ST_AsEWKB(ST_ClipByBox2D(way, envelope.box)) as way
FROM public.planet_osm_polygon CROSS JOIN envelope
WHERE ST_Intersects(way, envelope.box) AND ({z} < 15 AND ST_Area(way) > 5000 OR {z} >= 15)
UNION ALL
SELECT osm_id, ""addr:housename"", ""addr:housenumber"", 'roads' as ""source"", building, admin_level, place, landuse, water, name, ST_AsEWKB(ST_ClipByBox2D(way, envelope.box)) as way
FROM public.planet_osm_roads CROSS JOIN envelope
WHERE ST_Intersects(way, envelope.box)
UNION ALL
SELECT osm_id, ""addr:housename"", ""addr:housenumber"", 'point' as ""source"", building, admin_level, place, landuse, water, name, ST_AsEWKB(ST_ClipByBox2D(way, envelope.box)) as way
FROM public.planet_osm_point CROSS JOIN envelope
WHERE ST_Intersects(way, envelope.box) AND {z} >= 15
UNION ALL
SELECT osm_id, ""addr:housename"", ""addr:housenumber"", 'line' as ""source"", building, admin_level, place, landuse, water, name, ST_AsEWKB(ST_ClipByBox2D(way, envelope.box)) as way
FROM public.planet_osm_line CROSS JOIN envelope
WHERE ST_Intersects(way, envelope.box)";

What happens here is that during data import, the osm2pgsql utility creates a number of tables (planet_osm_polygon, planet_osm_roads, planet_osm_point, planet_osm_line) that correspond to different geometries and attributes but related to one map. The way field is the geometry; the remaining attributes will be useful when rendering. We pre-calculate the limited box (ST_MakeEnvelope) that will be used in all join queries and store the result in the envelope variable. We specify that the passed coordinates correspond to the 3857 coordinate system (Web Mercator). In the WHERE expression, we specify that we want to retrieve all geometries in the table that intersect with the envelope area using the ST_Intersects function. A very important point is that at the current stage of database integration, the library can read geometries in WKB format, but it is better to use EWKB, i.e., Extended Well-Known Binary, then there will be no need to pass the spatial coordinate system information as a separate field since it will already be embedded in the geometry information. For this, we use the ST_AsEWKB function. The ST_ClipByBox2D function is used to clip geometries that go beyond the boundaries of the bounding box.
Well, now is the key moment, how to execute the query and get a layer with a set of features that will be rendered on the tile. It's quite simple:
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

We have received one layer that contains all the geometries intersecting with our tile.
Okay, now we can color the map a little bit, like cities, water bodies, or forests. To do this, we need to break our single layer into separate independent ones that will match specific criteria, such as forests or rivers. Here's an example:
var cities = inputLayer.Where(x => x.GetValue<string>("place") == "city");
citiesLayer = CopyToNewLayer(cities, inputLayer);

var forest = inputLayer.Where(x => x.GetValue<string>("landuse") == "forest");
forestLayer = CopyToNewLayer(forest, inputLayer);

var water = inputLayer.Where(x => !x.IsValueNull("water"));
waterLayer = CopyToNewLayer(water, inputLayer);

Below you will see how we will use these layers. The CopyToNewLayer function is auxiliary, it helps create new layers; for this article, it is not of great importance, you can look at its implementation in the repository that I indicated at the beginning of the article.


And now we just need to render all this into a PNG tile and return it to the client. This is a sample code:

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

Here, a Map object is created with the standard tile size of 256x256. Essentially, a Map is a canvas for rendering the tile. Next, we initialize a special object for labeling, to which rules for rendering text on the drawn geometric shapes are passed, for example, house numbers, street names, etc. In this case, if it is not a polygon and/or the “addr:housenumber” attribute is empty, the data will be taken from the name attribute.
 An important point is that the Map object needs to explicitly specify the coordinate system in which it will render:
map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
Next, we need to set the real area of the tile that should be rendered, not the expanded area that we requested from the database. To do this, we explicitly set the rendering area through the Extent property:
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);
And then we sequentially add layers to the tile; the first one is added below all, and the last one is on top. Simultaneously, we pass the SimpleFill object, which contains layer rendering settings, and the SimpleLabeling object. 
We just need to render the tile as a byte stream in memory, reset the stream to the beginning, and pass the stream to the ASP.NET Core platform for further transfer to the client:
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);
pngStream.Seek(0, SeekOrigin.Begin);
return File(pngStream, "image/png");