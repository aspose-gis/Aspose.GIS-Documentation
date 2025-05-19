---
title: סמבולוגיה - API של C# GIS
linktitle: "סמבולוגיה"
type: docs
url: /he/symbology/
weight: 10
description: ספריית או API של GIS C# תומכת בסמבוליזטורים לציור גיאומטריית פיצ'רים כמו סמן, קו, מילוי ושילוב סמבוליזטורים ליצירת ויזואליזציות מורכבות יותר.
---

סמבוליזטור הוא דרך לצייר גיאומטריית פיצ'ר על מפה.

|** **|**סמבוליזטור**|**מחלקת API**|**תיאור**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**סמן**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|מצייר צורה מוגדרת מראש עם מילוי וקו מתכווננים. |
|![todo:image_alt_text](symbology_2.png)|**קו**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|מצייר קו עם עיצוב מתכוונן.|
|![todo:image_alt_text](symbology_3.png)|**מילוי**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|ממלא מצולע או שטח התחום על ידי קו עם מילוי וקו מתכווננים.|
בנוסף לסמבוליזטורים שעורכים ציור בפועל, יש מספר סמבוליזטורים אחרים המאפשרים לשלב סמבוליזטורים אחרים ליצירת ויזואליזציות מורכבות יותר.

|**סמבוליזטור**|**מחלקת API**|**תיאור**|
| :- | :- | :- |
|**סמבוליזטור שכבה**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|מצייר פיצ'ר עם מספר סמבוליזטורים אחד על השני|
|**סמבוליזטור גיאומטריה מעורבת**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|מצייר פיצ'רים משכבות המכילות גיאומטריות מסוגים מעורבים עם סמבוליזטור ספציפי לכל סוג גיאומטריה|
|**סמבוליזטור מבוסס כללים**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|בוחר סמבוליזטור ליישום על פיצ'ר לפי כללים שצוינו על ידי המשתמש.|
|**סמבוליזטור אשכול סמנים**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|מצייר קיבוץ של סמנים, קיבוץ של פריטים אלה.|
|**סמבוליזטור מחולל גיאומטריה**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|מאפשר להחליף את הגיאומטרייה של הפיצ'ר לפני העיבוד.|
|**סמבוליזטור Null**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|לא מצייר כלום. שימושי בשילוב עם סמבוליזטורים אחרים, כגון הסמבוליזטור מבוסס הכללים.|
