---
title: "Biểu tượng đường"
type: docs
url: /vi/net/line-symbolizer/
weight: 20
description: Thư viện GIS C# hoặc API hỗ trợ biểu tượng đường đơn giản cho các hình học 1 chiều là đường và có thể được áp dụng trên các hình học của bất kỳ loại nào như Điểm, Đường, Bề mặt.
---

## **Biểu tượng đường**
Biểu tượng đường đơn giản vẽ một đường với kiểu tùy chỉnh. Đây là biểu tượng mặc định cho các hình học 1 chiều (đường). 

Các tùy chọn tạo kiểu được hỗ trợ:

|**Thuộc tính**|**Mô tả**|
| :- | :- |
|[Color](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/color)|Chỉ định màu sắc và độ trong suốt của đường.|
|[Width](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/width)|Chỉ định chiều rộng của đường|
|[LineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/linejoin)|Xác định cách các đường được hiển thị tại giao điểm của các đoạn thẳng.|
|[Style](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/style)|Chỉ định cách đường viền biểu tượng nên được vẽ.|
|[DashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashpattern)|Chỉ định một mảng khoảng cách xác định độ dài của các đoạn gạch nối và khoảng trống xen kẽ trong các đường nét đứt.|
|[DashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/dashoffset)|Chỉ định khoảng cách từ điểm bắt đầu của một đường đến điểm bắt đầu của mẫu gạch nối.|
|[CapStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/capstyle)|<p>Chỉ định cách các đường được hiển thị ở cuối chúng.</p><p>- Butt - cạnh vuông sắc nét</p><p>- Round - cạnh bo tròn</p><p>- Square - cạnh vuông hơi kéo dài</p>|
|[Offset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline/properties/offset)|Chỉ định độ lệch từ đường ban đầu. Đối với khoảng cách dương, độ lệch sẽ ở bên trái của đường (tương đối so với hướng đường). Đối với khoảng cách âm, nó sẽ ở bên phải.|

### **Loại hình học**
` `Biểu tượng có thể được áp dụng cho các hình học của bất kỳ loại nào.

|**Kích thước hình học**|**Loại hình học**|**Hành vi hiển thị**|
| :-: | :-: | :-: |
|**Điểm**|Point, MultiPoint|Vẽ một đường có chiều dài nhỏ với hướng ngang được căn giữa điểm, với hai nắp cuối.|
|**Đường**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Vẽ đường.|
|**Bề mặt**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Đường viền khép kín của hình học được sử dụng làm chuỗi đường (không có nắp cuối)|

Đối với GeometryCollections, hành vi hiển thị được xác định riêng cho từng hình học bên trong bộ sưu tập. Các lớp có loại hình học hỗn hợp tuân theo logic cho GeometryCollections.

Sử dụng MixedGeometrySymbolizer để giới hạn một biểu tượng ở các loại hình học cụ thể.

### **Ví dụ**
Theo mặc định, biểu tượng đường vẽ các đường màu đen:



Đây là cách thay đổi màu đường thành màu xanh lam:



|![todo:image_alt_text](line-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyle.cs" >}}|
| :- | :- |

Để có các kịch bản nâng cao hơn, bạn có thể muốn điều chỉnh kiểu đường động dựa trên giá trị thuộc tính của đối tượng. Dưới đây là cách thực hiện:



|![todo:image_alt_text](line-symbolizer_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeLineStyleComplex.cs" >}}|
| :- | :- |



Bạn cũng có thể muốn thêm nhãn vào các đường của mình. Hãy truy cập [Ví dụ về gắn nhãn đường](/gis/net/simple-labeling/#simplelabeling-lineslabelingexamples) để biết thêm ví dụ.
