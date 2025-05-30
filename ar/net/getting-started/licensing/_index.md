---
title: "الترخيص"
second_title: Aspose.GIS لـ .NET
type: docs
url: /ar/net/licensing/
weight: 50
keywords: مكتبة جيوغرافية جغرافية c#، مكتبة جيوغرافية .net
description: قم بتقييم مكتبة أسبوز جي.آي.إس لـ C# .NET أو واجهة برمجة تطبيقات مع بعض القيود. قم بتطبيق الترخيص باستخدام ملف أو كائن تدفق أو كمورد مضمن.
---

## **قيم Aspose.GIS لـ .NET**
يمكنك تحميل Aspose.GIS لـ .NET مجانًا. قبل تطبيق ترخيص ، يعمل المكون في وضع التقييم. عند شراء ترخيص وإضافة بضعة أسطر من الكود لتطبيق الترخيص ، يتم إزالة قيود التقييم.

{{% alert color="primary" %}} إذا كنت ترغب في اختبار Aspose.GIS بدون قيود وضع التقييم ، يمكنك طلب ترخيص مؤقت لمدة 30 يومًا. يرجى الرجوع إلى [الحصول على ترخيص مؤقت](https://purchase.aspose.com/temporary-license). {{% /alert %}} 

### **قيود وضع التقييم**
عند التشغيل في وضع التقييم (بدون ترخيص مطبق) ، يوفر Aspose.GIS وظائف المنتج الكاملة باستثناء بعض قيود التقييم.

1. لا يمكن فتح أكثر من **15 مستندًا** و / أو إنشاءه خلال **الساعة الواحدة**
2. لا يمكن الوصول إلى أكثر من **100 ميزة** في كل مستند (قراءة أو كتابة)
3. لا يمكن الوصول إلى أكثر من **10 000 بيانات للصورة النقطية** في كل مستند (قراءة أو كتابة).
4. الحد الأقصى لعدد الميزات المسموح بها في مستند لعمليات التحويل هو **50**

عند التشغيل في وضع مرخص ، يمكنك معالجة عدد غير محدود من المستندات والميزات.
## **تطبيق ترخيص**
الترخيص هو ملف XML نصي يحتوي على تفاصيل مثل اسم المنتج ، وعدد المطورين الذي تُرخص لهم ، وتاريخ انتهاء الاشتراك وما إلى ذلك. الملف موقع رقميًا ، لذلك لا تقم بتعديل الملف. حتى إضافة عرض سطر عمودي اضافي غير مقصود إلى الملف سيجعله غير صالح.

يجب عليك تعيين ترخيص قبل استخدام Aspose.GIS إذا كنت ترغب في تجنب قيود التقييم الخاصة به. تكون هذه الأمر مطلوبة فقط لتعيين ترخيص مرة واحدة لكل تطبيق (أو عملية).
### **تعيين ترخيص في Aspose.GIS لـ .NET**
في Aspose.GIS ، يمكن تحميل الترخيص من ملف أو تدفق أو مورد مضمن. تحاول Aspose.GIS العثور على الترخيص في المواقع التالية:

- المسار الصريح
- المجلد الذي يحتوي على Aspose.GIS.dll
- المجلد الذي يحتوي على التجميع الذي استدعى Aspose.GIS.dll
- المجلد الذي يحتوي على التجميع الذي استدعى (الملف التنفيذي الخاص بك)
- مورد مضمن في التجميع الذي استدعى Aspose.GIS.dll. هناك طريقتان شائعتان لتعيين الترخيص ، يتم مناقشتهما أدناه:
### **تطبيق الترخيص باستخدام ملف أو كائن تدفق**
أسهل طريقة لتعيين ترخيص هي وضع ملف الترخيص في نفس المجلد الذي يحتوي على Aspose.GIS.dll وتحديد اسم الملف فقط من دون مساره.



{{< highlight java >}}

// عين مثيلًا للترخيص وحدد ملف الترخيص من خلال مساره

كرخصة Aspose.Gis.License = جديد أسبوع.جي الرخصة ( ) ;

كرخصة. مجموعة الترخيص ( "Aspose.GIS.lic") ;

{{< /highlight >}}

{{< highlight java >}}

// عين مثيلًا للترخيص وقم بتعيين الترخيص من خلال تدفق

كرخصة Aspose.Gis.License = جديد أسبوز.جي الرخصة ( ) ;

كرخصة.مجموعة الترخيص(  ) ;

{{< /highlight >}}



عند استدعاء طريقة SetLicense ، يجب أن يكون اسم الترخيص هو نفسه اسم ملف الترخيص الخاص بك. على سبيل المثال ، يمكنك تغيير اسم ملف الترخيص إلى "Aspose.GIS.lic.xml". ثم في الكود الخاص بك ، يجب استخدام اسم الترخيص المعدل (وهو Aspose.GIS.lic.xml) لطريقة SetLicense.
## **تضمين ملف الترخيص كمورد مضمن**
طريقة أنيقة أخرى لتعبئة الترخيص مع تطبيقك والتأكد من عدم فقدانه ، هي تضمينه كمورد مضمن في أحد التجميعات التي تستدعي dll للمكون (المضمن في Aspose.GIS). لتضمين ملف الترخيص كمورد مضمن ، قم باتباع الخطوات التالية:

- في Visual Studio ، قم بتضمين ملف الترخيص (.lic) في المشروع باستخدام File | Add Existing Item... القائمة
- حدد الملف في مستكشف الحلول واضبط Build Action على مورد مضمن في نافذة الخصائص
- للوصول إلى الترخيص المضمن في التجميع (كمورد مضمن) ، لا يلزم استدعاء GetExecutingAssembly و GetManifestResourceStream من فئة Microsoft .NET Framework. كل ما يلزم القيام به هو مجرد إضافة ملف الترخيص كمورد مضمن إلى مشروعك وتمرير اسم ملف الترخيص إلى طريقة License.SetLicense. ستجد فئة License تلقائيًا ملف الترخيص في الموارد المضمنة.

يرجى مراجعة المثال المعطى أدناه لفهم هذه الطريقة لتعيين الترخيص (المضمن) في تطبيقاتك.

{{< highlight java >}}

// عين فئة الترخيص

كرخصة Aspose.Gis = الرخصة الجديدة أسبوز.جي الرخصة ( ) ;

// مرر فقط اسم ملف الترخيص المضمن في التجميع

كرخصة.مجموعة الترخيص ( "Aspose.GIS.lic") ;

{{< /highlight >}}

## **تطبيق مفتاح المتردة**
[Aspose.Gis لـ .NET API](/ar/gis/net/) تسمح للمطورين بتطبيق مفتاح المتردة. إنه آلية ترخيص جديدة. ستُستخدم آلية الترخيص الجديدة إلى جانب آلية الترخيص الحالية. يمكن للعملاء الذين يرغبون في تقديم فواتير استنادًا إلى استخدام ميزات الواجهة البرمجية التحقق من المفتاح المتردد. لمزيد من التفاصيل ، يرجى الرجوع إلى القسم [أسئلة شائعة عن المفتاح المتردد](https://purchase.aspose.com/faqs/licensing/metered).

تم إدخال فئة جديدة **Metered** لتطبيق مفتاح المتردة. يتضمن الكود النموذجي التالي كيفية ضبط مفتاح المتردة العام والخاص.

**[C#]**

{{< highlight csharp >}}

// ضبط مفتاح المتردة العام والخاص

كرخصة Aspose.Gis.Metered = الجديدة أسبوز.جيس.ميتيرد ( ) ;

// الوصول إلى الخاصية setMeteredKey ومرور المفاتيح العامة والخاصة كمعلمات

ميترد.التعيين الميترة كي ( "*****", "*****") ;

// عملية المعالجة

// الحصول على كمية البيانات المستهلكة

عددي ليسونس.Metered.GetConsumptionQuantity();

// عرض المعلومات

اعرض "المبلغ المستهلك : " + amount.ToString();

{{< /highlight >}}
