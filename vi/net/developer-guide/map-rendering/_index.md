---
title: Kết xuất Bản đồ thành Hình ảnh SVG, PNG, JPG bằng Thư viện GIS C#
linktitle: "Kết xuất Bản đồ"
type: docs
url: /vi/net/map-rendering/
weight: 50
description: Với API GIS C# , bạn có thể kết xuất bản đồ từ Shapefile, FileGDB, GeoJSON, KML, thực hiện tạo kiểu nâng cao và vẽ bản đồ từ định dạng raster.
---

## **Tổng quan về Kết xuất Bản đồ**
Với Aspose.GIS for .NET C# API, bạn có thể kết xuất bản đồ từ Shapefile, FileGDB, GeoJSON, KML hoặc các [định dạng tệp được hỗ trợ khác](/gis/net/supported-file-formats/) thành SVG, PNG, JPEG hoặc BMP.

Đây là mã C# minh họa cách kết xuất bản đồ từ một shapefile sang SVG bằng cài đặt mặc định:



{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-RenderWithDefaultSettings.cs" >}}



Đây là kết quả:



![map rendering](map_rendering.png)

Hãy xem xét kỹ hơn về mã này.

Trước tiên, chúng ta khởi tạo một đối tượng [Map ](https://reference.aspose.com/gis/net/aspose.gis.rendering/map). Nó đại diện cho một tập hợp các lớp từ nhiều nguồn khác nhau có thể được kết xuất. Bản đồ có kích thước mà nó dự định hiển thị. Ở đây, chúng ta đặt bản đồ rộng 800 pixel và cao 400 pixel.

Lưu ý rằng Map được bao bọc trong câu lệnh using. Điều này là cần thiết vì bản đồ theo dõi tất cả các tài nguyên được thêm vào nó và giải phóng chúng khi chúng ta hoàn thành kết xuất và đối tượng Map bị giải phóng.

Tiếp theo, chúng ta thêm một lớp từ tệp vào bản đồ. Mỗi lớp được kết xuất trên lớp trước đó, theo thứ tự mà chúng được thêm vào bản đồ. Xem thêm chi tiết về cách mở các lớp vector [tại đây](/gis/net/working-with-vector-layers/).

Cuối cùng, chúng ta gọi [Map.Render](https://reference.aspose.com/gis/net/aspose.gis.rendering.map/render/methods/1) để kết xuất bản đồ thành một tệp. Chúng ta chỉ định đường dẫn đến nơi lưu trữ tệp kết quả và trình kết xuất sẽ sử dụng. Lớp [Renderers ](https://reference.aspose.com/gis/net/aspose.gis.rendering/renderers) chứa các tham chiếu đến tất cả các trình kết xuất được bao gồm trong Aspose.GIS. Ví dụ: bạn có thể chỉ định Renderers.Png thay vì Renderers.Svg trong ví dụ trên để kết xuất bản đồ thành tệp PNG

## **Tạo kiểu Nâng cao**
Với API Aspose.GIS, bạn có thể tùy chỉnh kết xuất và kiểu dáng tính năng để đạt được giao diện mong muốn. 

![advanced styling](advanced_styling.png)

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderMap-AddMapLayersAndStyles.cs" >}}
## **Vẽ raster trong bản đồ**
Với Aspose.GIS for .NET, bạn có thể kết xuất một bản đồ từ các định dạng raster.
### **Kết xuất với cài đặt mặc định**
Đây là cách kết xuất bản đồ từ GeoTIFF sang SVG bằng cài đặt mặc định:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawRasterDefaultSettings.cs" >}}

![default raster](default_raster.png)
### **Kết xuất raster bị lệch**
Với Aspose.GIS, bạn có thể kết xuất một raster với các ô raster bị lệch.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawSkewRaster.cs" >}}

![skew raster](skew_raster.png)
### **Kết xuất trong tham chiếu không gian cực**
Aspose.GIS cho phép bạn sử dụng các tham chiếu không gian cực trên quy trình kết xuất bản đồ.

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-RenderRasterFormats-DrawPolarRasterExtent.cs" >}}

![gnomonic countries](gnomonic_countries.png)
