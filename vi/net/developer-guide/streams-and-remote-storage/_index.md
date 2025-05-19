---
title: "Luồng và Lưu trữ Từ xa"
type: docs
url: /vi/net/streams-and-remote-storage/
weight: 70
---

## **Làm việc với các Định dạng Đa tệp**
Một số định dạng dữ liệu GIS chia nội dung thành nhiều tệp. Ví dụ, một shapefile phải có ít nhất ba tệp: *.shp, *.shx và *.dbf. Các định dạng này yêu cầu tất cả các tệp phải được lưu trữ trong một cấu trúc thư mục cụ thể với một mẫu tên tệp được xác định trước.

Đồng thời, các tệp có thể được lưu trữ trên một máy chủ từ xa hoặc một vị trí khác chỉ có thể truy cập thông qua luồng. Luồng thiếu thông tin về tên tệp và cấu trúc thư mục, khiến không thể đối với trình điều khiển định dạng tệp để xác định cách xử lý dữ liệu. Aspose.GIS giải quyết vấn đề này bằng cách cung cấp cơ chế đường dẫn trừu tượng.

Một đường dẫn trừu tượng đại diện cho một đường dẫn đến một tệp (hoặc thư mục) trong một bộ nhớ giống như hệ thống tập tin nào đó. Bộ nhớ có thể là bất cứ thứ gì có khái niệm về tệp và thư mục, từ một kho lưu trữ đến một máy chủ FTP. Nó định nghĩa cách thực hiện các thao tác tệp điển hình, chẳng hạn như mở một tệp hoặc liệt kê một thư mục.

Bạn có thể chỉ định cách thực hiện các thao tác tệp cho bộ nhớ của mình bằng cách triển khai một lớp kế thừa [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) và cung cấp các triển khai cho các phương thức trừu tượng của nó.
## **Ví dụ: Lưu trữ Blob Azure**
Kho lưu trữ Aspose.GIS Examples chứa một ví dụ về việc triển khai đường dẫn trừu tượng tùy chỉnh hoàn chỉnh cho Bộ nhớ Blob Azure. Ví dụ này cho thấy cách đọc trực tiếp một shapefile từ Bộ nhớ Blob Azure. Bạn có thể tìm thấy nó tại đây: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **Định dạng một tệp (GeoJSON, KML)**
Các định dạng dữ liệu GIS như GeoJSON và KML có thể lưu trữ tất cả dữ liệu cho một lớp trong một tệp duy nhất. Nếu bạn có thể lấy được luồng cho tệp, bạn có thể bỏ qua việc triển khai đường dẫn trừu tượng tùy chỉnh và sử dụng phương thức [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) để tạo một đường dẫn trừu tượng cho luồng.
### **Đọc một tệp từ một luồng**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **Ghi một tệp vào một luồng**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
