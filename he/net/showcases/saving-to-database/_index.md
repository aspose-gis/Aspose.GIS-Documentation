---
title: "עדכוני Aspose.GIS: עריכת תכונות וגיאומטריות ושמירת השינויים במסד הנתונים."
type: docs
url: /he/net/showcases/saving-changes-to-database/
description: "מאמר זה סוקר את השיפורים האחרונים בספריית Aspose.GIS, תוך התמקדות ביכולות החדשות לגילוי ושמירת שינויי גיאומטריה במסד נתונים."
weight: 80
---
# עדכוני Aspose.GIS: עריכת תכונות וגיאומטריות ושמירת השינויים במסד הנתונים.

## מבוא

לאור השינויים האחרונים בספריית [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis), חשוב להדגיש חלק מהם כדי שלא יעברו בלי שימת לב. במאמר זה, נדון ביכולת החדשה לגילוי ושמירת שינויים בגיאומטריות ותכונות במסד הנתונים.

כדוגמה להדגמה, נמשיך לעבוד על היישום המתואר במאמר ["צייר מפה. מפה גולשת עם אריחים"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) ונרחיב אותו מעט על ידי הוספת פונקציות עריכת עצמים במפה. ערכת הנתונים נשארת זהה כמו במאמר הקודם.

## חזית

להדגמת יכולות שינוי הגיאומטריה, בחרנו בהרחבה פופולרית בקוד פתוח עבור [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/).

אנו מוסיפים ספרייה זו באמצעות קובץ libman.json:
![Libman](libman.png)

לאחר מכן, אנו מחברים את הסגנונות והסקריפטים לדף:
```razor
@section Styles {
    <link href="~/lib/leaflet/leaflet.min.css" rel="stylesheet" />
    <link href="~/lib/contagt/leaflet-geoman-free/dist/leaflet-geoman.min.css" rel="stylesheet" />
    <link href="~/css/map.css" rel="stylesheet" asp-append-version="true"/>
}

@section Scripts {
    <script src="~/lib/leaflet/leaflet.js"></script>
    <script src="~/lib/contagt/leaflet-geoman-free/dist/leaflet-geoman.min.js"></script>
    <script src="~/js/map.js" asp-append-version="true"></script>
}
```

למטרות הדגמה, נגביל את יכולות העריכה לבניינים בלבד. המשתמש לוחץ על כפתור העכבר השמאלי במפה, ואם יש בניין במיקום זה, הוא מסומן והופך זמין לעריכה. זה מושג על ידי הנחת שכבה נוספת מעל האריחים.

כאשר המשתמש לוחץ על המפה, ספריית Leaflet מחשבת את הקואורדינטות הגיאו-מרחביות של הלחיצה. אנו שולחים קואורדינטות אלה לחלק האחורי ומחפשים במסד הנתונים גיאומטריות החוצות את הנקודה הלחוצה. אם יש בניינים בין הגיאומטריות האלה, אנחנו מחזירים אותם.

הבניינים מוחזרים מהחלק האחורי בפורמט `GeoJSON` ומוספים למפה כשכבה נפרדת לעריכה. כך אנו מטפלים בלחיצה:
```javascript
var featuresLayer = L.featureGroup().addTo(map);

map.on('click', function (e) {
    var latlng = e.latlng;
    var featureFound = false;

    console.log(latlng.lat + ' ' + latlng.lng);

    featuresLayer.eachLayer(function (layer) {
        if (layer.getBounds && layer.getBounds().contains(latlng)) {
            featureFound = true;
            return;
        }
    });

    if (!featureFound) {
        loadGeoJSON(latlng.lat, latlng.lng)
            .then((addedFeatureLayer) => {
                if (addedFeatureLayer) {
                    addedFeatureLayer.addTo(featuresLayer);
                    addedFeatureLayer.pm.enable();
                    console.log('Feature added.');
                } else {
                    console.log('No feature to add.');
                }
            });
    }

    featureFound = false;
});
```

יש לנו קבוצת שכבות קבועה לגיאומטריות ניתנות לעריכה, `featuresLayer`, אשר נוספה למפה. אנו בודקים אם הלחיצה נעשתה על גיאומטריה טעונה כבר, ואם לא, אנו מבצעים בקשה לחלק האחורי כדי לטעון את הפוליגונים המייצגים בניינים. שכבות התכונות הטעונות מתווספות ל-featuresLayer, ומצב העריכה מופעל.

