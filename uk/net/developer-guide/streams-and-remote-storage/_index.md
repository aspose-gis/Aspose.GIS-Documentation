---
title: "Потоки та віддалене сховище"
type: docs
url: /uk/net/streams-and-remote-storage/
weight: 70
---

## **Робота з багатофайловими форматами**
Деякі формати геоінформаційних даних розбивають вміст на кілька файлів. Наприклад, shapefile повинен мати щонайменше три файли: *.shp, *.shx та *.dbf. Ці формати вимагають зберігання всіх файлів у певній структурі каталогів із попередньо визначеним шаблоном для імен файлів.

Водночас файли можуть бути збережені на віддаленому сервері або в іншому місці, доступному лише через потоки. Потоки не містять інформації про імена файлів та структуру каталогів, що унеможливлює визначення способу обробки даних драйверами форматів файлів. Aspose.GIS вирішує цю проблему шляхом забезпечення механізму абстрактних шляхів.

Абстрактний шлях представляє шлях до файлу (або каталогу) в деякому сховищі, подібному до файлової системи. Сховище може бути будь-чим, що має поняття файлу та каталогу, від архіву до FTP-сервера. Він визначає, як виконувати типові операції з файлами, такі як відкриття файлу або перегляд каталогу.

Ви можете визначити, як виконувати операції з файлами для вашого сховища, реалізуючи клас, який успадковується від [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) та надаючи реалізації для його абстрактних методів.
## **Приклад: Azure Blob Storage**
Репозиторій Aspose.GIS Examples містить приклад повнофункціональної реалізації спеціального абстрактного шляху для Azure Blob Storage. Цей приклад демонструє, як читати shapefile безпосередньо з Azure Blob Storage. Ви можете знайти його тут: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **Однофайлові формати (GeoJSON, KML)**
Формати геоінформаційних даних, такі як GeoJSON та KML, можуть зберігати всі дані для шару в одному файлі. Якщо ви можете отримати потік для файлу, ви можете пропустити реалізацію спеціального абстрактного шляху та використовувати метод [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) для створення абстрактного шляху для потоку.
### **Читання файлу з потоку**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **Запис файлу в потік**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
