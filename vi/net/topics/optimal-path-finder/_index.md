---
title: "Optimal Path Finder"
type: docs
url: /vi/net/optimal-path-finder
weight: 70
---

## Summary

Việc tìm kiếm đường đi ngắn nhất trên mạng lưới đường bộ là một quá trình phân tích nhằm xác định cách hiệu quả nhất để di chuyển giữa các điểm trên bản đồ. Công cụ này có thể hữu ích cho việc tạo ra các tuyến đường tối ưu với nhiều điểm dừng hoặc đo khoảng cách và thời gian di chuyển giữa các địa điểm khác nhau. Với mỗi lần gọi, công nghệ của chúng tôi có thể tìm thấy các tuyến đường tối ưu cho một hoặc nhiều phương tiện. Ví dụ: nó có thể giúp người lái xe tìm các tuyến đường tối ưu để giao hàng hoặc xác định khoảng cách đi làm tối ưu từ nhà đến nơi làm việc cho những hành khách khác nhau.

## Algorithm Capabilities

Thư viện của chúng tôi cung cấp khả năng xây dựng **tuyến đường tối ưu giữa hai điểm** trên bản đồ. Nó có các tính năng chính sau:

1. Tìm kiếm đường dẫn tối ưu trên bản đồ, xem xét địa hình và chướng ngại vật: Chúng tôi không chỉ tính đến đường xá mà còn cả các con đường ngoài đường như đường mòn, lối đi dành cho người đi bộ và các chướng ngại vật có thể ảnh hưởng đến việc lựa chọn đường dẫn tối ưu.

2. Tìm kiếm đường dẫn tối ưu chỉ trên đường xá: Nếu bạn cần tìm một tuyến đường chỉ trên đường xá, chúng tôi cung cấp khả năng này. Điều này hữu ích, ví dụ, cho các phương tiện bị hạn chế chỉ được phép di chuyển trên đường xá.

3. Thiết lập tốc độ khác nhau cho các con đường: Chúng tôi có thể gán tốc độ khác nhau cho các con đường khác nhau. Ví dụ: tốc độ cao hơn có thể được đặt cho các tuyến đường cao tốc chính và tốc độ thấp hơn cho các làn đường hẹp.

4. Thiết lập chướng ngại vật hình chữ nhật: Bạn có thể xác định các chướng ngại vật hình chữ nhật trên bản đồ cần được tính đến khi xây dựng đường dẫn tối ưu. Điều này hữu ích khi có các chướng ngại vật đã biết như tòa nhà hoặc hồ (sự xấp xỉ của chúng).

5. Giới hạn bán kính tìm kiếm cho đường xá: Bạn có thể giới hạn bán kính tìm kiếm cho đường xá để giảm thời gian tìm kiếm và chỉ tập trung vào một khu vực cụ thể.

6. Kiểm soát hiệu suất và độ chính xác: Chúng tôi cung cấp khả năng kiểm soát hiệu suất và độ chính xác của thuật toán. Bạn có thể điều chỉnh nó để đạt được sự cân bằng mong muốn giữa tốc độ tìm kiếm và độ chính xác xây dựng tuyến đường.

Tiếp theo, chúng ta sẽ cung cấp mô tả chi tiết hơn về từng tính năng này và xem xét các ví dụ về ứng dụng của chúng.

## Approach to Solution

Mặc dù việc tìm đường là một nhiệm vụ không tầm thường, nhưng có một số thuật toán tốt và đáng tin cậy được công nhận trong cộng đồng phát triển.

Trong quá trình thực hiện của chúng tôi, chúng tôi đã sử dụng thuật toán Lee sửa đổi. Chúng ta có một lưới các ô trên mặt phẳng. Từ điểm bắt đầu, một sóng lan truyền theo 8 hướng (bao gồm cả đường chéo) đến các ô lân cận, tính toán thời gian cần thiết để đến mỗi ô đó. Một ô lân cận có thể chứa chướng ngại vật hoặc đường xá. Đường xá có thể có hệ số vận tốc khác nhau. Do đó, chúng ta "đánh dấu" lưới của mình bằng thời gian cần thiết để đến mỗi ô từ ô bắt đầu trong một bán kính nhất định hoặc cho đến khi đến điểm đích. Nếu chúng ta đến điểm đích, chúng ta xây dựng đường đi ngược lại bằng cách sử dụng lưới của mình.

