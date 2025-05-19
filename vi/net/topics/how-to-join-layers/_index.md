---
title: "Cách Kết Hợp Lớp Sử Dụng Hình Học hoặc Thuộc Tính"
type: docs
url: /vi/net/how-to-join-layers
weight: 70
---

## Tóm tắt

Trong GIS, việc kết hợp là một cơ chế mạnh mẽ để kết hợp thông tin từ các lớp khác nhau dựa trên thuộc tính chung hoặc mối quan hệ không gian. Việc kết hợp cho phép bạn hợp nhất dữ liệu thuộc tính từ một lớp (lớp nguồn) với một lớp khác (lớp mục tiêu) bằng cách sử dụng một trường chung hoặc vị trí không gian. Cách thứ nhất là kết hợp dữ liệu theo khóa (thuộc tính trong bảng). Bằng cách sử dụng một trường chung, chẳng hạn như một khóa duy nhất, bạn có thể liên kết các bản ghi trong một bảng với các bản ghi trong bảng khác. Phương pháp thứ hai là kết hợp dữ liệu theo vị trí (không gian). Chúng tôi hỗ trợ cả hai phương pháp và cung cấp cho bạn cơ hội sử dụng chúng tùy thuộc vào nhu cầu của mình.

Hãy giả định rằng bạn đã nhận được dữ liệu mô tả phần trăm thay đổi dân số ở các quận khác nhau, và bạn muốn tạo một số bản đồ tăng trưởng dân số dựa trên thông tin này. Trong khi dữ liệu dân số của bạn được lưu trữ trong một bảng trong cơ sở dữ liệu của mình và chia sẻ một trường chung với lớp của bạn, bạn có thể kết hợp dữ liệu này với các đối tượng địa lý của mình và sử dụng các trường bổ sung để gắn nhãn, phân loại, truy vấn hoặc phân tích các đối tượng lớp.

Thông thường, bạn thực hiện việc kết hợp dữ liệu dựa trên giá trị trường tồn tại trong cả hai bảng. Tên trường không nhất thiết phải khớp nhau, nhưng kiểu dữ liệu phải giống nhau - số với số, chuỗi với chuỗi và vân vân. Bạn có thể thực hiện việc kết hợp dữ liệu bằng công cụ xử lý địa lý "Add Join". Khi kết hợp các thuộc tính, các trường đã kết hợp sẽ được thêm động vào bảng hiện có. Các thuộc tính trường như bí danh, khả năng hiển thị và định dạng số được bảo tồn khi thêm hoặc xóa kết hợp.

## Khả năng kết hợp theo trường khóa

- Phương pháp này cho phép bạn **liên kết các bản ghi từ các bảng khác nhau** dựa trên một trường khóa chung. Bạn có thể chỉ định trường khóa để sử dụng cho việc so sánh để thiết lập mối quan hệ giữa các bản ghi. Điều này đặc biệt hữu ích khi bạn cần hợp nhất dữ liệu dựa trên mã xác định hoặc thuộc tính duy nhất khác.

Chỉ định phương pháp so sánh dữ liệu dựa trên trường khóa:

- Bạn có thể định nghĩa **các phương pháp so sánh khác nhau** cho trường khóa khi hợp nhất dữ liệu. Ví dụ: bạn có thể chọn có sự khớp chính xác, so sánh dựa trên một mẫu hoặc trong phạm vi giá trị. Điều này cho phép xác định mối quan hệ giữa các bản ghi chính xác hơn và cung cấp quyền kiểm soát quá trình hợp nhất dữ liệu.

Chỉ định danh sách tên thuộc tính để hợp nhất:

- Khi hợp nhất dữ liệu, bạn có thể chỉ định **các thuộc tính cụ thể** mà bạn muốn hợp nhất. Điều này cho phép bạn chọn chỉ các thuộc tính cần thiết để hợp nhất và quản lý cấu trúc của bảng kết quả.

## Khả năng kết hợp bằng hình học

- Phương pháp này cho phép bạn liên kết dữ liệu dựa trên **vị trí không gian** của chúng. Bạn có thể định nghĩa bán kính tìm kiếm trong đó các đối tượng hình học gần nhất sẽ được tìm kiếm để hợp nhất. Điều này hữu ích khi bạn cần kết hợp dữ liệu dựa trên vị trí địa lý của chúng.

Kiểm soát bán kính tìm kiếm để tìm các đối tượng hình học gần nhất:

