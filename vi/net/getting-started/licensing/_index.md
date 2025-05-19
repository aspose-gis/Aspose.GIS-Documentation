---
title: "Licensing"
second_title: Aspose.GIS for .NET
type: docs
url: /vi/net/licensing/
weight: 50
keywords: c# gis library, .net gis library
description: Đánh giá thư viện GIS C# .NET hoặc API với một số hạn chế. Áp dụng Giấy phép bằng đối tượng Tệp hoặc Luồng hoặc dưới dạng Tài nguyên nhúng.
---

## **Đánh giá Aspose.GIS for .NET**
Bạn có thể tải xuống Aspose.GIS for .NET miễn phí. Trước khi bạn áp dụng giấy phép, thành phần hoạt động ở chế độ đánh giá. Khi bạn mua giấy phép và thêm một vài dòng mã để áp dụng giấy phép, các hạn chế đánh giá sẽ bị loại bỏ.

{{% alert color="primary" %}} Nếu bạn muốn kiểm tra Aspose.GIS mà không có giới hạn của chế độ đánh giá, bạn có thể yêu cầu Giấy phép tạm thời 30 ngày. Vui lòng tham khảo [Nhận giấy phép tạm thời](https://purchase.aspose.com/temporary-license). {{% /alert %}} 
### **Hạn chế của Chế độ Đánh giá**
Khi thực thi ở chế độ đánh giá (không có giấy phép áp dụng), Aspose.GIS cung cấp chức năng sản phẩm đầy đủ ngoại trừ một số hạn chế đánh giá.

1. Không quá **15 tài liệu** có thể được mở và/hoặc tạo **mỗi giờ**
2. Không quá **100 đối tượng** có thể được truy cập trong mỗi tài liệu (đọc hoặc ghi)
3. Không quá **10 000 dữ liệu raster** có thể được truy cập trong mỗi tài liệu (đọc hoặc ghi).
4. Số lượng đối tượng tối đa được phép trong một tài liệu để thực hiện các thao tác chuyển đổi là **50**

Khi thực thi ở chế độ giấy phép, bạn có thể xử lý số lượng tài liệu và đối tượng không giới hạn.
## **Áp dụng Giấy phép**
Giấy phép là tệp XML đơn giản chứa các chi tiết như tên sản phẩm, số lượng nhà phát triển mà nó được cấp phép cho, ngày hết hạn đăng ký, v.v. Tệp được ký kỹ thuật số, vì vậy đừng sửa đổi tệp. Ngay cả việc thêm ngẫu nhiên một dòng ngắt vào tệp cũng sẽ làm mất hiệu lực của nó.

Bạn cần đặt giấy phép trước khi sử dụng Aspose.GIS nếu bạn muốn tránh các hạn chế đánh giá của nó. Chỉ cần đặt giấy phép một lần cho mỗi ứng dụng (hoặc quy trình).
### **Đặt Giấy phép trong Aspose.GIS for .NET**
Trong Aspose.GIS, giấy phép có thể được tải từ tệp, luồng hoặc tài nguyên nhúng. Aspose.GIS cố gắng tìm giấy phép ở các vị trí sau:

- Đường dẫn rõ ràng
- Thư mục chứa Aspose.GIS.dll
- Thư mục chứa assembly gọi Aspose.GIS.dll
- Thư mục chứa assembly khởi động (exe của bạn)
- Một tài nguyên nhúng trong assembly gọi Aspose.GIS.dll. Có hai phương pháp phổ biến để đặt giấy phép, được thảo luận dưới đây:
### **Áp dụng Giấy phép bằng đối tượng Tệp hoặc Luồng**
Cách dễ nhất để đặt giấy phép là đặt tệp giấy phép vào cùng thư mục với Aspose.GIS.dll và chỉ định tên tệp mà không cần đường dẫn của nó.

{{< highlight java >}}

 // Khởi tạo một phiên bản của giấy phép và đặt tệp giấy phép thông qua đường dẫn của nó
 
Aspose.Gis.License license = new Aspose.Gis.License();
 
license.SetLicense("Aspose.GIS.lic");
 
{{< /highlight >}}

{{< highlight java >}}

 // Khởi tạo một phiên bản của giấy phép và đặt giấy phép thông qua một luồng
 
Aspose.Gis.License license = new Aspose.Gis.License();
 
license.SetLicense(myStream);
 
{{< /highlight >}}

Khi bạn gọi phương thức SetLicense, tên giấy phép phải giống với tên tệp giấy phép của bạn. Ví dụ: bạn có thể thay đổi tên tệp giấy phép thành "Aspose.GIS.lic.xml". Sau đó trong mã của bạn, bạn nên sử dụng tên giấy phép đã sửa đổi (tức là Aspose.GIS.lic.xml) cho phương thức SetLicense.

## **Bao gồm Tệp Giấy phép dưới dạng Tài nguyên nhúng**
Một cách khác để đóng gói giấy phép cùng với ứng dụng của bạn và đảm bảo rằng nó sẽ không bị mất là bao gồm nó dưới dạng tài nguyên nhúng vào một trong các assembly gọi DLL của thành phần (được bao gồm trong Aspose.GIS). Để bao gồm tệp giấy phép dưới dạng tài nguyên nhúng, hãy thực hiện các bước sau:

- Trong Visual Studio, hãy đưa tệp giấy phép (.lic) vào dự án bằng menu Tệp | Thêm mục hiện có...
- Chọn tệp trong Solution Explorer và đặt Hành động xây dựng thành Tài nguyên nhúng trong cửa sổ Thuộc tính
- Để truy cập giấy phép được nhúng trong assembly (dưới dạng tài nguyên nhúng), không cần gọi các phương thức GetExecutingAssembly và GetManifestResourceStream của lớp System.Reflection.Assembly của Microsoft .NET Framework. Tất cả những gì bạn cần làm là chỉ cần thêm tệp giấy phép dưới dạng tài nguyên nhúng vào dự án của mình và chuyển tên tệp giấy phép vào phương thức License.SetLicense. Lớp Giấy phép sẽ tự động tìm tệp giấy phép trong các tài nguyên nhúng.

Vui lòng xem ví dụ được cung cấp bên dưới để hiểu phương pháp này đặt giấy phép (nhúng) trong ứng dụng của bạn.

{{< highlight java >}}

 // Khởi tạo lớp Giấy phép
 
Aspose.Gis.License license = new Aspose.Gis.License();
 
// Chỉ chuyển tên tệp giấy phép được nhúng trong assembly
 
license.SetLicense("Aspose.GIS.lic");
 
{{< /highlight >}}

## **Áp dụng Khóa Đo lường**
[API của Aspose.GIS for .NET](/gis/net/) cho phép các nhà phát triển áp dụng khóa đo lường. Đây là một cơ chế cấp phép mới. Cơ chế cấp phép mới sẽ được sử dụng cùng với phương pháp cấp phép hiện có. Những khách hàng muốn thanh toán dựa trên mức sử dụng của các tính năng API có thể sử dụng giấy phép đo lường. Để biết thêm chi tiết, vui lòng tham khảo phần [Câu hỏi thường gặp về cấp phép đo lường](https://purchase.aspose.com/faqs/licensing/metered).

Một lớp mới **Metered** đã được giới thiệu để áp dụng khóa đo lường. Dưới đây là mã mẫu minh họa cách đặt khóa công khai và riêng tư đo lường.

**[C#]**

{{< highlight csharp >}}

 // đặt khóa công khai và riêng tư đo lường
 
Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();
 
// Truy cập thuộc tính setMeteredKey và chuyển khóa công khai và riêng tư làm tham số
 
metered.SetMeteredKey("*****", "*****");
 
// THỰC HIỆN XỬ LÝ
 
// nhận lượng tiêu thụ đo lường
 
decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();
 
// Hiển thị thông tin
 
Console.WriteLine("Amount Consumed : " + amount.ToString());
 

{{< /highlight >}}
