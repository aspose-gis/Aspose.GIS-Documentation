---
title: Biểu tượng - API GIS C#
linktitle: "Biểu tượng"
type: docs
url: /vi/net/symbology/
weight: 10
description: Thư viện hoặc API GIS C# hỗ trợ các biểu tượng để vẽ hình học đối tượng như Điểm đánh dấu, Đường thẳng, Tô màu và kết hợp các biểu tượng để tạo ra các hình ảnh trực quan phức tạp hơn.
---

Một biểu tượng là một cách để vẽ hình học của một đối tượng trên bản đồ.

|** **|**Biểu tượng**|**Lớp API**|**Mô tả**|
| :- | :- | :- | :- |
|![todo:image_alt_text](symbology_1.png)|**Điểm đánh dấu**|[SimpleMarker](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplemarker)|Vẽ một hình dạng được xác định trước với khả năng tùy chỉnh tô màu và đường viền. |
|![todo:image_alt_text](symbology_2.png)|**Đường thẳng**|[SimpleLine](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simpleline)|Vẽ một đường thẳng với kiểu dáng có thể tùy chỉnh.|
|![todo:image_alt_text](symbology_3.png)|**Tô màu**|[SimpleFill](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/simplefill)|Tô màu một đa giác hoặc khu vực được giới hạn bởi một đường thẳng với khả năng tùy chỉnh tô màu và đường viền.|
Ngoài các biểu tượng thực hiện vẽ, còn có một số biểu tượng khác cho phép kết hợp các biểu tượng khác để tạo ra các hình ảnh trực quan phức tạp hơn.

|**Biểu tượng**|**Lớp API**|**Mô tả**|
| :- | :- | :- |
|**Biểu tượng phân lớp**|[LayeredSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/layeredsymbolizer)|Vẽ một đối tượng với nhiều biểu tượng chồng lên nhau|
|**Biểu tượng hình học hỗn hợp**|[MixedGeometrySymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/mixedgeometrysymbolizer)|Vẽ các đối tượng từ các lớp chứa các hình học hỗn hợp với một biểu tượng cụ thể cho mỗi loại hình học|
|**Biểu tượng dựa trên quy tắc**|[RuleBasedSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/rulebasedsymbolizer)|Chọn một biểu tượng để áp dụng cho một đối tượng theo các quy tắc do người dùng chỉ định.|
|**Biểu tượng cụm điểm đánh dấu**|[MarkerCluster](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/markercluster)|Vẽ cụm của các điểm đánh dấu, nhóm các mục này.|
|**Biểu tượng tạo hình học**|[GeometryGenerator](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/geometrygenerator)|Cho phép thay thế hình học của đối tượng trước khi hiển thị.|
|**Biểu tượng Null**|[NullVectorSymbolizer](https://reference.aspose.com/gis/net/aspose.gis.rendering.symbolizers/nullvectorsymbolizer)|Không vẽ gì cả. Hữu ích khi kết hợp với các biểu tượng khác, chẳng hạn như biểu tượng dựa trên quy tắc.|
