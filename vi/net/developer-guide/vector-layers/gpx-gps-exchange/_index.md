---
title: Làm việc với các tệp ở định dạng GPX (GPS Exchange Format) trong C#
linktitle: GPX - Định dạng trao đổi GPS
type: docs
url: /vi/net/gpx-gps-exchange/
weight: 60
description: Thư viện GIS của C# cho phép bạn mở và đọc các đối tượng từ các tệp ở định dạng GPX (GPS Exchange File).
---

## **Làm việc với các tệp ở định dạng GPX (GPS Exchange Format)**
Aspose.GIS cho phép bạn mở và đọc các đối tượng từ các tệp ở định dạng GPX (GPS Exchange File).
## **Đọc các đối tượng từ tệp GPX**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXFeatures.cs" >}}
## **Đọc các đối tượng cho mỗi điểm trong phân đoạn**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-ReadGPXNestedAttributes.cs" >}}
## **Ghi các đa giác dưới dạng đường thẳng vào tệp GPX**
Định dạng GPX không hỗ trợ đa giác và đa giác phức tạp. Do đó, đôi khi việc chuyển đổi từ các định dạng khác có thể thất bại. Bạn nên áp dụng tùy chọn WritePolygonsAsLines để giải quyết vấn đề này.
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-GpxLayer-WriteGpxPolygonsAsLines.cs" >}}
