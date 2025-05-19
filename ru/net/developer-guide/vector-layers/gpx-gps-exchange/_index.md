---
title: Работа с файлами формата обмена GPS GPX в C#
linktitle: GPX - Формат обмена GPS
type: docs
url: /ru/net/gpx-gps-exchange/
weight: 60
description: Библиотека C# GIS позволяет открывать и читать объекты из файлов формата обмена GPS (GPX).
---

## **Работа с файлами формата обмена GPS (GPX)**
Aspose.GIS позволяет открывать и читать объекты из файлов формата обмена GPS (GPX).
## **Чтение объектов из GPX файла**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **Чтение объектов для каждой точки в сегменте**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **Запись полигонов в виде линий в GPX файл**
Формат GPX не поддерживает полигоны и мультиполигоны. В результате, иногда преобразование из других форматов может быть неудачным. Вам следует применить опцию WritePolygonsAsLines для решения этой проблемы.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
