---
author: client
comments: false
date: 2016-12-12 07:37:32+00:00
template: "post"
link: https://quachson.com/machine-learning-la-gi/
slug: machine-learning-la-gi
title: Machine Learning là gì ?
wordpress_id: 1339
categories:
- Machine Learning
---

**I. 3 dạng Machine Learning chính**
**1/ Supervised Learning (học tập có giám sát)**: Nôm na nghĩa là máy sẽ đưa ra suy đoán cho ra kết quả dựa trên những thuật toán và một tập dữ liệu cho trước mà không cần phải viết bất kỳ dòng code nào cho từng vấn đề cụ thể

Những vấn đề của supervised learning được chia làm 2 loại: hồi quy (**regression**) và phân loại (**classification**)
**Ví dụ 1**: Chúng ta có sẵn 1000 status facebook (gọi là dataset A) được phân loại theo các trạng thái như vui, buồn, giận dữ v.v.. (ứng với mỗi trạng thái là một tập hợp các đặc tính có liên quan, ví dụ các trạng thái status vui thì thường xuất hiện các cụm từ như “đáng yêu quá", “thích quá", “hay quá"...), supervised learning là phương pháp sử dụng dataset A này để xác định 100 status facebook khác chưa được gắn trạng thái.

**Ví dụ 2:**
**(a) Hồi quy** - Đưa ra tấm hình của 1 người, chúng ta dự đoán tuổi của người đó dựa trên tấm hình

**(b) Phân loại** - Với một bệnh nhân có khối u, chúng tôi-có để dự đoán xem khối u ác tính hoặc lành tính.

**2/ Unsupervised Learning**: Nôm na nghĩa là tay không bắt giặc :D máy sẽ tự tìm ra các mối quan hệ hoặc các pattern từ một dataset.
**Ví dụ 1**: Chúng ta có thể sử dụng phương pháp unsupervised learning để tìm ra các chủ đề được đề cập tới từ 1000 status facebook, ví dụ các status có chủ đề về bóng đá (vì trong những status này xuất hiện nhiều từ, cụm từ, hashtag có liên quan đến bóng đá chẳng hạn).

**Ví dụ 2:**
**Clustering**: Lấy một bộ sưu tập của một triệu gen khác nhau, và tìm cách tự động nhóm những gen có liên quan hoặc tương tự vào 1 nhóm lớn bởi những giá trị khác nhau như là tuổi thọ, vị trí, vai trò, ...

**Non-clustering**: Các "Thuật toán tiệc Cocktail", cho phép bạn tìm thấy một cấu trúc trong môi trường hỗn loạn. (Nghĩa là: Xác định tiếng nói riêng và âm nhạc từ một mạng lưới các âm thanh tại một bữa tiệc cocktail).

**3/ Reinforcement Learning**: Nôm na nghĩa là máy có thể tự cập nhật cách giải quyết vấn đề theo kiểu thử và sửa liên tục.
**Ví dụ:** DeepMind AlphaGo với việc chiến thắng Lee Sedol trong bộ môn cờ vây là ví dụ nổi tiếng nhất về RL (thực tế DeepMind gọi là Deep Reinforcement Learning).

**II. 10 thuật toán Machine Learning quan trọng nhất**
Để kết luận 10 thuật toán ML nào quan trọng nhất thực sự là việc rất phức tạp vì chúng ta không biết xếp theo tiêu chí nào? Ví dụ độ phổ biến, tính hữu dụng, tính đơn giản, tính chính xác v.v.. Vì thế mình chỉ giả định nếu mình phỏng vấn một người cho vị trí Data Scientist / Data Engineer thì mình cần họ phải nắm được 10 thuật toán sau (theo thứ tự ưu tiên):



 	
  * **Linear Regression (hồi quy tuyến tính)**

 	
  * **Logistic Regression **

 	
  * **Decision Trees (cây quyết định)**

 	
  * **Naïve Bayes Classification**

 	
  * **Ordinary Least Squares Regression**

 	
  * **Support Vector Machines**

 	
  * **Ensemble Methods**

 	
  * **Clustering Algorithms**

 	
  * **Principal Component Analysis**

 	
  * **Singular Value Decomposition**

 	
  * **Independent Component Analysis**


**1/ Linear Regression và Logistic Regression (Hồi quy tuyến tính và Hồi quy Logistic)**:

Machine learning: luôn là dự đoán. Giả sử dự đoán giá nhà 2 phòng ngủ ở California vào tháng 12, 2018 dựa vào tập dữ liệu (training set) của năm 2017.
<table style="width: 362px; height: 31px;" >
<tbody >
<tr >

<td style="width: 160.703125px;" >Tháng Năm
</td>

<td style="width: 186.296875px;" >Giá
</td>
</tr>
<tr >

<td style="width: 160.703125px;" >1-2018
</td>

<td style="width: 186.296875px;" >$525.000
</td>
</tr>
<tr >

<td style="width: 160.703125px;" >12-2017
</td>

<td style="width: 186.296875px;" >$524.000
</td>
</tr>
<tr >

<td style="width: 160.703125px;" >11-2017
</td>

<td style="width: 186.296875px;" >$520.000
</td>
</tr>
<tr >

<td style="width: 160.703125px;" >10-2017
</td>

<td style="width: 186.296875px;" >$516.000
</td>
</tr>
<tr >

<td style="width: 160.703125px;" >09-2017
</td>

<td style="width: 186.296875px;" >$513.000
</td>
</tr>
<tr >

<td style="width: 160.703125px;" >08-2017
</td>

<td style="width: 186.296875px;" >$509.000
</td>
</tr>
<tr >

<td style="width: 160.703125px;" >....
</td>

<td style="width: 186.296875px;" >.......
</td>
</tr>
<tr >

<td style="width: 160.703125px;" >01-2017
</td>

<td style="width: 186.296875px;" >$487.000
</td>
</tr>
</tbody>
</table>
Ta thấy tập dataset này, giá luôn tăng theo tuyết tính x=4.1% (giả sử), thì tháng 2,3,4-2018 giá sẽ luôn tăng.
<table style="width: 356px;" >
<tbody >
<tr >

<td style="width: 171.96875px;" >02-2018
</td>

<td style="width: 193.03125px;" >$527.000
</td>
</tr>
<tr >

<td style="width: 171.96875px;" >03-2018
</td>

<td style="width: 193.03125px;" >$528.000
</td>
</tr>
<tr >

<td style="width: 171.96875px;" >04-2018
</td>

<td style="width: 193.03125px;" >$530.000
</td>
</tr>
<tr >

<td style="width: 171.96875px;" >...
</td>

<td style="width: 193.03125px;" >...
</td>
</tr>
<tr >

<td style="width: 171.96875px;" >12-2018
</td>

<td style="width: 193.03125px;" >$545.000
</td>
</tr>
</tbody>
</table>
![](https://quachson.com/wp-content/uploads/Screen-Shot-2018-01-28-at-9.10.35-PM-300x246.png)

Dùng làm gì nhỉ? Thuật toán Linear Regression mô tả dữ liệu và thể hiện mối quan hệ giữa một biến phụ thuộc (x) với **một (y)** hoặc **nhiều (yi)** biến độc lập (**dependent variable - DV**) . Tức là nếu biến độc lập thay đổi thì ảnh hưởng đến biến phụ thuộc như thế nào. Nếu 1 biến độc lập gọi là Hồi quy tuyến tính đơn (**Simple** **Linear Regression**), nếu nhiều biến độc lập gọi là Hồi quy tuyến tính đa biến (**Multiple** **Linear Regression**).

Đơn: ![y = \beta 1 + \beta 2 x + \alpha](http://chart.apis.google.com/chart?cht=tx&chl=y%20%3D%20%5Cbeta%201%20%2B%20%5Cbeta%202%20x%20%2B%20%5Calpha)

Đa: ![y = \beta 0 + \beta 1 x1 + \beta 2 x2 + ... + \beta n xn + \alpha](http://chart.apis.google.com/chart?cht=tx&chl=y%20%3D%20%5Cbeta%200%20%2B%20%5Cbeta%201%20x1%20%2B%20%5Cbeta%202%20x2%20%2B%20...%20%2B%20%5Cbeta%20n%20xn%20%2B%20%5Calpha)

Nhìn vào phương trình ta thấy gì, y thay đổi khi x thay đổi.
Ok, tạm hiểu, thế sao người ta lại dùng Linear Regression mà không dùng thuật toán khác? Một số ưu điểm của Linear Regression là tính dễ hiểu của thuật toán (ví dụ trên chẳng hạn, những thuật toán sau ví dụ không dễ hiểu như vậy đâu :)); dễ chỉnh sửa (tuning); độ phổ biến cao và tốc độ giải thuật nhanh. Nghe có vẻ dễ đúng không? Cái khó nhất của các Generalized Linear Model (GLM - Mô hình tuyến tính tổng quát) là việc chọn independent variables chứ không phải là thuật toán.
Thế Linear Regression và Logistic Regression thì khác nhau cái gì? Cái khác nhau nhất chính là ở **dependent variable (DV)**, đối với Linear Regression thì DV có dạng liên tục (continuous) còn đối với Logistic Regression thì DV có thể chỉ là Có/Không, Sống/Chết, 0/1 (mô hình nhị phân) hoặc DV có thể ở dạng rời rạc (discrete). Continuos và discrete là hai khái niệm rất lớn trong toán học, các bạn có thể tìm hiểu thêm ở trên mạng, trong khuôn khổ bài này thì hơi khó để giải thích ngắn gọn được.
Ứng dụng trong đời thường như thế nào? Một trong những ứng dụng lớn nhất của GLM model (Mô hình tuyến tính tổng quát) là hệ thống quản lý rủi ro hoặc chấm điểm tín dụng của các ngân hàng. Chẳng hạn như để quyết định hạn mức thẻ Credit card của bạn, hệ thống sẽ sử dụng GLM để tính toán dựa trên các thông tin bạn cung cấp như mức lương hiện tại, độ tuổi, giới tính, công việc đang làm v.v..

**2/ Decision Trees (Cây quyết định)**
Dùng làm gì nhỉ?Cây quyết định là một công cụ dùng để hỗ trợ trong việc ra quyết định dựa trên một hoặc nhiều biểu đồ dạng cây. Biểu đồ này thể hiện số lượng câu hỏi yes/no tối thiểu mà một người cần hỏi, để đánh giá về khả năng ra được một quyết định đúng.
Ví dụ nhé,chúng ta có một dataset về dữ liệu về các cầu thủ trẻ trong khoảnng 10-16 tuổi. Chúng ta có thể collect được những dữ liệu như vị trí thi đấu, chiều cao, cân nặng, tỷ lệ sút bóng thành công, tỷ lệ xoạc bóng thành công, tỷ lệ chuyền bóng thành công, tốc độ, tỷ lệ đánh đầu thành công v.v...
Giả sử bạn là một HLV và đang có một lứa cầu thủ trẻ mới vào. Làm thế nào để quyết định được một cầu thủ trẻ nên chơi ở vị trí thi đấu nào là phù hợp nhất?
Sử dụng Cây quyết định sẽ giúp bạn làm được điều này, bằng cách thu thập những dữ liệu của lứa cầu thủ trẻ mới vào và so sánh dữ liệu mới này với dữ liệu có sẵn trong dataset, Cây quyết định sẽ giúp bạn xác định được vị trí thi đấu nào thích hợp nhất với một cầu thủ trẻ mới tuyển.
Nghe cool vãi, nhưng theo tôi biết thì đếch có thuật toán nào gọi là Cây quyết định cả :)) Oh đúng, xin lỗi :)) Cây quyết định thực ra là một họ tập hợp các thuật toán mà outcome của nó có thể biểu diễn dưới dạng cây. Một số thuật toán họ này rất phổ biến như C4.5 hoặc Random Forest v.v... Trong khuôn khổ bài mở đầu này, mình chỉ có thể giới thiệu khái quát như vậy, sẽ có những bài khác đi sâu hơn vào từng thuật toán trên.



