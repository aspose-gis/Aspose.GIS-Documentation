---
title: "Cách Vẽ Hình Học trên Bản Đồ"
type: docs
url: /vi/net/how-to-draw-geometry
weight: 70
---

Để tạo và hiển thị các đối tượng hình học trên bản đồ, bạn cần bắt đầu bằng cách **tạo một đối tượng hình học**. Có hai phương pháp bạn có thể sử dụng:

- **Constructor cho Mỗi Loại Tính Năng Hình Học**
Phương pháp này liên quan đến việc sử dụng constructor tùy chỉnh cho mỗi loại tính năng hình học. Ví dụ: để tạo một điểm, bạn sẽ sử dụng mã sau:

```
Point point = new Point(40.7128, -74.006);
```

Tuy nhiên, phương pháp này có thể trở nên phức tạp và khó quản lý khi tạo các đối tượng phức tạp như polylines hoặc collections. Do đó, nhà phát triển có thể cần thêm nhiều dòng mã, làm giảm tính dễ đọc của mã. Đảm bảo tính toàn vẹn dữ liệu trong quá trình khởi tạo cũng có thể khó khăn. Ví dụ: hãy xem xét ví dụ sau tạo một đa giác có lỗ bên trong:

```
Polygon polygon = new Polygon();

LinearRing ring = new LinearRing();
ring.AddPoint(50.02, 36.22);
ring.AddPoint(49.99, 36.26);
ring.AddPoint(49.97, 36.23);
ring.AddPoint(49.98, 36.17);
ring.AddPoint(50.02, 36.22);

LinearRing hole = new LinearRing();
hole.AddPoint(50.00, 36.22);
hole.AddPoint(49.99, 36.20);
hole.AddPoint(49.98, 36.23);
hole.AddPoint(50.00, 36.24);
hole.AddPoint(50.00, 36.22);

polygon.ExteriorRing = ring;
polygon.AddInteriorRing(hole);
```

Một bất lợi khác của phương pháp này là thiếu tính đồng nhất của dữ liệu để khởi tạo. Bạn không thể tạo một kho lưu trữ các hằng số hoặc tệp trong dự án của mình.

- **WKT (Well-Known Text)**
Phương pháp này liên quan đến việc tạo hình học từ WKT (Well-Known Text), cung cấp một cách tiêu chuẩn hóa để tạo hình học. Mã sau minh họa cách tạo một điểm và một đường:

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

Mặc dù phương pháp này có thể giảm hiệu suất một chút do cần phải phân tích chuỗi, nhưng nó đơn giản hóa việc tạo các đối tượng phức tạp hơn.

Bạn có thể tìm thêm chi tiết về WKT trong bài viết sau: "Xuất và Nhập Dữ liệu từ/đến WKT và WKB."

Hiển Thị Các Đối Tượng Hình Học trên Bản Đồ
Khi bạn đã tạo một đối tượng hình học, bước tiếp theo là hiển thị nó trên bản đồ. Mặc dù bản đồ có thể hiển thị các lớp được tải từ nhiều nguồn và định dạng khác nhau, nhưng InMemoryLayer là một lớp không yêu cầu nguồn.

**Để hiển thị đối tượng hình học của bạn**, bạn có thể tạo một InMemoryLayer và thêm đối tượng vào đó:

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

Bây giờ bạn có thể **hiển thị lớp này trên bản đồ và tạo một tệp ở một trong các định dạng được hỗ trợ**, chẳng hạn như SVG, với mã sau:

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

Khi bạn đã thêm lớp và hiển thị nó trên bản đồ, bạn có thể lưu nó ở bất kỳ định dạng nào được hỗ trợ. Trong ví dụ này, định dạng SVG được chọn để tránh các vấn đề tiềm ẩn với hỗ trợ Bitmap. Điều quan trọng cần lưu ý là Net 6.0 có hỗ trợ Bitmap hạn chế, điều này có thể dẫn đến các hạn chế như không thể hiển thị hình ảnh Bitmap bằng Blazor WebAsm trên máy khách. Do đó, khi chọn định dạng để lưu bản đồ của bạn, điều quan trọng là phải xem xét những hạn chế của nền tảng mục tiêu và chọn một định dạng tương thích với nó.

Bài viết giải thích cách tạo và hiển thị các đối tượng hình học trên bản đồ với kiểu mặc định, đơn giản. Tuy nhiên, thư viện Aspose cung cấp nhiều tùy chọn tạo kiểu có thể được tùy chỉnh để phù hợp với nhu cầu của bạn. Để khám phá những tùy chọn này, chúng tôi khuyên bạn nên tham khảo [tài liệu Aspose.MapRendering]( https://docs.aspose.com/gis/net/map-rendering/), cung cấp thông tin chi tiết về cách sử dụng các kỹ thuật tạo kiểu khác nhau để nâng cao tính hấp dẫn trực quan của bản đồ của bạn.

**Tóm lại**, để tạo các đối tượng hình học trên bản đồ, bạn có thể sử dụng constructor cho mỗi loại tính năng hình học hoặc tạo hình học từ WKT. Để hiển thị đối tượng, hãy đặt nó trên một lớp và hiển thị lớp trên bản đồ với kiểu bản đồ mặc định. Lưu bản đồ ở định dạng được hỗ trợ, chẳng hạn như SVG, và sử dụng thư viện của chúng tôi để khám phá các tùy chọn tạo kiểu. Ngoài ra, thư viện của chúng tôi cung cấp cơ hội để xem ví dụ hoàn chỉnh bằng cách nhấp vào [liên kết]( https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer) được cung cấp trong tài liệu, có thể giúp bạn hiểu cách triển khai các kỹ thuật này trong dự án của riêng mình.
