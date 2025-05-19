---
title: "בנאי גיאומטריה"
type: docs
url: /he/geometry-constructors/
weight: 5
description: ניתן לעבוד עם גיאומטריית נקודה, גיאומטריית מחרוזת קו, גיאומטריית מצולע ולבנות אוספי גיאומטריה באמצעות ספריית GIS C#.
---

## **גיאומטריית נקודה**
### **צור נקודה**
יצירת נקודה גיאוגרפית באמצעות ה-API היא פשוטה וקלה כפי שמוצג בדוגמת הקוד הבאה.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePoint-CreatePoint.cs" >}}
### **צור MultiPoint**
Aspose.GIS עבור .NET מספקת את האפשרות לייצג אוסף של נקודות ככיתת MultiPoint אחת. הוא יכול להכיל נקודה אחת או יותר המוגדרות על ידי מידע קו רוחב-אורך של כל נקודה.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPoint-CreateMultiPoint.cs" >}}
## **גיאומטריית מחרוזת קו**
ניתן ליצור מחרוזת קו על ידי ציון גיאומטריות נקודה.
### **צור מחרוזת קו**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateLineString-CreateLineString.cs" >}}
### **צור MultiLine String**
מחרוזת MultiLine היא אוסף של מחרוזות קו שהן בעצמן בנויות מגיאומטריות נקודה.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiLineString-CreateMultiLineString.cs" >}}
## **גיאומטריית מצולע**
מצולע הוא אוסף של גיאומטריות נקודה המוגדר על ידי נקודות בצורה של LinearRing.
### **צור מצולע**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygon-CreatePolygon.cs" >}}
### **צור MultiPolygon**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateMultiPolygon-CreateMultiPolygon.cs" >}}
### **צור מצולע עם חור**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreatePolygonWithHole-CreatePolygonWithHole.cs" >}}
## **צור אוסף גיאומטריה**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Geometries-CreateGeometryCollection-CreateGeometryCollection.cs" >}}