- Bạn có thể kiểm soát **bán kính tìm kiếm** khi hợp nhất dữ liệu dựa trên vị trí. Bằng cách chỉ định giá trị bán kính, bạn xác định khoảng cách trong đó các đối tượng gần nhất sẽ được tìm kiếm để hợp nhất. Điều này cung cấp quyền kiểm soát đối tượng nào sẽ tham gia vào quá trình hợp nhất dữ liệu dựa trên mối quan hệ không gian của chúng.

## Dự án Demo

Để hiểu rõ hơn về chức năng của thư viện của chúng tôi, hãy xem xét [một ví dụ về cách sử dụng](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Layers.Join). Mã này minh họa cách kết hợp các lớp vector bằng thuộc tính hoặc hình học.

Mã được cung cấp bao gồm hai phương thức, JoinByIndex() và JoinByCoords(), trình bày các thao tác kết hợp dữ liệu bằng cách sử dụng lớp LayerConstructor.

Trong phương thức JoinByIndex():

- Danh sách các hình học với các thuộc tính liên quan được tạo.

- Một đối tượng LayerConstructor được khởi tạo.

- Phương thức tạo một lớp vector và một lớp hình học bằng cách sử dụng các hình học được cung cấp.

- Lớp hình học được kết hợp dựa trên mã định danh duy nhất ("Id") bằng phương thức JoinLayersById().

- Lớp vector đã kết hợp kết quả được trả về.

Trong phương thức JoinByCoords():

- Danh sách các hình học với các thuộc tính liên quan được tạo.

- Một đối tượng LayerConstructor được khởi tạo.

- Các lớp hình học được tạo bằng cách sử dụng các hình học được cung cấp.

- Các lớp hình học được kết hợp dựa trên tọa độ khớp nhau bằng phương thức JoinLayersByCoords().

- Lớp vector đã kết hợp kết quả được trả về.

Tóm lại, các phương pháp này trình bày hai cách tiếp cận khác nhau để kết hợp dữ liệu: một dựa trên mã định danh duy nhất và phương pháp còn lại dựa trên tọa độ khớp nhau. Lớp LayerConstructor tạo điều kiện cho các thao tác kết hợp dữ liệu này.

## Tùy chọn Kết hợp cho Chỉ mục

Lớp JoinOptions cung cấp một tập hợp các tùy chọn để cấu hình việc kết hợp lớp. Hãy đi sâu hơn vào từng tùy chọn:

- **JoinAttributeName**: Tùy chọn này cho phép bạn chỉ định tên thuộc tính từ lớp đã kết hợp mà giá trị của nó sẽ được sử dụng trong so sánh điều kiện. Nó thiết lập kết nối giữa hai lớp dựa trên thuộc tính này.

- **TargetAttributeName**: Với tùy chọn này, bạn có thể chỉ định tên thuộc tính từ lớp chính sẽ được so sánh với thuộc tính từ lớp đã kết hợp. Nó giúp xác định các đối tượng khớp giữa các lớp.

- **JoinAttributeNames**: Tùy chọn này cho phép bạn chỉ định danh sách các tên thuộc tính mà bạn muốn kết hợp. Nếu danh sách này bị bỏ trống hoặc đặt thành null, tất cả các thuộc tính từ lớp đã kết hợp sẽ được bao gồm trong thao tác kết hợp. Tuy nhiên, bằng cách chọn các tên thuộc tính cụ thể, bạn có thể kiểm soát các thuộc tính được kết hợp, điều này có thể hữu ích để tối ưu hóa việc sử dụng bộ nhớ và thời gian xử lý.

- **ConditionComparer**: Tùy chọn này cho phép bạn định nghĩa logic tùy chỉnh để so sánh giá trị thuộc tính giữa các đối tượng của hai lớp. Theo mặc định, nó sử dụng trình so sánh EqualityComparer.Default, kiểm tra sự bằng nhau. Tuy nhiên, bạn có thể cung cấp trình so sánh tùy chỉnh của riêng mình triển khai IEqualityComparer cho các yêu cầu so sánh chuyên biệt hơn.

- **JoinedAttributesPrefix**: Tùy chọn này cho phép bạn chỉ định chuỗi tiền tố cho tên thuộc tính của lớp đã kết hợp. Giá trị mặc định là "joined_", có nghĩa là các thuộc tính đã kết hợp sẽ được thêm tiền tố "joined_" trong lớp đã kết hợp kết quả. Tiền tố này giúp phân biệt các thuộc tính đã kết hợp với các thuộc tính ban đầu của lớp chính.

Lớp JoinOptions cung cấp sự linh hoạt và kiểm soát đối với nhiều khía cạnh của quá trình kết hợp lớp. Bạn có thể chỉ định các thuộc tính để kết hợp, tùy chỉnh logic so sánh và xác định tiền tố cho các thuộc tính đã kết hợp kết quả. Các tùy chọn này cho phép bạn điều chỉnh thao tác kết hợp theo nhu cầu cụ thể của mình và đạt được những hiểu biết sâu sắc từ các lớp đã hợp nhất.

