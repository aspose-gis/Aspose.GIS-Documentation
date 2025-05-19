---
title: "זרמים ואחסון מרוחק"
type: docs
url: /he/net/streams-and-remote-storage/
weight: 70
---

## **עבודה עם פורמטים רב-קובציים**
חלק מפורמטי הנתונים של GIS מפצלים תוכן למספר קבצים. לדוגמה, לקובץ shapefile חייבים להיות לפחות שלושה קבצים: *.shp, *.shx ו-*.dbf. פורמטים אלה דורשים שכל הקבצים יאוחסנו במבנה ספריות מסוים עם תבנית מוגדרת מראש לשמות הקבצים.

באותו זמן, הקבצים עשויים להיות מאוחסנים בשרת מרוחק או מיקום אחר הנגיש באמצעות זרמים בלבד. לזרמים חסרה מידע על שמות קבצים ומבנה ספריות, מה שמקשה על מנהלי פורמט הקבצים לקבוע כיצד לעבד נתונים. Aspose.GIS פותר זאת על ידי מתן המנגנון של נתיבים מופשטים.

נתיב מופשט מייצג נתיב לקובץ (או ספריה) באחסון דמוי מערכת קבצים כלשהי. האחסון יכול להיות כל דבר שיש לו מושג של הקובץ והספרייה, מארכיון לשרת FTP. הוא מגדיר כיצד לבצע פעולות קבצים טיפוסיות, כגון פתיחת קובץ או רישום ספריה.

תוכל לציין כיצד לבצע פעולות קבצים עבור האחסון שלך על ידי יישום מחלקה שיורשת מ-[AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) ומתן יישומים לשיטות המופשטות שלה.
## **הדגמה: אחסון Azure Blob**
מאגר Aspose.GIS Examples מכיל דוגמה ליישום פונקציונלי מלא של נתיב מופשט מותאם אישית עבור אחסון Azure Blob. ההדגמה הזו מראה כיצד לקרוא קובץ shapefile ישירות מאחסון Azure Blob. תוכל למצוא אותו כאן: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **פורמטים חד-קובציים (GeoJSON, KML)**
פורמטי נתונים של GIS כמו GeoJSON ו-KML יכולים לאחסן את כל הנתונים עבור שכבה בקובץ אחד. אם אתה יכול לקבל זרם עבור הקובץ, תוכל לדלג על יישום נתיב מופשט מותאם אישית ולהשתמש בשיטה [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) כדי ליצור מופע של נתיב מופשט עבור הזרם.
### **קריאת קובץ מתוך זרם**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **כתיבת קובץ לזרם**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
