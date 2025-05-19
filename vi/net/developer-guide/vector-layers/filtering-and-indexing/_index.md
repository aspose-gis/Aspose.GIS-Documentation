---
title: Lọc và Tạo Chỉ Mục cho Các Lớp Vector GIS trong C#
linktitle: Lọc và Tạo Chỉ Mục
second_title: Aspose.GIS for .NET
type: docs
url: /vi/net/filtering-and-indexing/
weight: 30
description: Với Thư viện hoặc API GIS C# .NET, bạn có thể lọc các lớp vector GIS theo giá trị thuộc tính hoặc giới hạn không gian. Bạn cũng có thể sử dụng chỉ mục để tăng tốc độ lọc và truy vấn không gian.
---

Với Aspose.GIS for .NET, bạn có thể lọc các lớp theo giá trị thuộc tính hoặc giới hạn không gian. Bạn cũng có thể sử dụng chỉ mục để tăng tốc độ lọc và truy vấn không gian.
## **Chỉ mục Thuộc tính**
### **Lọc Không Có Chỉ Mục**
Đây là cách lọc một lớp theo giá trị của một thuộc tính:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **Lọc Với Chỉ Mục**
Mã trên hoạt động tốt miễn là lớp chỉ được lọc một lần. Nhưng, nếu lớp có khả năng được truy vấn nhiều lần, chúng ta có thể hưởng lợi từ các chỉ mục thuộc tính. Việc xây dựng chỉ mục thuộc tính mất một chút thời gian, nhưng nó có thể được sử dụng nhiều lần để tăng tốc độ lọc.

Ví dụ sau sử dụng tệp chỉ mục thuộc tính để tăng tốc độ lọc lớp theo giá trị của thuộc tính:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **Lưu Các Tính Năng Đã Lọc**
Các tính năng đã lọc có thể được lưu vào các lớp:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **Kết Xuất Các Tính Năng Đã Lọc**
Bạn cũng có thể kết xuất các tính năng đã lọc. Ví dụ sau sử dụng chỉ mục thuộc tính để nhanh chóng chọn tất cả các tính năng có dân số lớn hơn 2000 và thêm chúng vào bản đồ:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **Chỉ Mục Không Gian**
Các chỉ mục không gian được sử dụng để tăng tốc độ truy vấn không gian. Giống như các chỉ mục thuộc tính, các chỉ mục không gian được tái sử dụng sau khi tạo.
### **Tìm Các Tính Năng Gần Nhất với Điểm**
Đây là cách sử dụng chỉ mục không gian để tăng tốc độ tìm kiếm tính năng gần nhất với một điểm:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **Chọn Các Tính Năng Giao Với Hình Học**
Ví dụ sau sử dụng chỉ mục không gian để tăng tốc độ chọn các tính năng giao với hình học:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
