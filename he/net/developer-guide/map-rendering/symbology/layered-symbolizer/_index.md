---
title: "סמליזציה שכבתית"
type: docs
url: /he/net/layered-symbolizer/
weight: 40
description: סמליזציה שכבתית בספריית ה-GIS C# API מציירת תכונה עם מספר סמלים אחד על השני במצבי סדר עיבוד המבוססים על תכונות או שכבות.
---

## **סמליזציה שכבתית**
הסמליזציה השכבתית מציירת תכונה עם מספר סמלים אחד על השני. ניתן לבחור משני מצבי סדר עיבוד:

- [RenderOrder.ByFeatures](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - לצייר את התכונה הראשונה עם כל הסמלים שהוספו לסמליזציה השכבתית, ואז להמשיך בצייור התכונה הבאה.
- [RenderOrder.ByLayers](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/renderingorder) - לצייר את כל התכונות עם הסמל הראשון, ולאחר מכן לצייר את כל התכונות עם הסמל הבא.
### **עיבוד לפי תכונות**

### **עיבוד לפי שכבות**


|![todo:image_alt_text](layered-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-DrawLayeredSymbolizersByLayers.cs" >}}|
| :- | :- |
