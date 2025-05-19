---
title: עיבוד מפות לתמונה SVG, PNG, JPG באמצעות ספריית GIS C#
linktitle: "עיבוד מפות"
type: docs
url: /he/net/map-rendering/
weight: 50
description: עם API של GIS C#, אתה יכול לעבד מפה מקובץ Shapefile, FileGDB, GeoJSON, KML, לבצע עיצוב מתקדם ולצייר מפה מפורמטים רסטר.
---

## **סקירת עיבוד מפות**
עם Aspose.GIS עבור API של .NET C# אתה יכול לעבד מפה מקובץ Shapefile, FileGDB, GeoJSON, KML או פורמטים תומכים אחרים [/gis/net/supported-file-formats/] ל-SVG, PNG, JPEG או BMP.

הנה קוד C# המדגים כיצד לעבד מפה מקובץ shapefile ל-SVG באמצעות הגדרות ברירת מחדל:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



הנה התוצאה:



![עיבוד מפות](map_rendering.png)

בואו נסתכל מקרוב על הקוד.

ראשית, אנו יוצרים מופע של אובייקט [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map). הוא מייצג אוסף שכבות ממקורות שונים שניתן לעבד. למפה יש גודל שהיא אמורה להיות מוצגת בו. כאן אנו מגדירים את המפה לרוחב של 800 פיקסלים וגובה של 400 פיקסלים.

שימו לב שהמפה כלולה בהצהרת using. זה הכרחי מכיוון שהמפה עוקבת אחר כל המשאבים שנוספו אליה, ומפנה אותם כאשר סיימנו עם העיבוד ואובייקט המפה מפונה.

לאחר מכן, אנו מוסיפים שכבה מקובץ למפה. כל שכבה מעובדת על גבי השכבה הקודמת, בסדר שבו הן נוספו למפה. ראה פרטים נוספים כיצד לפתוח שכבות וקטוריות [כאן](/gis/net/working-with-vector-layers/).

לבסוף, אנו קוראים ל-[Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) כדי לעבד את המפה לקובץ. אנו מציינים נתיב לשמירת קובץ התוצאה ומעבד לשימוש. מחלקת [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) מכילה הפניות לכל המעבדים הכלולים ב-Aspose.GIS. לדוגמה, אתה יכול לציין Renderers.Png במקום Renderers.Svg בדוגמה לעיל כדי לעבד את המפה לקובץ PNG

## **עיצוב מתקדם**
עם Aspose.GIS API, אתה יכול להתאים אישית עיבוד וסגנונות תכונות כדי להשיג את המראה הרצוי.

![עיצוב מתקדם](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **צייר רסטר במפה**
עם Aspose.GIS עבור .NET אתה יכול לעבד מפה מפורמטים של רסטר.
### **עיבוד עם הגדרות ברירת מחדל**
הנה איך לעבד מפה מ-GeoTIFF ל-SVG באמצעות הגדרות ברירת מחדל:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![רסטר ברירת מחדל](default_raster.png)
### **עיבוד רסטרים עקומים**
עם Aspose.GIS אתה יכול לעבד רסטר עם תאי רסטר עקומים.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![רסטר עקום](skew_raster.png)
### **עיבוד בהפניית מרחב קוטבית**
Aspose.GIS מאפשר לך להשתמש בהפניות מרחב קוטביות בתהליך עיבוד מפות.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![מדינות גנומוניות](gnomonic_countries.png)
