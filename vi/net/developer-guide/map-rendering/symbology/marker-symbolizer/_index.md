---
title: "Biểu tượng Marker"
type: docs
url: /vi/net/marker-symbolizer/
weight: 10
description: Thư viện hoặc API GIS C# hỗ trợ biểu tượng Marker đơn giản, vẽ một hình dạng được xác định trước với tô màu và đường viền có thể tùy chỉnh trên các hình học thuộc mọi loại như Điểm, Đường, Bề mặt.
---

## **Biểu tượng Marker**
Biểu tượng Marker đơn giản vẽ một hình dạng được xác định trước với tô màu và đường viền có thể tùy chỉnh. Đây là biểu tượng mặc định cho các hình học 0 chiều (điểm). 

Các hình dạng được hỗ trợ:

|![todo:image_alt_text](marker-symbolizer_1.png)|Vòng tròn| |![todo:image_alt_text](marker-symbolizer_2.png)|Sao|
| :- | :- | :- | :- | :- |
|![todo:image_alt_text](marker-symbolizer_3.png)|Hình vuông| |![todo:image_alt_text](marker-symbolizer_4.png)|Chữ thập|
|![todo:image_alt_text](marker-symbolizer_5.png)|Tam giác| |![todo:image_alt_text](marker-symbolizer_6.png)|X|

Các tùy chọn tạo kiểu được hỗ trợ:

|**Thuộc tính**|**Mô tả**|
| :- | :- |
|[ShapeType](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/shapetype)|Chỉ định hình dạng của marker.|
|[Size](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/size)|Chỉ định kích thước của hình dạng marker|
|[FillColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/fillcolor)|Chỉ định màu sắc và độ trong suốt cho phần tô.|
|[StrokeColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokecolor)|Chỉ định màu sắc và độ trong suốt cho đường viền|
|[StrokeWidth](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokewidth)|Chỉ định độ rộng của đường viền|
|[StrokeLineJoin](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokelinejoin)|Xác định cách các đường được hiển thị tại giao điểm của các đoạn thẳng.|
|[StrokeStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokestyle)|Chỉ định cách đường viền của biểu tượng nên được vẽ.|
|[StrokeDashPattern](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashpattern)|Chỉ định một mảng khoảng cách xác định độ dài của các đoạn gạch nối và khoảng trống trong các đường đứt nét.|
|[StrokeDashOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/strokedashoffset)|Chỉ định khoảng cách từ đầu một đường đến điểm bắt đầu của mẫu gạch nối.|
|[Rotation](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/rotation)|Chỉ định độ xoay của biểu tượng xung quanh tâm của nó, bằng độ thập phân. Các giá trị dương chỉ ra sự xoay theo chiều kim đồng hồ, các giá trị âm chỉ ra sự xoay ngược chiều kim đồng hồ. Mặc định là 0.|
|[HorizontalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontaloffset)|Chỉ định độ lệch ngang từ vị trí một điểm đến điểm neo của hình dạng.|
|[VerticalOffset](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticaloffset)|Chỉ định độ lệch dọc từ vị trí một điểm đến điểm neo của hình dạng.|
|[HorizontalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/horizontalanchorpoint)|Chỉ định cạnh nào của hình dạng marker sẽ được căn chỉnh ngang với vị trí điểm.|
|[VerticalAnchorPoint](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker/properties/verticalanchorpoint)|Chỉ định cạnh nào của hình dạng marker sẽ được căn chỉnh dọc với vị trí điểm.|

### **Loại Hình học**
` `Biểu tượng này có thể được áp dụng cho các hình học thuộc mọi loại.

|**Kích thước Hình học**|**Loại Hình học**|**Hành vi Hiển thị**|
| :-: | :-: | :-: |
|**Điểm**|Điểm, MultiPoint|Vẽ hình dạng ở trung tâm tọa độ điểm.|
|**Đường**|LineString, CircularString, CompoundCurve, LinerRing, MultiCurve, MultiLineString|<p>Vẽ hình dạng ở trung tâm của trọng tâm của hình học</p><p> </p>|
|**Bề mặt**|Polygon, CurvePolygon, MultiPolygon, MultiSurface||

Đối với GeometryCollections, hành vi hiển thị được xác định riêng cho từng hình học bên trong bộ sưu tập. Các lớp có loại hình học hỗn hợp tuân theo logic cho GeometryCollections.

Sử dụng MixedGeometrySymbolizer để giới hạn biểu tượng ở các loại hình học cụ thể.

### **Ví dụ**
Theo mặc định, biểu tượng marker vẽ các vòng tròn màu đen:



Đây là cách thay đổi màu tô thành màu đỏ:




|![todo:image_alt_text](marker-symbolizer_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyle.cs" >}}|
| :- | :- |

-----

Một ví dụ khác về tạo kiểu với một hình dạng được xác định trước (tam giác):




|![todo:image_alt_text](marker-symbolizer_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleTriangles.cs" >}}|
| :- | :- |

-----
Đối với các kịch bản nâng cao hơn, bạn có thể muốn điều chỉnh kiểu marker một cách động dựa trên giá trị thuộc tính của đối tượng. Đây là cách thực hiện:




|![todo:image_alt_text](marker-symbolizer_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-ChangeMarkerStyleFeatureBased.cs" >}}|
| :- | :- |

-----
Bạn cũng có thể muốn thêm nhãn cho các marker của mình. Hãy truy cập [Ví dụ về Nhãn Điểm](/gis/net/simple-labeling/#simplelabeling-pointslabelingexamples) để biết thêm ví dụ.
