---
title: Praca z plikami w formacie GPX (GPS Exchange Format) w C#
linktitle: GPX - Format wymiany danych GPS
type: docs
url: /pl/net/gpx-gps-exchange/
weight: 60
description: Biblioteka GIS dla C# umożliwia otwieranie i odczytywanie cech z plików w formacie GPS Exchange File (GPX).
---

## **Praca z plikami w formacie GPX (GPS Exchange Format)**
Aspose.GIS umożliwia otwieranie i odczytywanie cech z plików w formacie GPS Exchange File (GPX).
## **Odczytywanie cech z pliku GPX**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **Odczytywanie cech dla każdego punktu w segmencie**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **Zapisywanie wielokątów jako linii do pliku GPX**
Format GPX nie obsługuje wielokątów i wielowielokątów. W rezultacie konwersja z innych formatów czasami może się nie powieść. Należy zastosować opcję WritePolygonsAsLines, aby rozwiązać ten problem.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
