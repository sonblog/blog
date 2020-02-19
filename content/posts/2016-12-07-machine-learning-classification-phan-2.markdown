---
author: quachson
comments: false
date: 2016-12-07 11:55:05+00:00
template: "post"
link: https://quachson.com/machine-learning-classification-phan-2/
slug: machine-learning-classification-phan-2
title: Machine Learning – Classification – phần 2
wordpress_id: 1294
category: "ML"
description: "Trở lại câu chuyện về hoa diên vĩ (Iris flower): Chúng ta có một danh sách các bông hoa diên vĩ được mô tả bằng độ dài và độ dày của đài hoa và cánh hoa (attributes). Chúng ta cũng đã biết chủng loại của tất cả các bông hoa trừ một cái duy nhất (chúng ta sẽ gọi nó là “bông diên vĩ bí ẩn”) và mục tiêu cuối cùng là tìm ra chủng loại của bông diên vĩ bí ẩn này. Với bài toán này, chúng ta giả sử rằng những thuộc tính trên là đặc trưng của chủng loại."

---

Trong bài viết trước ([link](https://quachson.com/machine-learning-classification-phan-1)), chúng ta đã cùng tìm hiểu về **Classification**. Chúng ta cũng đã đưa ra vài ví dụ về ứng dụng của nó và cũng đã làm quen với **the Iris dataset**. Nếu có thời gian, bạn nên đọc bài viết đó để có thể hiểu cặn kẽ những nội dung trong bài viết này.

Trở lại câu chuyện về hoa diên vĩ (Iris flower): Chúng ta có một danh sách các bông hoa diên vĩ được mô tả bằng độ dài và độ dày của đài hoa và cánh hoa (**attributes**). Chúng ta cũng đã biết chủng loại của tất cả các bông hoa trừ một cái duy nhất (chúng ta sẽ gọi nó là _"bông diên vĩ bí ẩn"_) và mục tiêu cuối cùng là tìm ra chủng loại của bông diên vĩ bí ẩn này. Với bài toán này, chúng ta giả sử rằng những thuộc tính trên là đặc trưng của chủng loại.


# Giải pháp 1:Quan sát tương đồng (_The same observation solution_)


Giải pháp đầu tiên mà ta thường nghĩ đến trong trường hợp này là tìm kiếm một bông diên vĩ khác với độ dài và độ dày của đài hoa và cánh hoa giống với bông diên vĩ bí ẩn. Nếu có, nhiều khả năng chủng loại của bông hoa này cũng tương đồng với bông hoa bí ẩn. Không may mắn thay, rất hiếm khi chúng ta tìm được hai bông diên vĩ với những thông số giống hệt nhau. Trên thực tế, tìm kiếm một quan sát với các thuộc tính giống hệt hiếm khi là một giải pháp tốt, sẽ luôn có những sự khác biệt dù là rất nhỏ.


# Giải pháp 2:Hàng xóm gần nhất (_The 1-nearest neighbors solution_)


Thay vì tìm kiếm một bông diên vĩ với các giá trị thuộc tính tương đồng, chúng ta sẽ tìm kiếm những bông hoa _gần giống_ với bông hoa bí ẩn. Nếu hai bông diên vĩ có kích thước rất gần giống nhau, chúng trông sẽ rất giống nhau và vì vậy, có thể chúng thuộc cùng một chủng loại.

Tuy nhiên, cách này sẽ không hiệu quả nếu như có một vài bông diên vĩ thuộc các chủng loại khác nhau nhưng đều có giá trị thuộc tính gần giống với bông diên vĩ bí ẩn. Vì vậy, chúng ta chỉ tìm ra bông diên vĩ _giống nhất_ với bông diên vĩ bí ẩn. Điều đó có nghĩa là chúng ta phải định nghĩa chính xác thế nào là hai bông diên vĩ _giống nhau_. Chúng ta cũng phải định nghĩa thế nào là một bông diên vĩ giống bông diên vĩ này _hơn_ so với một bông khác.

Giải pháp được sử dụng bởi các nhà nghiên cứu là định nghĩa _khoảng cách_ giữa hai bông diên vĩ. Khoảng cách giữa hai bông diên vĩ càng nhỏ, chúng càng _giống nhau_. Có rất nhiều cách để định nghĩa khoảng cách. Một trong những khoảng cách thường được sử dụng nhất trong Khoa học Máy tính là _khoảng cách Euclide_ **(the Euclidean distance)**. Nghe có vẻ nguy hiểm, nhưng thực ra khoảng cách Euclide chính là những gì bạn vẫn thường hiểu về _khoảng cách_ hay _đường chim bay_.

Tuy nhiên, mặc dù khoảng cách Euclide giữa hai điểm trên bản đồ rất dễ hiểu, sẽ khó tưởng tượng hơn một chút khi bạn nói đến khoảng cách giữa hai bông diên vĩ.

Để tính khoảng cách Euclide, bạn phải tính tổng bình phương của hiệu các thuộc tính tương đương, rồi lấy căn bậc hai của tổng đó. Hãy áp dụng công thức đó cho hai bông hoa đầu tiên được biểu diễn trong bảng sau:

![table2](https://quachson.com/wp-content/uploads/table2-300x208.png)

Khoảng cách giữa hai bông diên vĩ đầu tiên là:

(6.3−6.2)^2+(2.3−3.4)2+(4.4−5.4)2+(1.3−2.3)2−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−−√=1.79


![\sqrt{(6.3-6.2)^{2}+(2.3-3.4)^{2}+(4.4-5.4^{2}+(1.3-2.3)^{2}}](http://chart.apis.google.com/chart?cht=tx&chl=%5Csqrt%7B(6.3-6.2)%5E%7B2%7D%2B(2.3-3.4)%5E%7B2%7D%2B(4.4-5.4%5E%7B2%7D%2B(1.3-2.3)%5E%7B2%7D%7D)  = ![\sqrt{15.18}](http://chart.apis.google.com/chart?cht=tx&chl=%5Csqrt%7B15.18%7D) = 3.90


Khoảng cách giữa bông hoa đầu tiên và bông hoa thứ ba là:

![](/media/chart.png )  

Giá trị đầu tiên nhỏ hơn (3.7 < 3.9), điều này có nghĩa là bông diên vĩ đầu tiên giống bông hoa thứ hai hơn so với bông hoa thứ ba.

Nhờ những bước tính toán và so sánh như trên, bạn có thể tìm ra bông hoa giống bông hoa bí ẩn nhất. Đơn giản là chúng ta chỉ cần tính khoảng cách giữa bông hoa bí ẩn với mỗi bông hoa khác, và tìm bông hoa có khoảng cách nhỏ nhất. Phương pháp tưởng chừng như đơn giản này thực ra lại được sử dụng bởi rất nhiều nhà nghiên cứu. Nó có tên là _Hàng xóm gần nhất_ (_The 1-nearest neighbors solution_)

![irises](https://quachson.com/wp-content/uploads/irises-300x287.png)


# Giải pháp 3: k-hàng xóm gần nhất (_The k-nearest neighbors solution_)


Thông thường, giải pháp _hàng xóm gần nhất_ (_The 1-nearest neighbors solution_) cho kết quả tốt, nhưng trong nhiều trường hợp, vì nhiều nguyên nhân khác nhau mà giải pháp này cho kết quả thiếu chính xác. Một trong những nguyên nhân có thể là sự thiếu chính xác trong phép đo các thuộc tính. Điều này dẫn đến việc tính khoảng cách không đúng, và như vậy thuật toán không thể tìm ra lớp (**class**) đúng nhất.

Các nhà nghiên cứu đã tìm ra một giải pháp đơn giản cho vấn đề này: Thay vì tìm ra bông diên vĩ giống nhất, chúng ta sẽ tìm 5. Nói cách khác, chúng ta tìm 5 bông diên vĩ có khoảng cách nhỏ nhất so với bông diên vĩ bí ẩn. Nếu cả 5 bông diên vĩ thuộc cùng một chủng loại, vấn đề trở nên rất đơn giản: chủng loại (hay **lớp**) của bông diên vĩ bí ẩn chính là chủng loại của 5 bông diên vĩ đó.

Tuy nhiên, sẽ thế nào nếu 5 bông diên vĩ trên thuộc về các chủng loại khác nhau? Trong trường hợp này, chúng ta sẽ đếm số lượng các bông diên vĩ trong một chủng loại, và chủng loại với số bông diên vĩ lớn nhất sẽ được coi là chủng loại của bông diên vĩ bí ẩn. Ví dụ, nếu trong 5 bông diên vĩ giống nhất, có 1 bông thuộc loại Setosa, 1 thuộc Versicolour và 3 bông còn lại thuộc loại Viginica, chúng ta có thể khá chắc chắn khi kết luận rằng bông hoa bí ẩn thuộc loại Viginica (xem hình minh hoạ phía dưới).

![irises2](https://quachson.com/wp-content/uploads/irises2-300x257.png)

Giải thuật trên được gọi là _5-hàng xóm gần nhất_ (**5-nearest neighbors**)

Có thể bạn thắc mắc tại sao chúng ta lại tìm 5 hàng xóm gần nhất thay vì 2, 10 hay 50. Chọn ra **k** tốt nhất trong giải thuật _k-hàng xóm gần nhất_ là một câu hỏi rất khó trả lời vì nó phụ thuộc vào rất nhiều vấn đề. Chúng ta sẽ không giải thích chi tiết ở đây, nhưng bạn nên biết rằng, trong thực tế, các nhà nghiên cứu thường thử rất nhiều trường hợp để tìm ra phương án tốt nhất.

Bài viết đến đây là hết. Hi vọng bạn đã có một hiểu biết sơ lược về thuật toán nổi tiếng _k-hàng xóm gần nhất_ (hay _k-nearest neighbors_). Trong bài viết tiếp theo, tác giả sẽ giới thiệu một thuật toán mới hơn, phức tạp và rất mạnh gọi là **Random Forest**.

Hẹn gặp lại các bạn trong bài viết tới!

Nguồn: [vnoi.info](http://vnoi.info/wiki/translate/ml/Machine-Learning-Classification-phan-2)
