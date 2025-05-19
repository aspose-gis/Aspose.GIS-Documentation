---
title: "מילוי סמל"
type: docs
url: /he/net/fill-symbolizer/
weight: 30
description: ספריית GIS C# API תומכת בסמל מילוי פשוט כדי למלא סגנון וקו עבור גיאומטריות דו-ממדיות מצולעים של כל סוג כמו נקודה, קו, משטח.
---

## **סמל מילוי**
סמל המילוי הפשוט ממלא אזור בסגנון מילוי וקו הניתנים להתאמה אישית. זהו הסמל המוגדר כברירת מחדל עבור גיאומטריות דו-ממדיות (מצולעים).

אם למצולע יש "חורים", הם לא מתמלאים, אך הגבולות סביב החורים מסומנים בדרך הרגילה. "איים" בתוך חורים מלאים ומסומנים, וכן הלאה.

אפשרויות עיצוב נתמכות:

|**מאפיין**|**תיאור**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|מציין את הצבע והשקיפות הניתנים למילוי.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- מוצק - מילוי מוצק</p><p>- אין - אל תמלאו את המצולע</p><p>- קו אופקי - דפוס של קווים אופקיים.</p><p>- קו אנכי - דפוס של קווים אנכיים.</p><p>- קו צלב - מציין קווים אופקיים ואנכיים שחוצים.</p><p>- קו אלכסוני קדמי - דפוס של קווים באלכסון משמאל למעלה לימין תחתונה.</p><p>- קו אלכסוני אחורי - דפוס של קווים באלכסון מימין למעלה לשמאל תחתונה.</p><p>- קו צלב אלכסוני - דפוס של קווים אלכסוניים מצטלבים.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|מציין את הצבע והשקיפות הניתנים לקו המסומן.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|מציין כיצד יש לצייר את קווי הסמל.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|מציין את רוחב הקו המסומן.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|מציין מערך של מרחקים המציין את אורכי הריצות והרווחים המתחלפים בקווים מקווקווים.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|מציין את המרחק מתחילת הקו לתחילת דפוס הריצה.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>קובע כיצד קווים מעובדים בצמתים של מקטעי קו.</p><p>- Miter - פינה חדה</p><p>- Round - פינה מעוגלת</p><p>- Bevel - פינה אלכסונית</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|מציין קיזוז אופקי ממיקום נקודה לעיגון הצורה.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|מציין קיזוז אנכי ממיקום נקודה לנקודת העיגון של הצורה.|

### **סוגי גיאומטריה**
` `הסמל יכול להיות מיושם על גיאומטריות של כל סוג.

|**מימד גיאומטריה**|**סוגי גיאומטריה**|**התנהגות עיצוב**|
| :-: | :-: | :-: |
|**נקודה**|נקודה, MultiPoint|מצייר ריבוע קטן אורתוגונלי.|
|**קו**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|הקו סגור למילוי על ידי חיבור נקודת הסיום לנקודת ההתחלה שלו. רק הקו המקורי מסומן.|
|**משטח**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|מצייר את המצולע.|

עבור GeometryCollections, התנהגות העיצוב נקבעת בנפרד עבור כל גיאומטריה בתוך האוסף. שכבות עם סוג גיאומטריה מעורב עוקבות אחר ההיגיון עבור GeometryCollections.

השתמשו ב-MixedGeometrySymbolizer כדי להגביל את הסמל לסוגי גיאומטריה ספציפיים.

### **דוגמאות**
כברירת מחדל, סמל המילוי הפשוט מצייר קו מסומן שחור ומילוי לבן מוצק:



כאן איך לשנות עיצוב:




|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

-----
ייתכן שתרצו גם להוסיף תוויות למצולעים שלכם. בקרו ב-[דוגמאות תיוג קווים](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) לדוגמאות כיצד לתייג גבולות מצולעים או [דוגמאות תיוג נקודות](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) בדוגמאות כיצד לתייג מרכזי מצולעים.
