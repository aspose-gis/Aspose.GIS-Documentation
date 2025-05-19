---
title: "Cài đặt"
second_title: Aspose.GIS for .NET
type: docs
url: /vi/net/installation/
weight: 40
keywords: thư viện gis c#, thư viện gis .net
description: Cài đặt thư viện hoặc API GIS C#.NET từ NuGet bằng giao diện người dùng Package Manager hoặc Console, từ ZIP Archive. Nó cũng có thể được sử dụng trong .NET Core và hệ điều hành Linux.
---

## **Cài đặt Aspose.GIS**
### **Từ NuGet**
Để cài đặt Aspose.GIS, bạn sử dụng giao diện người dùng Package Manager hoặc Package Manager Console. Khi bạn cài đặt một gói, NuGet sẽ ghi lại sự phụ thuộc trong tệp dự án của bạn hoặc tệp packages.config.
#### **Giao diện người dùng Package Manager**
1. Trong Solution Explorer, nhấp chuột phải vào **References** và chọn **Manage NuGet Packages**.

![todo:image_alt_text](installation_1.png)

1. Kiểm tra xem "nuget.org" đã được chọn làm **Package Source**, chọn tab Browse, tìm kiếm Aspose.GIS, chọn gói đó trong danh sách và nhấp vào Install:

![todo:image_alt_text](installation_2.png)

1. Làm quen với [Thỏa thuận cấp phép người dùng cuối của Aspose](https://about.aspose.com/legal/eula).
1. Nếu được nhắc xem lại các thay đổi, chọn **OK**.
#### **Package Manager Console**
1. Chọn menu lệnh **Tools** > **NuGet Package Manager** > **Package Manager Console**.
1. Sau khi console mở, hãy đảm bảo rằng danh sách thả xuống **Default project** hiển thị dự án mà bạn muốn cài đặt gói vào đó. Nếu bạn có một dự án duy nhất trong giải pháp, nó đã được chọn.

![todo:image_alt_text](installation_3.png)

1. Nhập lệnh Install-Package Aspose.GIS. Cửa sổ console sẽ hiển thị đầu ra cho lệnh.
### **Với MSI Installer hoặc Từ ZIP Archive**
Ngoài việc cài đặt NuGet, bạn có thể tải xuống Aspose.GIS từ [phần Downloads](https://downloads.aspose.com/gis/net) được đóng gói dưới dạng MSI installer hoặc ZIP archive.

## **Hướng dẫn dành riêng cho nền tảng**
### **Linux**
Khi sử dụng chức năng hiển thị bản đồ của Aspose.GIS trên Linux, hãy đảm bảo rằng thư viện System.Drawing.Common được cấu hình chính xác. Nếu bạn nhận được thông báo lỗi tương tự như 

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

điều đó có nghĩa là các phụ thuộc của System.Drawing.Common đang bị thiếu trong hệ thống. Để khắc phục điều đó, hãy chạy:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev

## **Yêu cầu hệ thống cho Aspose.GIS for .NET**
Tất cả các thành phần .NET của Aspose đều yêu cầu quyền tập hợp Full Trust.

Aspose.GIS bao gồm hai biến thể của assembly được xây dựng cho

- .NET Framework 4.7,
- .NET Standard 2.0.

### **.NET Framework v4.7 trở lên**
Hệ điều hành: 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `Cả phiên bản 32 và 64 bit đều được hỗ trợ.
### **.NET Core v2.0 trở lên**
` `Hệ điều hành:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (phiên bản 1607) hoặc các phiên bản mới hơn
- Microsoft Windows Server 2008 R2 SP1 (Full Server hoặc Server Core), 2012 SP1 (Full Server hoặc Server Core), 2012 R2 (Full Server hoặc Server Core), 2016 trở lên (Full Server, Server Core hoặc Nano Server)
- macOS 10.12 "Sierra" và các phiên bản mới hơn
- Linux (64-bit, x86_64 hoặc amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64-bit, arm32), 8.7 trở lên
  - Ubuntu 18.04 (64-bit, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 trở lên
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 trở lên
  - Alpine Linux 3.7 trở lên

Thông tin chi tiết hơn có sẵn trong Hướng dẫn .NET Core: [Yêu cầu Windows](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [Yêu cầu macOS](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Yêu cầu Linux](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).

### **Hỗ trợ thử nghiệm**
- Mono 5.4 trở lên
- Xamarin:
  - Xamarin.iOS: phiên bản 10.14 hoặc mới hơn
  - Xamarin.Android: phiên bản 8.0 trở lên
  - Xamarin.Mac: phiên bản 3.8 trở lên
