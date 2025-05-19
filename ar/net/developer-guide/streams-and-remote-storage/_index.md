---
title: "تدفقات وتخزين عن بُعد"
type: docs
url: /ar/net/streams-and-remote-storage/
weight: 70
---

## **العمل مع تنسيقات الملفات المتعددة**
بعض تنسيقات بيانات نظم المعلومات الجغرافية تنقسم إلى عدة ملفات. على سبيل المثال، يجب أن تحتوي ملفات الشكل على الأقل على ثلاث ملفات: *.shp، *.shx، و *.dbf. تتطلب هذه التنسيقات تخزين جميع الملفات في هيكل دليل معين بنمط محدد لأسماء الملفات.

في الوقت نفسه، قد يتم تخزين الملفات في خادم عن بُعد، أو موقع آخر يمكن الوصول إليه من خلال تدفقات فقط. تفتقر التدفقات إلى معلومات حول أسماء الملفات وهيكل الدليل، مما يجعل من المستحيل على برامج تشغيل تنسيق الملفات تحديد كيفية معالجة البيانات. يُحل ذلك بواسطة Aspose.GIS من خلال توفير آلية المسارات المجردة.

يُمثل المسار المجرد مسارًا إلى ملف (أو دليل) في بعض تخزينيات الملفات شبيهة بنظام الملفات. يمكن أن يكون التخزين أي شيء يتضمن مفهوم الملف والدليل، من أرشيف إلى خادم FTP. يحدد كيفية تنفيذ عمليات الملف التقليدية، مثل فتح ملف أو إدراج دليل.

يمكنك تحديد كيفية تنفيذ عمليات الملفات لتخزينك من خلال تنفيذ فئة ترث من [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) وتوفير تطبيقات لأساليبه المجردة.
## **عرض: تخزين Blob في Azure**
يحتوي مستودع أمثلة Aspose.GIS على مثال لتنفيذ مسار مجرد مخصص لتخزين Blob في Azure بشكل يعمل بكامل الوظائف. هذا العرض يوضح كيفية قراءة ملف شكل مباشرةً من تخزين Blob في Azure. يمكنك العثور عليه هنا: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **تنسيقات الملفات ذات الملف الواحد (GeoJSON، KML)**
تنسيقات بيانات نظم المعلومات الجغرافية مثل GeoJSON و KML يمكن أن تُخزن جميع البيانات لطبقة ما في ملف واحد. إذا كنت تستطيع الحصول على تدفق للملف، فيمكنك تجاوز تنفيذ مسار مجرد مخصص واستخدام طريقة [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) لإنشاء مسار مجرد للتدفق.
### **قراءة ملف من التدفق**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **كتابة ملف إلى تدفق**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
