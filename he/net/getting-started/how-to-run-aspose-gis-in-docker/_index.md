---
title: איך להריץ את Aspose.GIS ב-Docker
type: docs
description: "הרץ את Aspose.GIS במכולת Docker עבור Linux, Windows Server וכל מערכת הפעלה."
weight: 139
url: /he/net/how-to-run-aspose-gis-in-docker/
---

## דרישות מוקדמות

- Docker חייב להיות מותקן במערכת שלך. לקבלת מידע כיצד להתקין את Docker ב-Windows או Mac, עיין בקישורים בסעיף "ראה גם".

- Visual Studio 2022.

- NET Core 3.1 SDK נמצא בשימוש בדוגמה.


## יישום Hello World

בדוגמה זו, אתה יוצר יישום קונסולה פשוט של Hello World שיוצר עקומת מורכבת ושומר אותה בקבצים. לאחר מכן ניתן לבנות ולהפעיל את היישום ב-Docker.

### יצירת יישום הקונסולה

כדי ליצור את תוכנית ה-Hello World, בצע את השלבים הבאים:
1. לאחר התקנת Docker, ודא שהוא משתמש במכולות Linux (ברירת מחדל). אם יש צורך, בחר באפשרות Switch to Linux containers מתפריט שולחן העבודה של Docker.
1. ב-Visual Studio, צור יישום קונסולה NET Core 3.1.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. התקן את הגרסה האחרונה של Aspose.GIS מ-NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. מכיוון שהיישום יופעל ב-Linux, יש להתקין את הנכסים הלילדיים המתאימים של Linux. התחל עם תמונת הבסיס של dotnet core sdk 3.1 והתקן libgdiplus libc6-dev.
1. כאשר כל התלות הדרושה נוספה, כתוב תוכנית פשוטה שיוצרת עקומת מורכבת:<br>
**.NET**<br>
{{< highlight csharp >}}
using System.IO;
using Aspose.Gis.Geometries;
using Aspose.Gis;

namespace Aspose.GIS.Docker.Sample
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string path = Path.Combine("TestOut", "CreateCompoundCurve_out.shp");
            using (VectorLayer layer = VectorLayer.Create(path, Drivers.Shapefile))
            {
                var feature = layer.ConstructFeature();
                // create an 'S' letter (starts at bottom left end)
                var compoundCurve = new CompoundCurve();

                var bottom = (ILineString)Geometry.FromText("LineString (0 0, 3 0)");
                var firstArc = (ICircularString)Geometry.FromText("CircularString (3 0, 4 1, 3 2)");
                var middle = (ILineString)Geometry.FromText("LineString (3 2, 1 2)");
                var secondArc = (ICircularString)Geometry.FromText("CircularString (1 2, 0 3, 1 4)");
                var top = (ILineString)Geometry.FromText("LineString (1 4, 4 4)");

                compoundCurve.AddCurve(bottom);
                compoundCurve.AddCurve(firstArc);
                compoundCurve.AddCurve(middle);
                compoundCurve.AddCurve(secondArc);
                compoundCurve.AddCurve(top);
                feature.Geometry = compoundCurve;

                layer.Add(feature);
            }
        }
    }
}
{{< /highlight >}}

שימו לב שהתיקייה �TestOut� מצוינת כתיקיית פלט לשמירת מסמכי הפלט. בעת הרצת היישום ב-Docker, תיקייה במכונה המארחת תותאם לתיקייה זו במכולה. זה יאפשר לך לצפות בקלות בפלט שנוצר על ידי Aspose.GIS במכולת Docker.

### הגדרת קובץ Dockerfile

השלב הבא הוא ליצור ולהגדיר את קובץ ה-Dockerfile.

1. צור את קובץ ה-Dockerfile והנח אותו לצד קובץ הפתרון של היישום שלך. שמור שם קובץ זה ללא סיומת (ברירת המחדל).
1. בקובץ ה-Dockerfile, ציין:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

האמור לעיל הוא קובץ Dockerfile פשוט, המכיל את ההוראות הבאות:

- תמונת ה-SDK שיש להשתמש בה. כאן זהו התמונה Net 3.1. Docker יוריד אותה כאשר הבנייה תרוץ. מצוין גרסת SDK כתגית.
- ספריית העבודה, המצוינת בשורה הבאה.
- הפקודה להתקנת libgdiplus מופעלת במכולה. זה נדרש על ידי System.Drawing.Common.
- הפקודה להעתקת הכל למכולה, פרסום היישום וציון נקודת הכניסה.

### בנייה והרצת היישום ב-Docker

כעת ניתן לבנות ולהפעיל את היישום ב-Docker. פתח את שורת הפקודה המועדפת עליך, שנה ספריה לתיקייה עם היישום (תיקייה שבה נמצא קובץ הפתרון וקובץ ה-Dockerfile) והפעל את הפקודה הבאה:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

בזמן הפעלה הראשונה של פקודה זו, היא עשויה לקחת זמן רב יותר, מכיוון ש-Docker צריך להוריד את התמונות הנדרשות. לאחר השלמת הפקודה הקודמת, הפעל את הפקודה הבאה:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

שימו לב לטיעון ההרכבה, מכיוון שכפי שהוזכר קודם לכן, תיקייה במכונה המארחת מותאמת לתיקיית המכולה, כדי לראות בקלות את תוצאות ביצוע היישום. נתיבים ב-Linux רגישים לאותיות רישיות וקטנות.

{{% /alert %}}


## דוגמאות נוספות

לדוגמאות נוספות כיצד ניתן להשתמש ב-Aspose.GIS ב-Docker, ראה את [הדוגמאות](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## ראה גם

- [התקן Docker Desktop ב-Windows](https://docs.docker.com/docker-for-windows/install/)
- [התקן Docker Desktop ב-Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- [Switch to Linux containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) אפשרות
- מידע נוסף על [.NET Core SDK](https://hub.docker.com/_/microsoft-dotnet-sdk)