Để xác định tuyến đường tối ưu trên mạng lưới đường bộ, cần thực hiện nhiều bước. Đầu tiên, bạn cần xác định các con đường và chỉ định tốc độ di chuyển trên mỗi con đường. Bạn cũng nên xem xét sự hiện diện của chướng ngại vật nhân tạo và tự nhiên có thể ảnh hưởng đến đường đi. Sau đó, bạn cần chỉ định điểm bắt đầu và đích của việc tìm kiếm. Khi các bước chuẩn bị này hoàn tất, bạn có thể tiến hành tìm đường thực tế. Kết quả sẽ là một đường dẫn được biểu diễn, ví dụ như một danh sách các tọa độ điểm.

Điều quan trọng cần lưu ý là đường đi tối ưu có thể phụ thuộc vào phương thức vận chuyển đã chọn, vì tốc độ di chuyển và tập hợp chướng ngại vật có thể khác nhau. Do đó, các bộ đường xá và chướng ngại vật khác nhau nên được sử dụng cho mỗi loại hình vận chuyển khi tìm kiếm đường dẫn tối ưu.

## Demo Project on GitHub

Để hiểu rõ hơn về chức năng của thư viện của chúng tôi, hãy xem xét [một ví dụ về cách sử dụng nó](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths). Mã này minh họa cách thiết lập đường xá và chướng ngại vật trong thuật toán tìm đường và tìm tuyến đường tối ưu.

Ví dụ bao gồm các bước sau:

