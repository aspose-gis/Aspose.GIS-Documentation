---
title: "Ứng dụng Console Tạo Lớp"
type: docs
url: /vi/net/layer-generator-console
weight: 50
---

## Tóm tắt

Ứng dụng console này được thiết kế để tạo các đối tượng hình học thuộc nhiều loại khác nhau và lưu chúng ở định dạng đã chọn. Nó cho phép bạn tạo điểm, đa giác và đường gấp khúc, chỉ định số lượng đối tượng cần tạo và chọn định dạng đầu ra để lưu.

## Cách sử dụng

Cú pháp lệnh:

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

Đối số:

```
-t, --type: Loại hình học. Một trong các loại sau: Point, Polygon, Polyline.

-c, --count: Bắt buộc. Số lượng đối tượng cần tạo. Ví dụ: 15.

-f, --fileName: Bắt buộc. Tên tệp để lưu. Chỉ định tên tệp và phần mở rộng. Ví dụ: test.json.

-o, --outputFormat: Định dạng đầu ra. Xem các định dạng tệp được hỗ trợ tại đây.

--help: Hiển thị thông tin trợ giúp cho lệnh.

--version: Hiển thị thông tin phiên bản ứng dụng.
```

Ví dụ về một lệnh để tạo 15 điểm ngẫu nhiên và lưu chúng vào một tệp ở định dạng "test.json":

```
app.exe -t Point -c 15 -f test.json -o json
```

## Cài đặt và Giấy phép

Nếu bạn muốn sử dụng ứng dụng, bạn cần tải xuống kho lưu trữ và giải nén nó. Vui lòng làm theo liên kết dưới đây.

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

Mặc dù Ứng dụng Console Tạo Lớp Aspose.GIS là miễn phí, nhưng Aspose.GIS .NET được cấp phép như bình thường, vì vậy bạn có thể tái sử dụng giấy phép của mình thông qua ứng dụng hoặc đánh giá ứng dụng bằng cách sử dụng Aspose.GIS .NET ở chế độ dùng thử hoặc yêu cầu Giấy phép tạm thời.

## Kết luận

Trình tạo đối tượng hình học là một ứng dụng console tiện dụng giúp bạn tạo các mẫu hình học thuộc nhiều loại khác nhau và lưu chúng ở định dạng mong muốn. Đây là một công cụ hữu ích để làm việc với dữ liệu không gian địa lý và phát triển hệ thống thông tin địa lý.
