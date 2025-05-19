---
title: Cách Chạy Aspose.GIS trong Docker
type: docs
description: "Chạy Aspose.GIS trong một container Docker cho Linux, Windows Server và bất kỳ hệ điều hành nào."
weight: 139
url: /vi/net/how-to-run-aspose-gis-in-docker/
---

## Yêu cầu tiên quyết

- Docker phải được cài đặt trên hệ thống của bạn. Để biết thông tin về cách cài đặt Docker trên Windows hoặc Mac, hãy tham khảo các liên kết trong phần "Xem thêm".

- Visual Studio 2022.

- NET Core 3.1 SDK được sử dụng trong ví dụ.


## Ứng dụng Hello World

Trong ví dụ này, bạn tạo một ứng dụng console Hello World đơn giản tạo ra một đường cong phức hợp và lưu nó vào các tệp. Sau đó, ứng dụng có thể được xây dựng và chạy trong Docker.

### Tạo ứng dụng Console

Để tạo chương trình Hello World, hãy làm theo các bước sau:
1. Khi Docker đã được cài đặt, hãy đảm bảo rằng nó sử dụng Container Linux (mặc định). Nếu cần thiết, chọn tùy chọn Chuyển sang container Linux từ menu Docker Desktops.
1. Trong Visual Studio, tạo một ứng dụng console NET Core 3.1.<br>
![todo:image_alt_text](create-a-new-project.png)<br>
1. Cài đặt phiên bản Aspose.GIS mới nhất từ NuGet.<br>
![todo:image_alt_text](nuget-aspose-gis.png)<br>
1. Vì ứng dụng sẽ chạy trên Linux, các tài sản Linux gốc phù hợp phải được cài đặt. Bắt đầu với hình ảnh cơ sở dotnet core sdk 3.1 và cài đặt libgdiplus libc6-dev.
1. Khi tất cả các phụ thuộc cần thiết đã được thêm vào, hãy viết một chương trình đơn giản tạo ra một đường cong phức hợp:<br>
**.NET**<br>
{{< highlight csharp >}}
using System.IO;
using Aspose.Gis.Geometries;
using Aspose.Gis;

namespace Aspose.GIS.Docker.Sample
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string path = Path.Combine("TestOut", "CreateCompoundCurve_out.shp");
            using (VectorLayer layer = VectorLayer.Create(path, Drivers.Shapefile))
            {
                var feature = layer.ConstructFeature();
                // create an 'S' letter (starts at bottom left end)
                var compoundCurve = new CompoundCurve();

                var bottom = (ILineString)Geometry.FromText("LineString (0 0, 3 0)");
                var firstArc = (ICircularString)Geometry.FromText("CircularString (3 0, 4 1, 3 2)");
                var middle = (ILineString)Geometry.FromText("LineString (3 2, 1 2)");
                var secondArc = (ICircularString)Geometry.FromText("CircularString (1 2, 0 3, 1 4)");
                var top = (ILineString)Geometry.FromText("LineString (1 4, 4 4)");

                compoundCurve.AddCurve(bottom);
                compoundCurve.AddCurve(firstArc);
                compoundCurve.AddCurve(middle);
                compoundCurve.AddCurve(secondArc);
                compoundCurve.AddCurve(top);
                feature.Geometry = compoundCurve;

                layer.Add(feature);
            }
        }
    }
}
{{< /highlight >}}

Lưu ý rằng thư mục �TestOut� được chỉ định là một thư mục đầu ra để lưu trữ các tài liệu đầu ra. Khi chạy ứng dụng trong Docker, một thư mục trên máy chủ sẽ được gắn vào thư mục này trong container. Điều này sẽ cho phép bạn dễ dàng xem kết quả do Aspose.GIS tạo ra trong container Docker.

### Cấu hình Dockerfile

Bước tiếp theo là tạo và cấu hình Dockerfile.

1. Tạo Dockerfile và đặt nó bên cạnh tệp giải pháp của ứng dụng của bạn. Giữ tên tệp này không có phần mở rộng (mặc định).
1. Trong Dockerfile, hãy chỉ định:

{{< highlight plain >}}
FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster 
WORKDIR /app
COPY . ./
RUN apt-get update && \
    apt-get install -y --allow-unauthenticated libgdiplus libc6-dev
RUN dotnet publish "Aspose.GIS.Docker.Sample.csproj" -c Release -o /app/out
ENTRYPOINT ["dotnet", "out/Aspose.GIS.Docker.Sample.dll"]
{{< /highlight >}}

Trên đây là một Dockerfile đơn giản, chứa các hướng dẫn sau:

- Hình ảnh SDK được sử dụng. Tại đây, đó là hình ảnh Net 3.1. Docker sẽ tải xuống nó khi quá trình xây dựng chạy. Phiên bản của SDK được chỉ định dưới dạng thẻ.
- Thư mục làm việc, được chỉ định ở dòng tiếp theo.
- Lệnh để cài đặt libgdiplus đang chạy trong container. Điều này là bắt buộc đối với System.Drawing.Common.
- Lệnh sao chép mọi thứ vào container, xuất bản ứng dụng và chỉ định điểm truy cập.

### Xây dựng và Chạy Ứng dụng trong Docker

Bây giờ ứng dụng có thể được xây dựng và chạy trong Docker. Mở dòng lệnh yêu thích của bạn, thay đổi thư mục thành thư mục chứa ứng dụng (thư mục nơi tệp giải pháp và Dockerfile được đặt) và chạy lệnh sau:

{{< highlight plain >}}
docker build -t dockerfile .
{{< /highlight >}}

Lần đầu tiên lệnh này được thực thi có thể mất nhiều thời gian hơn, vì Docker cần tải xuống các hình ảnh cần thiết. Khi lệnh trước hoàn tất, hãy chạy lệnh sau:

{{< highlight plain >}}
docker run --mount type=bind,source=C:\Temp,target=/app/TestOut --rm dockerfile from Docker
{{< /highlight >}}

{{% alert color="primary" %}} 

Hãy chú ý đến đối số mount, vì như đã đề cập trước đó, một thư mục trên máy chủ được gắn vào thư mục của container, để dễ dàng xem kết quả thực thi ứng dụng. Đường dẫn trong Linux phân biệt chữ hoa chữ thường.

{{% /alert %}}


## Ví dụ khác

Để biết thêm các ví dụ về cách bạn có thể sử dụng Aspose.GIS trong Docker, hãy tham khảo [các ví dụ](https://github.com/aspose-gis/Aspose.Gis-for-.NET).


## Xem thêm

- [Cài đặt Docker Desktop trên Windows](https://docs.docker.com/docker-for-windows/install/)
- [Cài đặt Docker Desktop trên Mac](https://docs.docker.com/docker-for-mac/install/)
- [Visual Studio 2022, NET 3.1 SDK](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore31#dependencies)
- Tùy chọn [Chuyển sang container Linux](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers)