## Tùy chọn Kết hợp cho Hình học

Lớp **JoinByGeometryOptions** đại diện cho các tùy chọn để kết hợp các lớp dựa trên hình học. Hãy khám phá chức năng của từng tùy chọn:

- **Radius**: Tùy chọn này chỉ định bán kính trong đó hình học đã kết hợp sẽ được tìm kiếm. Nó xác định mức độ gần gũi mà các đối tượng từ lớp chính sẽ khớp với các đối tượng từ lớp đã kết hợp dựa trên mối quan hệ không gian của chúng.

- **ConditionComparer**: Tùy chọn này cho phép bạn định nghĩa logic tùy chỉnh để so sánh giá trị thuộc tính từ các đối tượng của hai lớp. Theo mặc định, nó sử dụng EqualityComparer. Default, kiểm tra sự bằng nhau. Tuy nhiên, bạn có thể cung cấp trình so sánh tùy chỉnh của riêng mình triển khai IEqualityComparer cho các yêu cầu so sánh cụ thể hơn.

- **JoinedAttributesPrefix**: Tùy chọn này cho phép bạn chỉ định chuỗi tiền tố cho tên thuộc tính của lớp đã kết hợp. Giá trị mặc định là "joined_", có nghĩa là các thuộc tính đã kết hợp sẽ được thêm tiền tố "joined_" trong lớp đã kết hợp kết quả. Tiền tố này giúp phân biệt các thuộc tính đã kết hợp với các thuộc tính ban đầu của lớp chính.

Lớp JoinByGeometryOptions cung cấp phương tiện để tùy chỉnh quá trình kết hợp các lớp dựa trên mối quan hệ không gian của chúng. Bằng cách chỉ định bán kính tìm kiếm, bạn có thể kiểm soát phạm vi trong đó hình học sẽ khớp nhau. Điều này cho phép tinh chỉnh thao tác kết hợp dựa trên mức độ gần mong muốn giữa các đối tượng. Tùy chọn cung cấp trình so sánh tùy chỉnh mang lại sự linh hoạt khi so sánh giá trị thuộc tính và tùy chọn thêm tiền tố vào các thuộc tính đã kết hợp giúp phân biệt chúng trong lớp đã kết hợp kết quả.

Sử dụng các tùy chọn này, bạn có thể thực hiện việc hợp nhất dữ liệu nhận biết không gian và thu được những hiểu biết sâu sắc từ các lớp đã kết hợp dựa trên sự gần gũi về không gian và giá trị thuộc tính của chúng.

## Tóm tắt

Cơ chế kết hợp dữ liệu trong GIS cho phép kết hợp các đối tượng hình học với các thuộc tính tương ứng của chúng từ các lớp khác nhau. Điều này cung cấp khả năng phân tích và trích xuất thông tin dựa trên mối quan hệ không gian và thuộc tính trong dữ liệu. Các tùy chọn có sẵn cho phép tùy chỉnh quá trình kết hợp để đáp ứng các yêu cầu cụ thể và nhu cầu phân tích trong dữ liệu GIS.

Việc kết hợp dữ liệu tạo điều kiện thuận lợi cho nhiều tác vụ, bao gồm:

- Tìm các đối tượng đáp ứng tiêu chí không gian cụ thể, chẳng hạn như xác định tất cả các tòa nhà trong bán kính 500 mét từ một điểm cụ thể.

- Kết hợp dữ liệu địa lý để tạo ra cái nhìn tổng quan toàn diện và thông tin hơn về một tình huống.

- Phân tích giá trị thuộc tính của các đối tượng dựa trên các điều kiện không gian cụ thể để xác định xu hướng và mẫu.

Các tùy chọn kết hợp dữ liệu cho phép cấu hình chính xác quá trình khớp đối tượng. Các tùy chọn này bao gồm lựa chọn các thuộc tính để kết hợp, định nghĩa logic tùy chỉnh để so sánh giá trị thuộc tính và thêm tiền tố vào tên thuộc tính của dữ liệu đã kết hợp. Những tùy chọn này cung cấp sự linh hoạt và khả năng thích ứng với quá trình kết hợp, đáp ứng các mục tiêu và mục đích phân tích dữ liệu trong GIS.

Cơ chế kết hợp dữ liệu đóng một vai trò quan trọng trong việc tích hợp và phân tích dữ liệu địa lý, mang lại sự hiểu biết toàn diện hơn về bản chất không gian và thuộc tính của các đối tượng được điều tra.