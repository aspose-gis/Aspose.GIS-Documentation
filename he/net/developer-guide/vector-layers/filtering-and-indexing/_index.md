---
title: סינון ואינדוקס של שכבות וקטוריות GIS ב-#C
linktitle: סינון ואינדוקס
second_title: Aspose.GIS עבור .NET
type: docs
url: /he/filtering-and-indexing/
weight: 30
description: עם ספריית או API של GIS C#‎ .NET, תוכלו לסנן שכבות וקטוריות GIS לפי ערכי תכונות או גבולות מרחביים. ניתן גם להשתמש באינדקסים כדי להאיץ סינון ושאלתות מרחביות.
---

עם Aspose.GIS עבור .NET תוכלו לסנן שכבות לפי ערכי תכונות או גבולות מרחביים. ניתן גם להשתמש באינדקסים כדי להאיץ סינון ושאלתות מרחביות.
## **אינדקס תכונות**
### **סינון ללא אינדקס**
הנה איך לסנן שכבה לפי ערכים של תכונה:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **סינון עם אינדקס**
הקוד למעלה בסדר כל עוד השכבה מסוננת רק פעם אחת. אבל, אם סביר להניח שהשכבה תיבדק מספר פעמים, נוכל להרוויח מאינדקסים של תכונות. לוקח קצת זמן לבנות אינדקס תכונות, אך ניתן להשתמש בו שוב ושוב כדי להאיץ את הסינון.

הדוגמה הבאה משתמשת בקובץ אינדקס תכונות כדי להאיץ סינון שכבה לפי ערכים של התכונה:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **שמירת תכונות מסוננות**
ניתן לשמור תכונות מסוננות לתוך שכבות:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **עיבוד תכונות מסוננות**
ניתן גם לעבד תכונות מסוננות. הדוגמאות הבאות משתמשות באינדקס תכונות כדי לבחור במהירות את כל התכונות עם אוכלוסייה גדולה מ-2000 ולהוסיף אותן למפה:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **אינדקס מרחבי**
אינדקסים מרחביים משמשים להאצת שאילתות מרחביות. בדיוק כמו אינדקסים של תכונות, אינדקסים מרחביים בשימוש חוזר לאחר יצירתם.
### **מציאת תכונות הקרובות ביותר לנקודה**
הנה איך להשתמש באינדקס מרחבי כדי להאיץ את החיפוש אחר התכונה הקרובה ביותר לנקודה מסוימת:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **בחירת תכונות החוצות גיאומטריה**
הדוגמאות הבאות משתמשות באינדקס מרחבי כדי להאיץ את בחירת התכונות שחוצות גיאומטריה:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
