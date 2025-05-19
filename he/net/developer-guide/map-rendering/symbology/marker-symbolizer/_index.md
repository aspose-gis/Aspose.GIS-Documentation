---
title: "סמל מסמן"
type: docs
url: /he/net/marker-symbolizer/
weight: 10
description: ספריית GIS C# או API תומכת בסמל מסמן פשוט שמצייר צורה מוגדרת מראש עם מילוי וקו מתאר הניתנים להתאמה אישית על גיאומטריות של כל סוג כמו נקודה, קו, משטח.
---

## **סמל מסמן**
סמל המסמן הפשוט מצייר צורה מוגדרת מראש עם מילוי וקו מתאר הניתנים להתאמה אישית. זהו הסמל המוגדר כברירת מחדל לגיאומטריות ממדי 0 (נקודות).

הצורות הנתמכות הן:

|![todo:image_alt_text](marker-symbolizer_1.png)|מעגל| |![todo:image_alt_text](marker-symbolizer_2.png)|כוכב|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|ריבוע| |![todo:image_alt_text](marker-symbolizer_4.png)|צלב|
|![todo:image_alt_text](marker-symbolizer_5.png)|משולש| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

אפשרויות עיצוב נתמכות:

|**מאפיין**|**תיאור**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|מציין את הצורה של המסמן.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|מציין את גודל צורת המסמן|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|מציין את הצבע והשקיפות הניתנים למילוי|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|מציין את הצבע והשקיפות הניתנים לקו|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|מציין את רוחב הקו|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|קובע כיצד קווים מעובדים בצמתים של מקטעי קו.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|מציין כיצד יש לצייר את העבודה הקווית של הסמל.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|מציין מערך של מרחקים שמציין את אורכי המקפים והרווחים המתחלפים בקווים מקווקווים.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|מציין את המרחק מתחילת הקו לתחילת דפוס המקף.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|מציין את הסיבוב של הסמל סביב נקודת המרכז שלו, במעלות עשרוניות. ערכים חיוביים מציינים סיבוב בכיוון השעון, ערכים שליליים מציינים סיבוב נגד כיוון השעון. ברירת המחדל היא 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|מציין קיזוז אופקי ממיקום נקודה לעיגון הצורה.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|מציין קיזוז אנכי ממיקום נקודה לנקודת העיגון של הצורה.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|מציין איזה צד של צורת מסמן ייושר אופקית עם מיקום הנקודה.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|מציין איזה צד של צורת מסמן ייושר אנכית עם מיקום הנקודה.|

### **סוגי גיאומטריה**
` `המסמל יכול להיות מיושם על גיאומטריות של כל סוג.

|**ממד גיאומטריה**|**סוגי גיאומטריה**|**התנהגות עיבוד**|
| :-: | :-: | :-: |
|**נקודה**|נקודה, MultiPoint|מצייר את הצורה במרכז קואורדינטת הנקודה.|
|**קו**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>מצייר את הצורה במרכז הכובד של הגיאומטריה</p><p> </p>|
|**משטח**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

עבור GeometryCollections, התנהגות העיבוד נקבעת בנפרד עבור כל גיאומטריה בתוך האוסף. שכבות עם סוג גיאומטריה מעורב עוקבות אחר ההיגיון עבור GeometryCollections.

השתמש ב-MixedGeometrySymbolizer כדי להגביל מסמל לסוגי גיאומטריה ספציפיים.

### **דוגמאות**
כברירת מחדל, המסמל מצייר עיגולים שחורים:



כאן איך לשנות את צבע המילוי לאדום:




|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

דוגמה נוספת לעיצוב עם צורה מוגדרת מראש (משולש):




|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----

עבור תרחישים מתקדמים יותר, ייתכן שתרצה להתאים את סגנון המסמן באופן דינמי בהתבסס על ערכי התכונות של הפיצ'ר. כך איך לעשות זאת:




|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
ייתכן שתרצה גם להוסיף תוויות למסמנים שלך. בקר ב[דוגמאות תיוג נקודות](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) לדוגמאות.
