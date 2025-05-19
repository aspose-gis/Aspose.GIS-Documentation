---
title: "Gán Nhãn Đơn Giản"
type: docs
url: /vi/net/simple-labeling/
weight: 10
---

## **Gán Nhãn Đơn Giản**
Gán nhãn đơn giản xác định cách các thuộc tính phải được gán nhãn.

Các tùy chọn được hỗ trợ là:

|**Thuộc tính**|**Mô tả**|
| :- | :- |
|[LabelAttribute](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelattribute)|Chỉ định tên thuộc tính được sử dụng làm nguồn của nhãn.|
|[LabelExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/labelexpression)|Cung cấp một cách để tùy chỉnh và định dạng văn bản nhãn. Ghi đè LabelAttribute|
|[FontFamily](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontfamily)|Chỉ định phông chữ được sử dụng để hiển thị văn bản. Giá trị mặc định phụ thuộc vào hệ thống.|
|[FontStyle](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontstyle)|<p>Kiểu áp dụng cho văn bản.</p><p>- FontStyle.Regular - văn bản thông thường.</p><p>- FontStyle.Bold - văn bản đậm.</p><p>- FontStyle.Italic - văn bản nghiêng.</p><p>- FontStyle.Underine - văn bản có gạch chân.</p><p>- FontStyle.StrikeOut - văn bản có một đường kẻ ngang qua giữa.</p>|
|[FontSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontsize)|Chỉ định kích thước của văn bản.|
|[FontColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/fontcolor)|Xác định màu sắc của văn bản.|
|[HaloSize](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halosize)|Xác định kích thước của hào quang (hoặc đường viền) xung quanh văn bản.|
|[HaloColor](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/halocolor)|Xác định màu sắc của hào quang xung quanh văn bản.|
|[GeometryExpression](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/geometryexpression)|Biểu thức hình học được sử dụng để biến đổi hình học trước khi chuyển nó cho công cụ gán nhãn.|
|[MultipartMode](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/multipartmode)|<p>Chỉ định hành vi hiển thị cho các hình học nhiều phần.</p><p>- MultipartMode.All - đặt nhãn gần mỗi phần của hình học.</p><p>- MultipartMode.Any - đặt một nhãn gần bất kỳ phần nào của hình học.</p><p>- MultipartMode.Largest - đặt nhãn gần phần lớn nhất của hình học.</p>|
|[Placement](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/placement)|<p>Chỉ định cách các nhãn được đặt tương đối so với hình học.</p><p>- PointLabelPlacement - đặt nhãn gần trung tâm của hình học.</p><p>- LineLabelPlacement - đặt nhãn dọc theo hình học hoặc chu vi của nó.</p>|
|[Priority](https://reference.aspose.com/gis/net/aspose.gis.rendering.labelings/simplelabeling/properties/priority)|Chỉ định độ ưu tiên của nhãn trong trường hợp nó chồng lên các nhãn khác.<br>Nhãn có độ ưu tiên thấp hơn không được hiển thị. Mặc định là 1000.|

## **Ví dụ**
### **Ví dụ Gán Nhãn Điểm**
Theo mặc định, SimpleLabeling vẽ văn bản trên các điểm:

|![todo:image_alt_text](simple-labeling_1.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabeling.cs" >}}|
| :- | :- |

-----
Đây là cách tạo kiểu phông chữ:

|![todo:image_alt_text](simple-labeling_2.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingStyled.cs" >}}|
| :- | :- |

-----
Để kiểm soát vị trí văn bản tương đối so với các đặc trưng điểm, thuộc tính placement phải được đặt:

|![todo:image_alt_text](simple-labeling_3.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-PointsLabelingPlaced.cs" >}}|
| :- | :- |

-----
Để có các kịch bản nâng cao hơn, bạn có thể muốn chọn các nhãn khác nhau cho các đặc trưng. Đây là cách thực hiện:

|![todo:image_alt_text](simple-labeling_4.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-RuleBasedLabeling.cs" >}}|
| :- | :- |

-----
### **Ví dụ Gán Nhãn Đường**
Theo mặc định, SimpleLabeling vẽ nhãn gần trung tâm của đường:

|![todo:image_alt_text](simple-labeling_5.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabeling.cs" >}}|
| :- | :- |

-----
Để xoay nhãn sao cho chúng song song với các đường, LineLabelPlacement với LineLabelAlignment.Parallel có thể được sử dụng:

|![todo:image_alt_text](simple-labeling_6.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingParallel.cs" >}}|
| :- | :- |

-----
Nếu bạn muốn văn bản tuân theo đường chính xác, LineLabelPlacement với LineLabelAlignment.Curved có thể được sử dụng:

|![todo:image_alt_text](simple-labeling_7.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurved.cs" >}}|
| :- | :- |

-----
Nếu bạn không muốn văn bản chồng lên đường, hãy sử dụng LineLabelPlacement.Offset:

|![todo:image_alt_text](simple-labeling_8.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingCurvedWithOffset.cs" >}}|
| :- | :- |

-----
Để có các kịch bản nâng cao hơn, bạn có thể muốn điều chỉnh kiểu nhãn động dựa trên giá trị thuộc tính của đặc trưng. Đây là cách thực hiện:

|![todo:image_alt_text](simple-labeling_9.png)|{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Rendering-LabelMap-LinesLabelingFeatureBased.cs" >}}|
| :- | :- |
