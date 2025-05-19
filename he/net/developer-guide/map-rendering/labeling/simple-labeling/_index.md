---
title: "תיוג פשוט"
type: docs
url: /he/net/simple-labeling/
weight: 10
---

## **תיוג פשוט**
התיוג הפשוט מציין כיצד יש לתייג תכונות.

אפשרויות נתמכות הן:

|**מאפיין**|**תיאור**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|מציין את שם המאפיין שיש להשתמש בו כמקור לתיוגים.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|מספק דרך להתאים אישית ולעצב את טקסט התווית. עוקף את LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|מציין את משפחת הגופנים שיש להשתמש בה כדי לעבד טקסט. ברירת המחדל היא ערך התלוי במערכת.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>סגנון ליישום על הטקסט.</p><p>- FontStyle.Regular - טקסט רגיל.</p><p>- FontStyle.Bold - טקסט מודגש.</p><p>- FontStyle.Italic - טקסט נטוי.</p><p>- FontStyle.Underine - טקסט קו תחתון.</p><p>- FontStyle.StrikeOut - טקסט עם קו באמצע.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|מציין את גודל הטקסט.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|קובע את צבע הטקסט.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|קובע גודל הילה (או קו מתאר) סביב הטקסט.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|קובע את צבע ההילה סביב הטקסט.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|ביטוי גיאומטריה שיש להשתמש בו כדי לשנות את הגיאומטריות לפני העברתן למנוע התיוג.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>מציין התנהגות עיבוד עבור גיאומטריות מרובות חלקים.</p><p>- MultipartMode.All - הצב תווית ליד כל חלק של הגיאומטריה.</p><p>- MultipartMode.Any - הצב תווית אחת ליד כל חלק של הגיאומטריה.</p><p>- MultipartMode.Largest - הצב תווית ליד החלק הגדול ביותר של הגיאומטריה.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>מציין כיצד תוויות ממוקמות ביחס לגיאומטריה.</p><p>- PointLabelPlacement - ממקם תווית ליד מרכז הגיאומטריה.</p><p>- LineLabelPlacement - ממקם תווית לאורך הגיאומטריה או ההיקף שלה.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|מציין את העדיפות של התווית במקרה שהיא חופפת לתווית אחרת.<br>התווית בעדיפות נמוכה יותר אינה מעובדת. ברירת המחדל היא 1000.|

## **דוגמאות**
### **דוגמאות תיוג נקודות**
כברירת מחדל, SimpleLabeling מצייר טקסט על נקודות:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
הנה איך לעצב גופן:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
כדי לשלוט במיקום הטקסט ביחס לתכונת הנקודה, יש להגדיר את המאפיין placement:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
לתרחישים מתקדמים יותר, ייתכן שתרצה לבחור תיוגים שונים לתכונות. הנה איך לעשות את זה:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **דוגמאות תיוג קווים**
כברירת מחדל, SimpleLabeling מצייר תווית ליד מרכז הקו:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
כדי לסובב תוויות כך שהן מקבילות לקווים, ניתן להשתמש ב-LineLabelPlacement עם LineLabelAlignment.Parallel:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
אם אתה רוצה שהטקסטים יעקבו אחר הקו במדויק, ניתן להשתמש ב-LineLabelPlacement עם LineLabelAlignment.Curved:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
אם אינך רוצה שהטקסטים יחפפו עם הקו, השתמש ב-LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
לתרחישים מתקדמים יותר, ייתכן שתרצה להתאים את סגנון התוויות באופן דינמי בהתבסס על ערכי המאפיינים של התכונה. הנה איך לעשות את זה:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