![decision-tree](https://quachson.com/wp-content/uploads/decision-tree.jpg)


Oh thế Cây quyết định thì có gì hay? Cái hay nhất của Cây quyết định là tính đơn giản và dễ interpret của kết quả. Hầu như bất kỳ ai nhìn vào một decision tree cũng có thể hiểu được mà không cần có kiến thức gì về Machine Learning cả.
Ứng dụng lớn nhất của Decision Trees là gì? Ứng dụng của Decision Trees cực nhiều, cực phổ biến, vì tính thực tiễn của nó trong việc hỗ trợ ra quyết định (mà trong thực tế thì công việc gì cũng cần quyết định). Ví dụ: quyết định cho vay, quyết định về chiến lược giá bán v.v..

Mình muốn kết thúc phần này bằng một câu nói của Andrew Ng - Chief Scientist của Baidu và Founder của Coursera: “Nếu bạn thành thạo thuật toán hồi quy tuyến tính, hồi quy logistic và nguyên tắc kiểm soát (regularization) thì bạn đã biết nhiều về Machine Learning hơn phần lớn các kỹ sư Machine Learning ở Silicon Valley rồi". Để biết về các thuật toán này thì không khó nhưng để master nó thì không hề dễ chút nào (nhất là về regularization). Điều mà mình muốn nói ở đây chính là Machine Learning không hề khó, không phải là một black-box, ai cũng có thể học và master được nếu họ thực sự yêu thích và muốn nắm được một trong những vũ khí mạnh nhất của nhân loại hiện nay.

**3/ Naïve Bayes Classification: bằng chứng và sự thay đổi mức độ tin tưởng.**

Suy luận Bayes sử dụng các khía cạnh của phương pháp khoa học, trong đó có việc thu thập các bằng chứng nhất quán hoặc không nhất quán với một giả thuyết nào đó. Khi các bằng chứng tích lũy, mức độ tin tưởng vào một giả thuyết thay đổi. Khi có đủ bằng chứng, mức độ tin tưởng này thường trở nên rất cao hoặc rất thấp. Do đó, theo lý thuyết, đây có thể được coi là một cơ sở lôgic thích hợp cho việc phân biệt các giả thuyết mâu thuẫn nhau - các giả thuyết với mức độ tin tưởng cao được chấp nhận là đúng; các giả thuyết với độ tin tưởng rất thấp nên bị coi là sai và loại bỏ. Trong thực tiễn, tuy khung toán học tổng quát của suy luận Bayes là đúng đắn, nó đòi hòi việc gán các xác suất tiền nghiệm cho các giả thuyết, trong khi các xác suất này có thể là đối tượng của sự sai lệch chủ quan



 	    Một ví dụ về suy luận Bayes:



 	    _Hàng tỉ năm nay, Mặt Trời đã mọc sau khi nó lặn. Tối nay Mặt Trời đã lặn. Ngày mai Mặt Trời sẽ mọc với xác suất rất cao (hoặc tôi rất tin tưởng vào điều đó hoặc điều đó là đúng). Với xác suất rất thấp (hoặc tôi không hề tin hoặc điều sau không đúng), ngày mai Mặt Trời sẽ không mọc._





Ưu điểm:



 	
  * Thuật toán đơn giản nên dễ dàng cài đặt

 	
  * Thời gian thực thi tương tự như cây quyết định

 	
  * Đạt kết quả tốt trong phần lớn cái trường hợp


Khuyết điểm

 	
  * Giả thiết về tính độc lập điều kiện của các thuộc tính làm giảm độ chính xác.




Tham khảo: [Nguyễn Đức Anh](https://www.facebook.com/notes/nguy%E1%BB%85n-%C4%91%E1%BB%A9c-anh/machine-learning-cho-n%C3%B4ng-d%C3%A2n-p-1-d/10154954912798072)
