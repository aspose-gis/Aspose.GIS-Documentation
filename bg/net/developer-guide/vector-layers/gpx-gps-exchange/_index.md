---
title: Работа с файлове в GPX формат за обмен на GPS данни в C#
linktitle: GPX - Формат за обмен на GPS данни
type: docs
url: /bg/net/gpx-gps-exchange/
weight: 60
description: C# GIS библиотека ви позволява да отворите и прочетете характеристики от файлове с формат за обмен на GPS данни (GPX).
---

## **Работа с файлове в GPX формат за обмен на GPS данни**
Aspose.GIS ви позволява да отворите и прочетете характеристики от файлове с формат за обмен на GPS данни (GPX).
## **Четене на характеристики от GPX файл**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **Четене на характеристики за всяка точка в сегмент**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **Запис на полигони като линии в GPX файл**
GPX форматът не поддържа полигони и многополигони. В резултат, понякога преобразуването от други формати е неуспешно. Трябва да приложите опцията WritePolygonsAsLines, за да разрешите този проблем.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
