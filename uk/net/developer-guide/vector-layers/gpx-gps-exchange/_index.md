---
title: Робота з файлами GPS Exchange Format GPX у C#
linktitle: GPX - Формат обміну даними GPS
type: docs
url: /uk/net/gpx-gps-exchange/
weight: 60
description: Бібліотека C# GIS дозволяє відкривати та читати об'єкти з файлів GPS Exchange File (GPX).
---

## **Робота з файлами GPS Exchange File (GPX)**
Aspose.GIS дозволяє відкривати та читати об'єкти з файлів GPS Exchange File (GPX).
## **Читання об'єктів з GPX файлу**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **Читання об'єктів для кожної точки в сегменті**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **Запис багатокутників як ліній у GPX файл**
Формат GPX не підтримує полігони та мультиполігони. В результаті, іноді перетворення з інших форматів може бути невдалим. Ви повинні застосувати опцію WritePolygonsAsLines для вирішення цієї проблеми.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
