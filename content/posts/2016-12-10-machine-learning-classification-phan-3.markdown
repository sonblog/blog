---
author: client
comments: false
date: 2016-12-10 06:22:18+00:00
template: "post"
link: https://quachson.com/machine-learning-classification-phan-3/
slug: machine-learning-classification-phan-3
title: Machine Learning – Classification – phần 3
wordpress_id: 1312
category: "ML"
description: "Trong hai bài viết trước ([phần 1]), chúng ta đã cùng tìm hiểu về Classification. Chúng ta cũng đã làm quen với một thuật toán rất nổi tiếng gọi là k-nearest neighbors. Nếu có thời gian, bạn nên đọc các bài viết đó để có thể hiểu cặn kẽ những nội dung trong bài viết này, bài viết cuối cùng trong chuỗi bài giới thiệu về"
---

Trong hai bài viết trước ([phần 1](https://quachson.com/machine-learning-classification-phan-1)) và ([phần 2](https://quachson.com/machine-learning-classification-phan-2)), chúng ta đã cùng tìm hiểu về **Classification**. Chúng ta cũng đã làm quen với một thuật toán rất nổi tiếng gọi là **k-nearest neighbors**. Nếu có thời gian, bạn nên đọc các bài viết đó để có thể hiểu cặn kẽ những nội dung trong bài viết này, bài viết cuối cùng trong chuỗi bài giới thiệu về **Classification**.

Thuật toán _k-nearest neighbors_ mà chúng ta tìm hiểu ở bài viết trước là một thuật toán được sử dụng rất rộng rãi. Tuy nhiên, nó cũng là một thuật toán rất cũ. Cho đến thời điểm này, các nhà nghiên cứu đã và đang phát triển những thuật toán phức tạp và mạnh mẽ hơn nhiều. Thuật toán tiếp theo mà tác giả muốn giới thiệu với các bạn được gọi là **Random Forest**. Đây là một thuật toán mới xuất hiện tầm 10 năm trước, và được coi là một cuộc cách mạng trong _Machine Learning_. _Random Forest_ chỉ phức tạp hơn một chút so với _k-nearest neighbors_, nhưng nó hiệu quả hơn nhiều nếu xét trên hiệu năng tính toán của máy tính. Bên cạnh đó, _Random Forest_ còn cho kết quả _chính xác_ hơn nhiều so với _k-nearest neighbors_. Nghĩa là, khi các nhà nghiên cứu kiểm thử kết quả của hai thuật toán này trên các bộ dữ liệu khác nhau (bao gồm cả _the Iris dataset_), _Random Forest_ thường cho kết quả đúng hơn so với _k-nearest neighbors_

Một trong những lí do khiến _Random Forest_ hiệu quả hơn so với _k-nearest neigbors_ là bởi vì, với _k-nearest neighbors_, tất cả các thuộc tính đều có mức độ quan trọng như nhau. Mặt khác, _Random Forest_ có khả năng tìm ra thuộc tính nào quan trọng hơn so với những thuộc tính khác. Trên thực tế, nó còn có thể chỉ ra rằng một số thuộc tính là hoàn toàn vô dụng.

_Random Forest_ là một thành viên trong họ thuật toán **decision tree** (cây quyết định). Vậy cây quyết định là gì? Một cây quyết định là một cách đơn giản để biểu diễn một giao thức (**protocol**). Nói cách khác, cây quyết định biểu diễn một kế hoạch, trả lời câu hỏi phải làm gì trong một hoàn cảnh nhất định. Ví dụ, cây quyết định được sử dụng trong tổng đài điện thoại để quyết định xem tổng đài viên sẽ trả lời như thế nào dựa trên phản hồi của khách hàng. Nó cũng được sử dụng trong hệ điều hành của bất kì cỗ máy nào mà bạn có thể tưởng tượng (tàu ngầm, bom nguyên tử,...) hay đơn giản, cây quyết định được các bác sĩ sử dụng để chẩn đoán bệnh.

Hãy trở lại câu chuyện của chúng ta với một ví dụ đơn giản. Hình ảnh phía dưới minh hoạ một cây quyết định để xác định chủng loại của một con vật. Để đơn giản, chúng ta sẽ chỉ xét một vài chủng loại động vật mà thôi. Giả sử ta có một con vật, hãy thử dùng cây quyết định này để tìm ra chủng loại của nó.

Đường đi bắt đầu từ câu hỏi đầu tiên ở phía trên của cây (bên dưới vòng tròn đỏ). Trả lời câu hỏi đó, và đi tiếp xuống các nút phía dưới của cây tuỳ thuộc vào câu trả lời (có/không với câu hỏi đầu tiên). Lặp lại hành động đó cho đến khi đi tới nút lá (các út màu xanh lá cây). Khi đó, bạn sẽ có câu trả lời.

![exampledt](https://quachson.com/wp-content/uploads/exampledt-300x245.png)

(chú thích trên hình bị sai: 50cm thay vì 50kg)

Ví dụ, bạn bắt gặp một con vật mà bạn không biết nó thuộc chủng loại gì. Câu hỏi đầu tiên là: "Nó có lông không?". Giả sử nó có lông, chúng ta đi tiếp sang nhánh bên phải. Câu hỏi tiếp theo là: "Nó cao bao nhiêu?". Giả sử con vật của chúng ta chỉ cao 30cm. Điều này có nghĩa là chúng ta sẽ đi theo nhánh bên trái. Khi đó, vì chúng ta đã đi đến nút lá, chúng ta biết rằng con vật mà mình đang xét chính là con gà.

Bây giờ chắc bạn đã hiểu phần nào về cây quyết định, hãy trở lại với thuật toán _Random Forest_: Ý tưởng phía sau _Random Forest_ khá đơn giản. Thuật toán này sinh một số cây quyết định (thường là vài trăm) và sử dụng chúng. Các câu hỏi của cây quyết định sẽ là câu hỏi về các thuộc tính. Ví dụ: "Cánh hoa có dài hơn 1.7cm hay không?". Câu giá trị ở nút lá sẽ là các lớp (_class_). Sử dụng hàng trăm cây quyết định là bất khả thi với con người, nhưng máy tính có thể làm việc này tương đối dễ dàng.

Đến lúc này chúng ta đã tìm hiểu cách sử dụng một cây quyết định, nhưng vấn đề là làm thế nào để tạo ra nó.

Có hai giải pháp. Cách thứ nhất là hỏi chuyên gia (ví dụ như một nhà nhân chủng học với bài toán phân biệt chủng loại của con vật). Nghe có vẻ hấp dẫn, nhưng không phải khi nào bạn cũng có thể tiếp cận được với chuyên gia trong bài toán của mình. Hơn nữa, bạn có thể sẽ ngạc nhiên rằng ngay cả những chuyên gia giỏi nhất cũng gặp khó khăn trong việc viết ra những kiến thức của mình. Ngay cả khi bạn tìm được một chuyên gia có khả năng đó thì chắc chắn sẽ có những thứ mà họ không biết tới. Ví dụ, nhà nhân chủng học của chúng ta có thể quên mất rằng con đà điểu có thể nhỏ hơn 50kg.

Thay vì sử dụng chuyên gia, các nhà nghiên cứu sử dụng phương án thứ hai: tạo ra một thuật toán tự sinh cây quyết định. Điều kiện duy nhất là phải có vài ví dụ để máy tính có thể tham chiếu. Trong _Iris dataset_, những ví dụ này chính là những bông hoa mà chúng ta đã biết chủng loại.

Để tạo ra một cây quyết định, thuật toán _Random Forest_ luôn bắt đầu bằng một cây rỗng. Một cây quyết định rỗng chỉ có một ô _Start_ chỉ thẳng đến câu trả lời (ô xanh lá). Tiếp theo, thuật toán sẽ tìm câu hỏi đầu tiên và bắt đầu xây dựng cây quyết định (trong ví dụ trước, câu hỏi đó là "Nó có lông không?"). Mỗi lần thuật toán tìm được thêm một câu hỏi, nó tạo hai nhánh trên cây quyết định. Khi không còn câu hỏi nào nữa, thuật toán dừng lại và chúng ta có một cây quyết định hoàn chỉnh.

Làm thế nào để tìm ra những câu hỏi tốt nhất cho cây quyết định? Đây là một bước khá phức tạp nhưng ý tưởng đằng sau nó tương đối đơn giản: Ở thời điểm bắt đầu, thuật toán của chúng ta chưa biết phân biệt các chủng loại của các con vật. Nói cách khác, tất cả các con vật được cho chung vào một "cái túi". Để tìm ra câu hỏi tốt nhất, thuật toán thử đưa ra tất cả các câu hỏi có thể (có khi là hàng triệu câu hỏi). Ví dụ: "Nó có bao nhiêu chân?", "Nó có đuôi không?",... Sau đó, với mỗi câu hỏi, thuật toán sẽ đánh giá mức độ hiệu quả mà câu hỏi này giúp phân biệt các chủng loại, hay các _class_. Câu hỏi được chọn không cần thiết phải hoàn hảo, nhưng nó phải tốt hơn những câu hỏi khác. Để tính toán mức độ hiệu quả của câu hỏi, chúng ta sử dụng một độ đo có tên là **information gain**. Chúng ta sẽ không bàn chi tiết về độ đo này, có thể hiểu nôm na nó như một cách để "cho điểm" các câu hỏi. Câu hỏi với _information gain_ lớn nhất sẽ được chọn như là câu hỏi tốt nhất để xây dựng cây quyết định.

Hình ảnh phía dưới minh hoạ 4 bước để tạo một cây quyết định đơn giản. Quá trình này sẽ được lặp lại cho tất cả các cây.

![building-dt](https://quachson.com/wp-content/uploads/building-dt-300x88.png)

Sau khi thuật toán xây dựng xong các cây quyết định, những cây này sẽ được sử dụng để trả lời câu hỏi (hay phân loại). Trong bài toán về hoa diên vĩ, thuật toán sẽ trả lời câu hỏi: "Chủng loại của bông hoa bí ẩn là gì?".

Nếu bạn theo dõi sát sao bài viết này, có thể bạn sẽ thấy một chút mâu thuẫn: chúng tôi nói với bạn rằng thuật toán _Random Forest_ xây dựng nhiều cây quyết định. Tuy nhiên, chúng tôi mới chỉ giải thích cách dựng một cây quyết định mà thôi.

**Random Forest** coi mỗi cây quyết định như một _cử tri_ bỏ phiếu độc lập (như một cuộc bầu cử thực sự). Ở cuối cuộc bầu cử, câu trả lời nhận được nhiều bầu chọn nhất từ các cây quyết định sẽ được lựa chọn.

Tuy nhiên, vẫn còn một vấn đề: Nếu như tất cả các cây được dựng theo cùng một cách, chúng sẽ cho những câu trả lời giống nhau. Như vậy chẳng khác gì chúng ta chỉ sử dụng một cây quyết định duy nhất cả. Ở đây, _Random Forest_ có một cách làm rất hay: Để chắc chắn rằng không phải tất cả các cây quyết định cho cùng câu trả lời, thuật toán _Random Forest_ chọn ngẫu nhiên các quan sát (observations). Chính xác hơn, _Random Forest_ sẽ xoá một số quan sát và lặp lại một số khác một cách ngẫu nhiên. Xét toàn cục, những quan sát này vẫn rất gần với tập các quan sát ban đầu, nhưng những thay đổi nhỏ sẽ đảm bảo rằng mỗi cây quyết định sẽ có một chút khác biệt. Quá trình này gọi là **bootstrapping**

Thêm vào đó, để thực sự chắc chắn các cây quyết định là khác nhau, thuật toán _Random Forest_ sẽ ngẫu nhiên bỏ qua một số câu hỏi khi xây dựng cây quyết định. Trong trường hợp này, nếu câu hỏi tốt nhất không được chọn, một câu hỏi kế tiếp sẽ được lựa chọn để dựng cây. Quá trình này được gọi là **attribute sampling**

Chắc rằng các bạn rất thắc mắc tại sao người ta lại tạo ra một thuật toán phức tạp như vậy: ngẫu nhiên thay đổi các quan sát và bỏ qua một số câu hỏi. Câu trả lời rất đơn giản: Có thể các mẫu thử mà chúng ta đang sử dụng chưa hoàn hảo. Ví dụ, có thể mẫu thử của chúng ta chỉ có những con mèo có lông đuôi. Trong trường hợp này những con mèo thuộc loài sphynx (mèo không lông) có thể được phân loại là con chuột. Tuy nhiên, nếu câu hỏi về đuôi không được hỏi (bởi vì sự thay đổi ngẫu nhiên), thuật toán có thể sử dụng câu hỏi các câu hỏi khác (ví dụ: Con vật đó có kích thước như thế nào?). Việc có nhiều câu hỏi đa dạng (có thể không hoàn hảo) là một ý tưởng không tồi: nó có thể là cứu tinh khi thuật toán tham chiếu đến một quan sát mà nó chưa từng thấy trước đây.

Và đó là tất cả những gì bạn cần biết về _Random Forest_.

Đây là bài viết cuối cùng trong chuỗi ba bài viết về **Classification** trong _Machine Learning_. Hi vọng bạn đã có được những hiểu biết ban đầu về bài toán phân loại, và quen thuộc với các khái niệm _quan sát_ (observations) hay _thuộc tính_ (attributes). Chúng tôi cũng đã trình bày hai thuật toán phân loại nổi tiếng, **k-nearest neighbors** và **Random Forest**, hi vọng bạn đã hiểu được phần nào về cách thức mà các thuật toán này hoạt động.

Bài viết tới mình sẽ viết về những hạn chế của **Classification**, bài tới nữa sẽ giới thiệu vệ **Hồi Quy.**

