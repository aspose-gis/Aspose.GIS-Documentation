---
title: "סמל קו"
type: docs
url: /he/net/line-symbolizer/
weight: 20
description: ספריית GIS C# או API תומכת בסמל קו פשוט עבור גיאומטריות חד מימדיות של קווים, וניתן ליישם אותה על גיאומטריות מכל סוג כמו נקודה, קו, משטח.
---

## **סמל קו**
סמל הקו הפשוט מצייר קו עם סגנון הניתן להתאמה אישית. זהו הסמל המוגדר כברירת מחדל עבור גיאומטריות חד מימדיות (קווים). 

אפשרויות עיצוב נתמכות:

|**מאפיין**|**תיאור**|
| :- | :- |
|[Color](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|מציין את הצבע והשקיפות הניתנים לקו.|
|[Width](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|מציין את רוחב הקו|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|קובע כיצד קווים מוצגים בצמתים של מקטעי קו.|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|מציין כיצד יש לצייר את העבודה הקווית של הסמל.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|מציין מערך של מרחקים המציין את אורכי הריווחים המתחלפים והרווחים בקווים מקווקווים.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|מציין את המרחק מתחילת הקו לתחילת תבנית הריווח.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>מציין כיצד קווים מוצגים בקצותיהם.</p><p>- Butt - קצה מרובע חד</p><p>- Round - קצה מעוגל</p><p>- Square - קצה מרובע מעט מוארך</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|מציין את ההסטה מהקו המקורי. עבור מרחק חיובי, ההסטה תהיה בצד שמאל של הקו (ביחס לכיוון הקו). עבור מרחק שלילי היא תהיה בצד ימין.|

### **סוגי גיאומטריה**
` `ניתן ליישם את הסמל על גיאומטריות מכל סוג.

|**מימד גיאומטריה**|**סוגי גיאומטריה**|**התנהגות עיבוד**|
| :-: | :-: | :-: |
|**נקודה**|נקודה, MultiPoint|מצייר קו באורך קטן עם כיוון אופקי המרוכז על הנקודה, עם שני מכסים.|
|**קו**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|מצייר את הקו.|
|**משטח**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|המתאר הסגור של הגיאומטריה משמש כקו (ללא מכסים)|

עבור GeometryCollections, התנהגות העיבוד נקבעת בנפרד עבור כל גיאומטריה בתוך האוסף. שכבות עם סוג גיאומטריה מעורב עוקבות אחר ההיגיון עבור GeometryCollections.

השתמש ב-MixedGeometrySymbolizer כדי להגביל את הסמל לסוגי גיאומטריה ספציפיים.

### **דוגמאות**
כברירת מחדל, סמל הקו מצייר קווים שחורים:



כאן כיצד לשנות את צבע הקו לכחול:




|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

-----

עבור תרחישים מתקדמים יותר, ייתכן שתרצה להתאים את סגנון הקו באופן דינמי בהתבסס על ערכי התכונות של הפיצ'ר. כך איך לעשות זאת:




|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |



-----

ייתכן שתרצה גם להוסיף תוויות לקווים שלך. בקר ב-[דוגמאות תיוג קווים](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) לקבלת דוגמאות.
