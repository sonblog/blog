---
author: client
comments: false
date: 2016-12-12 03:31:42+00:00
template: "post"
link: https://quachson.com/nhung-han-che-cua-classification/
slug: nhung-han-che-cua-classification
title: Những hạn chế của Classification
wordpress_id: 1321
categories:
- Machine Learning
---

Classification là toán xác xuất nên để kỳ vọng tính chính xác 100% là rất khó vì nó phụ thuộc vào tập dataset. Classification chỉ có 2 giá trị: [0,1], [đúng, sai], về email thì [spam, not spam], [khẳng định, phủ định], thông thường thì có ngưỡng giữa tùy vào ta chọn như [0,1] ta chọn 0.5 cho đơn giản làm ví dụ, nếu < 0.5 ==> 0,  > 0.5 là 1. Kết quả trả về rơi nhiều vào giữa ngưỡng [0.4, 0.5, 0.6] có thể dẫn đến kết quả sai. Gọi là na ná giống nhau, nhưng về bản chất nhiều khi khác nhau xa lắm. Cho nên khi có kết quả gần đúng người ta sẽ dùng thuật toán khác filter thêm lần nữa để cho ra kết quả tốt hơn. Ta làm thử 1 ví dụ để xem tính chính xác của Classification như thế nào nhé.

Example: ta dùng tập [0,1] và chọn ngưỡng giữa là 0.5 và có tập kết quả là {1, 0, 0.6, 0.4, 1, 0}

- TP: đúng tuyệt đối, có giá trị là 1.

- FN: Sai tuyệt đối, có giá trị là 0.

- FP: Đúng ở ngưỡng giữa, 0.5, 0.6, 0.7... < 1

- TN: Sai ở ngưỡng giữa: 0.4, 0.3,0.2... > 0

Trong trường hợp này ta có.

TP = 2 (có 2 giá trị 1), đúng 100%

FN = 2 (có 2 giá trị 0), sai 100%

FP = 1 (0.6)

TN = 1 (0.4)

Ta có thể định nghĩa tính chính xác như sau:

Tính chính xác = `(TP + TN)/(TP + TN + FP + FN) = (2 + 2)/(2 + 2 + 1 + 1) = 2⁄3`

Ta có 4 mẫu đúng trên 6 mẫu. Bây giờ ta xem thêm ví dụ khác về lọc email spam.
<table >

<tr >

Classified positive
Classified negative
</tr>

<tbody >
<tr >

<td >Positive class
</td>

<td >10
</td>

<td >15
</td>
</tr>
<tr >

<td >Negative class
</td>

<td >5
</td>

<td >100
</td>
</tr>
</tbody>
</table>
Trong trường hợp này, tính chính xác = (10 + 100)/(10 + 5 + 15 + 100) = **84.6%. **Ta tạm thời cho rằng thuật toán phân loại làm việc rất hiệu quả, dò tìm dc gần 85% những email spam. Tuy nhiên điều gì sẽ xảy ra khi ta chuyển đổi thuật toán của Classficication rằng không có email spam nào cả.


<table >

<tr >

Classified positive
Classified negative
</tr>

<tbody >
<tr >

<td >Positive class
</td>

<td >0
</td>

<td >0
</td>
</tr>
<tr >

<td >Negative class
</td>

<td >15
</td>

<td >115
</td>
</tr>
</tbody>
</table>
Tính chính xác = (0 + 115)/(0 + 15 + 0 + 115) = **88.5%**. Thật không thể tin nổi. Ta thay đổi thuật toán để cho ra kết quả hoàn toàn vô nghĩa, với số 0 ta đã làm tăng tính chính xác.

Cái này dc gọi là nghịch lý chính xác (**the accuracy paradox**). Khi TP < FP, tính chính xác sẽ luôn tăng khi ta thay đổi thuật toán phân loại để luôn luôn ra kết quả sai. Ngược lại khi TN < FN tương tự như vậy khi ta thay đổi luật để luôn cho ra kết quả đúng.

Vậy thì ta có thể làm dc gì, Ta nên biết rằng không có thuật toán phân loại nào là tốt nhất, chính xác nhất cả, ta phải biết kết hợp nhiều thuật toán phân loại với nhau để cho ra kết quả chính xác nhất có thể.

Kết luận là lại chọn ngưỡng giữa cho Classification là rất quan trọng. Trong y học những triệu chứng bệnh na ná giống nhau là rất nhiều, khi phân loại dc bệnh rồi còn phải yêu cầu đi làm xét nghiệm nữa, nghĩa là phân loại thêm lần nữa để chính xác hơn.