הנה איך נראה הפונקציה לטעינת תכונות והמרת מ- `GeoJSON`:
```javascript
function loadGeoJSON(lat, lng) {
    return fetch(`/features?lat=${lat}&lng=${lng}`)
        .then(response => response.json())
        .then(data => {
            if (data && data.features && data.features.length > 0) {
                return L.geoJSON(data);

            } else {
                return null;
            }
        })
        .catch(error => console.error('Error loading a feature:', error));
}
```

לאחר סיום העריכה, המשתמש לוחץ על כפתור `שמור` מותאם אישית:

![Save](save-btn.png)

רענן את הדף וראה את השינויים:

![Changes](changes.png)

למרבה הצער, הפונקציה `tiles.redraw()` לא עובדת כראוי מכיוון שאריחים טעונים בעבר מטופלים במטמון, מה שמחייב רענון בכוח של המפה באמצעות `Ctrl + F5`.

זהו הטיפול בלחיצה על כפתור השמירה:
```javascript
function saveResult() {
    if (featuresLayer.getLayers().length === 0) {
        console.log('There are no layers to send to the server.');
        return;
    }
    sendGeoJSONToServer()
        .then(() => {
            console.log('clear and update map');
            featuresLayer.clearLayers();
            tiles.redraw();
        });
}

function sendGeoJSONToServer() {
    var geojsonData = featuresLayer.toGeoJSON();

    return fetch('/features', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/geo+json'
        },
        body: JSON.stringify(geojsonData)
    })
        .then(data => {
            console.log('The data has been successfully sent to the server.');
        })
        .catch(error => {
            console.error('Error when sending GeoJSON:', error);
        });
}
```

## חלק אחורי

כאן אנו מוסיפים בקר חדש, `FeaturesController`, שבו אנו יוצרים מטפל לחילוץ בתים/תכונות לפי הקואורדינטות שנשלחו.

בקשת ה-SQL נראית כך:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

הקואורדינטות מומרות לנקודה, המציינת את מערכת הקואורדינטות של הבקשה המקורית של הלקוח (WGS 84), ואז מתורגמות למערכת שבה מוצגים נתוני מסד הנתונים (Web Mercator). אנו מחפשים חיתוכים עם נקודה זו עבור גיאומטריות המסומנות כבניינים.

ביצוע הבקשה ושליחת נתונים ללקוח מתרחש באופן דומה למה שדיון במאמר הקודם:
```csharp
VectorLayer inputLayer;

using (var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary"))
{
    var dataSource = Drivers.PostGis
        .FromQuery(query)
        .GeometryField("way")
        .AddAttribute("osm_id", AttributeDataType.Long)
        .AddAttribute("name", AttributeDataType.String)
        .AddAttribute("building", AttributeDataType.String)
        .Build();

    conn.Open();

    inputLayer = await dataSource.ReadAsync(conn);
}

var jsonStream = new MemoryStream();

inputLayer.SaveTo(AbstractPath.FromStream(jsonStream), Drivers.GeoJson);

var result = Encoding.UTF8.GetString(jsonStream.ToArray());

return new ContentResult()
{
    Content = result,
    ContentType = "application/geo+json"
};
```
עם הבדל קטן: אנו שומרים את השכבה שלנו בזיכרון כ-GeoJSON בזיכרון כזרם, ואז ממירים אותו למחרוזת ושולחים אותו ללקוח.

עכשיו אנחנו מגיעים לעיקרי העדכונים ב-Aspose.GIS — שמירת שינויים במסד הנתונים. השיטה `Edit()` מטפלת בכך. אנו קוראים את גוף הבקשה כדי לטעון אותו כולו בזיכרון וקוראים אותו כזרם:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync();
Request.Body.Position = 0;
```
לאחר מכן, אנו קוראים את התכונות הנערכות בפורמט GeoJSON:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
השלב הבא, מהסט שנשלח של תכונות, אנו מחלצים את התכונות המייצגות מזהים ייחודיים של התכונות המתאימות במסד הנתונים. אנו יוצרים בקשה לאכלוס שכבה מיוחדת לעריכה ובונים את מקור הנתונים המתאים:
```csharp
var ids = string.Join(", ", inputLayer.Select(x => x.GetValue<long>("osm_id")));

var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
               FROM public.planet_osm_polygon
               WHERE osm_id IN ({ids});";

var dataSource = Drivers.PostGis
    .FromQuery(query)
    .GeometryField("way")
    .AddAttribute("osm_id", AttributeDataType.Integer, System.Data.DbType.Int64)
    .AddAttribute("name", AttributeDataType.String)
    .AddAttribute("building", AttributeDataType.String)
    .AsTrackableForChanges("public.planet_osm_polygon", "osm_id", true)
    .Build();