1. Tạo một danh sách thông tin đường (RoadInfo), bao gồm thông tin về đoạn đường (Segment) và tốc độ di chuyển (Velocity).
2. Thêm các con đường nhanh vào danh sách.
3. Thêm các vòng xoay chậm vào danh sách.
4. Tạo trình tạo lớp đường (WayLayerGenerator) và thêm đường xá vào trình tạo.
5. Tìm kiếm nhiều đường dẫn từ điểm bắt đầu (startPoint) đến các điểm đích (goalPoint01, goalPoint02, goalPoint03) bằng cách sử dụng bán kính được chỉ định (radius).
6. Chuẩn bị một lớp đường xá (roadsLayer) để hiển thị trên bản đồ và thêm các đối tượng đường xá.
7. Chuẩn bị một lớp đường (wayLayer) để hiển thị trên bản đồ và tạo các đối tượng hình học cho mỗi đường dẫn được tìm thấy.
8. [Hiển thị bản đồ](https://docs.aspose.com/gis/net/how-to-draw-geometry/) bằng cách sử dụng hàm ShowMap, lưu bản đồ tại đường dẫn được chỉ định.

Mã này xây dựng và hiển thị các đường dẫn trên bản đồ cho các điểm đã chỉ định bằng thông tin đường xá và trình tạo lớp đường.

## Search Options

Việc tìm đường được thực hiện bằng lớp **WayLayerGenerator** nằm trong không gian tên Aspose.Gis.GeoTools.WayAnalyzer.

Lớp WayLayerGenerator có phương thức **FindTheWay** để tìm đường đi từ điểm bắt đầu đến mục tiêu. Để tạo một phiên bản của lớp WayLayerGenerator, chúng ta truyền WayOptions làm tham số (tất cả các tham số đều là tùy chọn):

- StartPoint: Điểm bắt đầu

- GoalPoint: Điểm đích

- Radius: Bán kính tìm kiếm

- Scale: Tỷ lệ của lưới

- IsMoveOnlyRoad: Cho biết có nên chỉ tìm đường trên đường xá hay không

Tính năng đáng chú ý ở đây là tham số Scale. Nếu nó được chỉ định trong bộ tạo, chúng ta cố định một tỷ lệ liên tục cho các lần tìm kiếm tiếp theo. Nếu tham số Scale không được đặt nhưng StartPoint và GoalPoint được đặt, chúng ta tính toán tỷ lệ như khoảng cách giữa điểm bắt đầu và đích chia cho 100. Trong tất cả các trường hợp khác, giá trị mặc định của Scale là 1. Đối với người dùng có kinh nghiệm, tốt hơn nên đặt Scale hoặc đặt trực tiếp StartPoint và GoalPoint để biểu diễn đường xá và chướng ngại vật trên lưới một cách hiệu quả nhất (đặc biệt nếu có nhiều).

Để sử dụng phương thức FindTheWay, chúng ta cần chỉ định điểm bắt đầu và đích. Chúng ta cũng có thể đặt bán kính tìm kiếm (khoảng cách mà sóng lan truyền đến đó). Mặc định, bán kính được tính như khoảng cách giữa điểm bắt đầu và đích nhân với 3. Điểm bắt đầu và đích có thể gần hoặc rất xa nhau, vì vậy dựa trên khoảng cách giữa chúng, chúng ta tính toán tỷ lệ của lưới của mình. Nếu tỷ lệ hiện tại không khớp với tỷ lệ trước đó, chúng ta sẽ tính toán lại lưới. Tỷ lệ có thể được cố định bằng tham số Scale. Trong trường hợp này, nó không được tính toán và lưới không được tính toán lại.

Trước khi bắt đầu tìm kiếm, chúng ta cần xác định bản đồ đường xá và chướng ngại vật bằng cách sử dụng các phương thức AddRoad và AddBlock tương ứng của lớp WayLayerGenerator.

Đối với phương thức **AddRoad**, chúng ta cần chỉ định:

- startPoint: Điểm bắt đầu của con đường

- endPoint: Điểm kết thúc của con đường

- velocity: Tốc độ di chuyển trên con đường

Đối với phương thức **AddBlock**, chúng ta cần chỉ định:

- x: Tọa độ x của góc trên bên trái của khối

- y: Tọa độ y của góc trên bên trái của khối

- sizeX: Kích thước theo trục x

- sizeY: Kích thước theo trục y

Các phương thức này cho phép chúng ta xác định bản đồ đường xá và chướng ngại vật trước khi bắt đầu quá trình tìm đường.

## Code examples

Dưới đây là một số ví dụ về mã minh họa cách thiết lập đường xá và chướng ngại vật trong thuật toán tìm đường và tìm tuyến đường tối ưu.

Ví dụ 1: Tìm đường đi giữa điểm bắt đầu và đích.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Ví dụ 2**: Đặt tham số tỷ lệ và có tọa độ âm cho điểm.

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Ví dụ 3**: Đặt tham số IsMoveOnlyRoad và bán kính tìm kiếm.

```
WayOptions mapGeneratorOptions = new WayOptions();
mapGeneratorOptions.IsMoveOnlyRoad = true;
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddRoad(new Point(100, 100), new Point(140, 150), 10);
generator.AddRoad(new Point(140, 150), new Point(190, 100), 10);
Point startPoint = new Point(100, 100);
Point goalPoint = new Point(190, 100);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 100);
```

**Ví dụ 4**: Đặt tham số tỷ lệ để tìm kiếm nhanh hơn.

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**Ví dụ 5**: Ví dụ tìm kiếm nhiều lần.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddBlock(200, 1700, 1500, 100, 0);
generator.AddBlock(1700, 200, 100, 1600, 0);
generator.AddBlock(200, 200, 1500, 100, 0);
generator.AddRoad(new Point(1000, 1150), new Point(200, 600), 10);
generator.AddRoad(new Point(50, 450), new Point(150, 1850), 10);

Point startPoint = new Point(1000, 1000);
Point goalPoint = new Point(1900, 1000);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 3500);

Point startPoint = new Point(50, 50);
Point goalPoint = new Point(70, 70);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

Các ví dụ về mã này xây dựng và hiển thị các đường dẫn trên bản đồ cho các điểm đã chỉ định, sử dụng thông tin đường xá và trình tạo lớp đường.

**Tóm lại**, công cụ tìm đường tối ưu là một công cụ mạnh mẽ để phân tích mạng lưới đường bộ và xác định các tuyến đường hiệu quả nhất giữa các điểm trên bản đồ. Nó tính đến nhiều yếu tố như loại đường, chướng ngại vật và tốc độ khác nhau để tính toán đường đi tối ưu. Với khả năng tìm kiếm đường dẫn trên cả đường xá và địa hình gồ ghề, cũng như kiểm soát bán kính tìm kiếm và điều chỉnh hiệu suất và độ chính xác, thuật toán này cung cấp một giải pháp linh hoạt cho việc tối ưu hóa tuyến đường. Bằng cách xem xét các phương thức vận chuyển khác nhau và điều chỉnh bộ đường xá và chướng ngại vật tương ứng, nó có thể được sử dụng trong nhiều tình huống như lập kế hoạch giao hàng hoặc tối ưu hóa đi làm. Các ví dụ về mã và giải thích được cung cấp minh họa khả năng của thuật toán và các bước liên quan đến việc sử dụng nó.