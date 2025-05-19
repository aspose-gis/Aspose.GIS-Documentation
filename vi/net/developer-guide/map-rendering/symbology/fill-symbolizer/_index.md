---
title: "Fill Symbolizer"
type: docs
url: /vi/net/fill-symbolizer/
weight: 30
description: Thư viện GIS C# API hỗ trợ Simple Fill symbolizer để tô màu và đường viền cho các hình học 2 chiều đa giác thuộc mọi loại như Điểm, Đường, Bề mặt.
---

## **Fill Symbolizer**
Simple Fill symbolizer lấp đầy một khu vực bằng kiểu tô màu và đường viền có thể tùy chỉnh. Đây là symbolizer mặc định cho các hình học 2 chiều (đa giác). 

Nếu một đa giác có “lỗ”, chúng sẽ không được tô màu, nhưng các đường viền xung quanh lỗ sẽ được vẽ theo cách thông thường. “Đảo” bên trong lỗ sẽ được tô màu và vẽ, v.v.

Các tùy chọn tạo kiểu được hỗ trợ:

|**Property**|**Description**|
| :- | :- |
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillcolor)|Chỉ định màu sắc và độ trong suốt được cung cấp cho phần tô màu.|
|[FillStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/fillstyle)|<p>- Solid - Tô màu đặc</p><p>- None - Không tô đa giác</p><p>- Horizontal Hatch - Một mẫu các đường ngang.</p><p>- Vertical Hatch - Một mẫu các đường dọc.</p><p>- Cross Hatch - Chỉ định các đường ngang và dọc giao nhau.</p><p>- Forward Diagonal Hatch - Một mẫu các đường chéo từ trên trái xuống dưới phải.</p><p>- Backward Diagonal Hatch - Một mẫu các đường chéo từ trên phải xuống dưới trái.</p><p>- Diagonal Cross Hatch - Một mẫu các đường chéo đan xen.</p>|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokecolor)|Chỉ định màu sắc và độ trong suốt được cung cấp cho đường viền.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokestyle)|Chỉ định cách đường viền của symbol nên được vẽ.|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokewidth)|Chỉ định độ rộng của đường viền.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashpattern)|Chỉ định một mảng khoảng cách chỉ định độ dài của các đoạn gạch nối và khoảng trống xen kẽ trong các đường nét đứt.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokedashoffset)|Chỉ định khoảng cách từ điểm bắt đầu của một đường đến điểm bắt đầu của mẫu gạch nối.|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/strokelinejoin)|<p>Xác định cách các đường được hiển thị tại giao điểm của các đoạn thẳng.</p><p>- Miter - góc nhọn</p><p>- Round - góc tròn</p><p>- Bevel - góc xiên</p>|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/horizontaloffset)|Chỉ định độ lệch ngang từ vị trí một điểm đến điểm neo của hình dạng.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill/properties/verticaloffset)|Chỉ định độ lệch dọc từ vị trí một điểm đến điểm neo của hình dạng.|

### **Geometry Types**
` `Symbolizer có thể được áp dụng cho các hình học thuộc mọi loại.

|**Geometry Dimension**|**Geometry Types**|**Rendering Behavior**|
| :-: | :-: | :-: |
|**Point**|Point, MultiPoint|Vẽ một hình vuông nhỏ theo chiều dọc.|
|**Line**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|Đường được đóng để tô màu bằng cách kết nối điểm cuối của nó với điểm bắt đầu của nó. Chỉ đường ban đầu được vẽ.|
|**Surface**|Polygon, CurvePolygon, MultiPolygon, MultiSurface|Vẽ đa giác.|

Đối với GeometryCollections, hành vi hiển thị được xác định riêng cho từng hình học bên trong bộ sưu tập. Các lớp có loại hình học hỗn hợp tuân theo logic cho GeometryCollections.

Sử dụng MixedGeometrySymbolizer để giới hạn symbolizer ở các loại hình học cụ thể.

### **Examples**
Theo mặc định, Simple Fill symbolizer vẽ một đường viền màu đen và tô màu trắng đặc:



Đây là cách thay đổi kiểu dáng:


|![todo:image_alt_text](fill-symbolizer_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeFillStyle.cs" >}}|
| :- | :- |

Bạn cũng có thể muốn thêm nhãn vào các đa giác của mình. Hãy truy cập [Lines Labeling Examples](/gis/vi/simple-labeling/#simplelabeling-lineslabelingexamples) để biết ví dụ về cách gắn nhãn đường viền đa giác hoặc [Points Labeling Examples](/gis/vi/simple-labeling/#simplelabeling-pointslabelingexamples) trên các ví dụ về cách gắn nhãn tâm của đa giác.