```
שימו לב לשיטת התצורה `AsTrackableForChanges`. זוהי שיטה מיוחדת המציינת את הצורך ליצור מקור נתונים ספציפי המסוגל לעקוב אחר שינויים. הפרמטר הראשון מציין את הטבלה שאליה יש לשלוח בקשות לשינוי. השנייה מציינת איזה תכונה תיחשב למזהה לביצוע שינויים במסד הנתונים. החלק המעניין ביותר הוא הפרמטר השלישי. כאשר מוגדר כ-True, הוא מציין שהשכבה תעקוב אחר הופעתם של כפילויות לפי הפרמטר השני ות"תדרוס" תכונות טעונות קודמות עם חדשות. עם זאת, במקרה של תוצאות עריכה, כלומר הוספת תכונה חדשה עם אותו מזהה, פקודת `UPDATE` תיצור בהתאם לשינויים בהשוואה לערך הישן. אם הפרמטר השלישי מוגדר כ-false, חריגה תושלך בעת הופעת כפילויות, בין אם במהלך האתחול או העריכה.

שמות התכונות ישמשו כשמות שדות בטבלה הניתנת לעריכה. חשוב לציין נקודה מכרעת לגבי גילוי השינויים. חיוני לציין את סוג הנתונים המדויק של התכונה שתאוחסן בשכבה למעקב אחר שינויים, הוא חייב להיות מדויק בהתאם לסוגים שנוספו או שונו לאחרונה. לדוגמה, אם אנו מוסיפים תכונה חדשה עם `osm_id` מסוג `Int32`, בעוד שסוג התכונה המצוין בשכבה הוא `Int64`, זה יטופל כערכים שונים מכיוון שאין עומס של השיטה `Equal`s שנראית כמו `Int64.Equals(Int32)`. בגרסאות עתידיות, התנהגות זו תיבדק ותתוקן במידת האפשר. סוג הפרמטר השלישי יוחל במהלך שמירת הנתונים כסוג המטרה של טבלת מסד הנתונים.

לאחר מכן, אנו מתחברים למסד הנתונים וקוראים נתונים מהטבלה:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
נקודה חשובה היא שלכדי עבודה נכונה של העסקה ברמת מסד הנתונים, יש להעביר את העסקה הנוכחית כפרמטר השני במהלך פעולת הקריאה.

לאחר מכן, אנו צריכים לבצע סדרת טרנספורמציות לפני שליחת השינויים למסד הנתונים:
```csharp
var transformer = SpatialReferenceSystem.Wgs84.CreateTransformationTo(SpatialReferenceSystem.WebMercator);

foreach (var feature in inputLayer)
{
    feature.Geometry = transformer.Transform(feature.Geometry);
    ((Geometry)feature.Geometry).HasZ = false;
}

foreach (var feature in inputLayer)
{
    var replacingId = feature.GetValue<long>("osm_id");
    var toReplaceIndex = editLayer.TakeWhile(x => x.GetValue<long>("osm_id") != replacingId).Count();
    editLayer.ReplaceAt(toReplaceIndex, feature);
}

await dataSource.SubmitChangesAsync(editLayer, conn, transaction);

transaction.Commit();
```
Leaflet יוצר גיאומטריות במערכת הקואורדינטות WGS 84, עם זאת, סכימת מסד הנתונים דורשת אחסון ב-Web Mercator. כדי להמיר למערכת Web Mercator, אנו יוצרים אובייקט `transformer` מיוחד ומשתמשים בו לטרנספורמציה.

בנוסף, leaflet ממלא את הפרמטר השלישי של קואורדינטות הגיאומטריה Z בערך של 0. עם זאת, פרמטר זה אינו נחשב בסכימת מסד הנתונים שלנו, אז אנו מסירים את נוכחותו על ידי הגדרת הערך של `HasZ` ל-false.

הנקודה הסופית היא החלת שינויים על ידי החלפת התכונה הקיימת בחדשה שהתקבלה מהלקוח שיש לה אותו osm_id. פעולה זו תוביל לגילוי השינויים ביחס למקרים הישנים של התכונה. ברגע שנקרא `SubmitChangesAsync`, תהליך גילוי השינויים יתרחש, והפקודות INSERT, DELETE ו-UPDATE יישלחו למסד הנתונים בהתאם לשינויים שלך.

תודה שקראת עד הסוף. כל הקוד יהיה זמין במאגר הבא: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)
---