---
author: admin
comments: true
date: 2011-09-24 18:15:14+00:00
layout: post
link: https://quachson.com/d%e1%bb%8bch-v%e1%bb%a5-m%e1%ba%a1ng-restful-khai-ni%e1%bb%87m-c%c6%a1-b%e1%ba%a3n/
slug: d%e1%bb%8bch-v%e1%bb%a5-m%e1%ba%a1ng-restful-khai-ni%e1%bb%87m-c%c6%a1-b%e1%ba%a3n
title: 'Dịch vụ mạng RESTful: Khái niệm cơ bản'
wordpress_id: 657
categories:
- Web Services
tags:
- RESTful
- Web Services
---

**Tóm tắt:**  Chuyển đổi trạng thái đại diện (REST) đã giành được sự chấp nhận rộng rãi trên mạng như là một sự thay thế đơn giản hơn đối với các dịch vụ mạng dựa trên SOAP và dựa trên ngôn ngữ miêu tả dịch vụ mạng (WSDL). Bằng chứng quan trọng của sự chuyển đổi này trong giao diện thiết kế là các nhà cung cấp dịch vụ mạng 2.0 chủ đạo đã thông qua gồm Yahoo, Google và Facebook, những công ty này đã phản đối hoặc bỏ qua các giao thức dựa trên SOAP hoặc WSDL và ủng hộ phương thức hướng đến tài nguyên và dễ sử dụng để trình bày các dịch vụ của họ. Trong bài viết này, Alex Rodriguez sẽ giới thiệu với các bạn các nguyên lý cơ bản của REST.

Nhập môn

REST xác định một nhóm các nguyên lý kiến trúc, bằng cách đó bạn có thể thiết kế các dịch vụ mạng, chú trọng vào các tài nguyên hệ thống, bao gồm các trạng thái tài nguyên được định dạng như thế nào và được chuyển tải qua HTTP thông qua một lượng lớn người dùng và được viết bởi những ngôn ngữ khác nhau. Nếu tính theo số dịch vụ mạng sử dụng, REST đã nổi lên trong một vài năm qua như là một mô hình thiết kế dịch vụ chiếm ưu thế. Thực tế là REST đã có những ảnh hưởng lớn đến như vậy đối với mạng và gần như chiếm vị trí của thiết kế giao diện dựa trên SOAP hay WSDL vì nó là cách thức đơn giản hơn rất nhiều để sử dụng.

REST không thu hút được nhiều sự chú ý khi lần đầu tiên nó được giới thiệu vào năm 2000 bởi Roy Fielding trong luận án của ông "Architectural Styles and the Design of Network-based Software Architectures" (Phong cách kiến trúc và thiết kế kiến trúc phần mềm dựa trên mạng) tại Đại học California. Luận án đã phân tích một loạt các nguyên tắc kiến trúc phần mềm sử dụng mạng như là một nền tảng tính toán phân tán (xem [Tài nguyên](http://www.ibm.com/developerworks/vn/library/ws-restful/#resources) có liên kết tới luận án). Hiện nay, vài năm sau khi được giới thiệu, các khung làm việc chính đối với REST đã được bắt đầu xuất hiện và vẫn đang được tiếp tục phát triển, vì nó đang được xem xét đề xuất ví dụ như trở thành một phần của Java™ 6 thông qua JSR-311.

Bài viết này khuyến nghị rằng trong cách thức đơn thuần nhất ngày nay, khi đã thu hút được nhiều sự chú ý thì việc thực hiện cụ thể của một dịch vụ mạng REST sẽ tuân theo bốn nguyên lý thiết kế cơ bản như sau



	
  * Sử dụng các phương thức HTTP một cách rõ ràng

	
  * Phi trạng thái

	
  * Hiển thị cấu trúc thư mục như URls

	
  * Chuyển đổi JavaScript Object Notation (JSON) và XML hoặc cả hai.


Các phần sau đây sẽ mở rộng dựa trên bốn nguyên lý này và đề xuất một nhân tố kỹ thuật cơ bản giải thích vì sao chúng quan trọng đối với các nhà thiết kế dịch vụ mạng REST.

[Về đầu trang](http://www.ibm.com/developerworks/vn/library/ws-restful/#ibm-pcon)

Sử dụng phương thức HTTP một cách rõ ràng

Một đặc tính quan trọng của dịch vụ mạng RESTful là sử dụng một cách rõ ràng phương thức HTTP theo cách một giao thức được xác định bởi RFC 2616. Ví dụ HTTP GET được xác định như là một phương thức sinh ra số liệu mà được sử dụng có chủ đích bởi các ứng dụng người dùng để thu thập được tài nguyên, thu dữ liệu từ một máy chủ mạng, hoặc thực thi một truy vấn mà máy chủ mạng sẽ tìm kiếm và phản hồi cùng với một gói tài nguyên tương thích.

REST yêu cầu các chuyên viên phát triển sử dụng phương thức HTTP một cách rõ ràng theo cách tương thích với giao thức chuẩn. Nguyên lý thiết kế REST cơ bản này thiết lập một ánh xạ 1-1 giữa các hoạt động tạo lập, đọc, cập nhật và xoá các phương thức (CRUD) và phương pháp HTTP. Theo phương thức ánh xạ này:



	
  * Để tạo một tài nguyên trên máy chủ, sử dụng POST.

	
  * Để truy xuất một tài nguyên, sử dụng GET.

	
  * Để thay đổi trạng thái một tài nguyên hoặc để cập nhật nó, sử dụng PUT.

	
  * Để huỷ bỏ hoặc xoá một tài nguyên, sử dụng DELETE.


Một thiết kế không may bị hỏng dễ nhận ra trong nhiều mạng APIs là phương thức sử dụng HTTP cho các mục đích không dự tính trước. Ví dụ lệnh URI trong một lệnh HTTP GET thường xác định một tài nguyên cụ thể. Hoặc một chuỗi truy vấn trong một lệnh URI bao gồm một nhóm các tham số xác định tiêu chí tìm kiếm được máy chủ sử dụng để tìm các tài nguyên phù hợp. Ít nhất điều này cho thấy HTTP/1.1 miêu tả GET như thế nào. Nhưng có nhiều trường hợp Web APIs không được tốt lắm, do sử dụng HTTP GET để khởi động một vài tác vụ trên máy chủ — ví dụ, thêm các bản ghi vào một cơ sở dữ liệu. Trong các trường hợp này, GET yêu cầu URI không được sử dụng đúng đắn hoặc ít ra không sử dụng REST một cách đầy đủ. Nếu Web API sử dụng GET để ra lệnh từ xa một quy trình, nó sẽ có dạng như sau:

`GET /adduser?name=Robert HTTP/1.1`

Đây không phải là mẫu thiết kế hấp dẫn vì phương pháp mạng nói trên hỗ trợ phương thức thay đổi trạng thái trên HTTP GET. Nói cách khác, phương pháp HTTP GET yêu cầu nói trên có những tác động phụ. Nếu được xử lý thành công, kết quả của yêu cầu này là để tạo thêm vào người sử dụng mới vào mẫu này — trong ví dụ này, Robert — đối với việc lưu giữ số liệu cơ bản. Vấn đề ở đây chỉ về mặt ngữ nghĩa. Những mạng máy chủ được thiết kế để tương thích với các yêu cầu của HTTP GET bằng cách truy lại mã nguồn phù hợp với đường dẫn (hoặc là tiêu chuẩn yêu cầu) theo như câu lệnh URI và gửi lại những mã nguồn này hoặc là thông tin đại diện mà không thêm mẫu dữ liệu vào cơ sở dữ liệu. Từ góc độ mục đích sử dụng giao thức đó và từ phương pháp HTTP/1.1-compliant của mạng chủ thì sử dụng GET theo cách này sẽ không thống nhất

Trên mặt ngữ nghĩa, vấn đề khác cùng với GET là để khởi động một sự xoá bỏ, sửa đổi, hoặc ghi thêm vào cơ sở dữ liệu, hoặc để thay đổi trạng thái máy chủ theo một cách nào đó. Nó kéo các công cụ lưu trữ web (các đường dẫn) và các công cụ tìm kiếm, để làm thay đổi máy chủ một cách không chủ định theo cách đơn giản bởi một đường dẫn. Một cách đơn giản để vượt qua vấn đề hay xảy ra này là dịch chuyển tên và giá trị các tham số dựa trên đòi hỏi URL đối với các thẻ XML. Các thẻ kết quả, một đại diện XML của một chủ thể được tạo ra, có thể được gửi vào một nhóm HTTP POST, những nơi mà yêu cầu URL là chủ thể sinh ra có chủ đích (xem ví dụ 1 và 2).
**Ví dụ 1. Trước**
<table cellpadding="0" width="50%" cellspacing="0" border="0" >
<tbody >
<tr >

<td >

    
            
    GET /adduser?name=Robert HTTP/1.1



</td>
</tr>
</tbody>
</table>
**Ví dụ 2. Sau**
<table cellpadding="0" width="50%" cellspacing="0" border="0" >
<tbody >
<tr >

<td >

    
            
    POST /users HTTP/1.1
    Host: myserver
    Content-Type: application/xml
    <?xml version="1.0"?>
    <user>
      <name>Robert</name>
    </user>



</td>
</tr>
</tbody>
</table>


Phương pháp trên là ví dụ của lệnh RESTful: cách sử dụng đúng HTTP POST và bao gồm cả tải trọng trong phần thân câu lệnh. Đối với phía đầu tiếp nhận, câu lệnh có thể được xử lý bằng cách thêm tài nguyên vào hệ thống đó như một phần phụ tài nguyên được định dạng trong lệnh URI; trong trường hợp này tài nguyên mới phải được thêm vào như là một nhánh con của `/users`. Quan hệ bao hàm giữa thực thể mới và nhánh mẹ, như đã xác định trong yêu cầu POST, tương tự như cách tệp đã thuộc thư mục mẹ. Máy khách thiết lập quan hệ giữa thực thể và nhánh mẹ, và xác định URI của thực thể mới trong yêu cầu POST.

Ứng dụng máy khách sau đó có thể nhận kết nối của nguồn sử dụng URI mới, lưu ý rằng ít nhất về mặt logic, nguồn được đặt dưới `/users`, như trong ví dụ 3.
**Ví dụ 3. Lệnh HTTP GET**
<table cellpadding="0" width="50%" cellspacing="0" border="0" >
<tbody >
<tr >

<td >

    
            
    GET /users/Robert HTTP/1.1
    Host: myserver
    Accept: application/xml



</td>
</tr>
</tbody>
</table>


Sử dụng GET theo cách này rất rõ ràng vì GET chỉ dành cho truy cập dữ liệu. GET là một phương thức mà không có hiệu ứng phụ, như là một đặc tính riêng _không thay đổi giá trị_.

Một cách chỉnh lại của phương thức mạng cũng cần được ứng dụng trong các trường hợp khi một thao tác cập nhật được hỗ trợ qua HTTP GET, như thể hiện trong ví dụ 4.
**Ví dụ 4. Cập nhật đối với HTTP GET**
<table cellpadding="0" width="50%" cellspacing="0" border="0" >
<tbody >
<tr >

<td >

    
            
    GET /updateuser?name=Robert&amp;newname=Bob HTTP/1.1



</td>
</tr>
</tbody>
</table>


Điều này thay đổi thuộc tính (hoặc đặc tính) `name` của tài nguyên. Trong khi chuỗi truy vấn có thể được dùng cho những phương thức như thế này, và ví dụ 4 là một ví dụ đơn giản, mẫu phương pháp dấu hiệu như là chuỗi truy vấn (query-string-as-method-signature) có xu hướng chia rẽ khi được sử dụng đối với các phương thức phức tạp hơn. Do mục tiêu của chúng ta là sử dụng phương pháp HTTP một cách rõ ràng, cách tiếp cận RESTful là gửi một yêu cầu HTTP PUT để cập nhật tài nguyên, thay vì HTTP GET, cho những lý do tương tự chỉ ra ở trên (xem ví dụ 5).
**Ví dụ 5. Lệnh HTTP PUT**
<table cellpadding="0" width="50%" cellspacing="0" border="0" >
<tbody >
<tr >

<td >

    
            
    PUT /users/Robert HTTP/1.1
    Host: myserver
    Content-Type: application/xml
    <?xml version="1.0"?>
    <user>
      <name>Bob</name>
    </user>



</td>
</tr>
</tbody>
</table>


Sử dụng PUT để thay thế tài nguyên gốc, cung cấp một giao diện sạch hơn, phù hợp với các nguyên lý của REST và các khái niệm của phương pháp HTTP. Lệnh PUT trong ví dụ 5 rõ ràng ở chỗ nó chỉ ra tài nguyên được cập nhật bằng cách xác định nó trong câu lệnh URI, và nó chuyển một đại diện mới của các thuộc tính tài nguyên chuyển đổi như là nhóm không chặt chẽ các tên tham số và giá trị trên lệnh URI. Ví dụ 5 cũng có hiệu ứng từ việc đổi tên tài nguyên từ `Robert` sang` Bob`, và trong việc các thay đổi của URI sang `/users/Bob`. Trong một dịch vụ mạng REST, lệnh tiếp theo của tài nguyên sử dụng URI cũ sẽ sinh ra lỗi căn bản 404 Not Found.

Như là một nguyên tắc thiết kế chung, nó giúp theo sát các hướng dẫn sử dụng REST để sử dụng phương pháp HTTP một cách rõ ràng bằng cách sử dụng các danh từ trong URIs thay vì động từ. Trong một dịch vụ mạng RESTful, các động từ — POST, GET, PUT, và DELETE — đã được xác định bởi giao thức. Và tốt nhất, để giữ giao diện được khái quát hoá và cho phép các khách dùng thông tỏ về phương thức họ đề xuất, dịch vụ mạng không nên đưa ra nhiều động từ hoặc các quy trình từ xa, như `/adduser` hoặc `/updateuser`. Nguyên tắc thiết kế chung này cũng áp dụng đối với phần thân câu lệnh HTTP, cái mà được sử dụng có chủ ý để chuyển trạng thái tài nguyên, không mang tên của một phương thức từ xa hoặc quy trình từ xa được đề xuất.

[Về đầu trang](http://www.ibm.com/developerworks/vn/library/ws-restful/#ibm-pcon)

Phi trạng thái

Các dịch vụ mạng REST cần được điều chỉnh về quy mô để đáp ứng được các yêu cầu ngày càng cao về chất lượng thực hiện. Các khu vực lưu trữ của máy chủ với khả năng cân bằng tải và vượt qua sự mất mát, các bức ngăn (tường lửa) và các cổng được sắp xếp theo một phương thức đặc thù nhằm tạo ra một cấu trúc dịch vụ bền vững, mà được phép yêu cầu để chuyển tiếp từ một máy chủ tới máy chủ khác khi cần để giảm tổng thời gian phản hồi của một yêu cầu dịch vụ mạng. Sử dụng máy chủ trung gian nhằm nâng cao mức yêu cầu dịch vụ mạng REST của khách hàng để gửi các yêu cầu hoàn chỉnh và độc lập, có nghĩa là gửi các yêu cầu bao gồm tất cả dữ liệu cần thiết để đáp ứng sao cho các thành phần trong các máy chủ trung gian có thể gửi tiếp đi, gửi theo tuyến và cân bằng tải mà không cần các trạng thái được kiểm soát bên trong giữa các yêu cầu.

Một yêu cầu hoàn chỉnh, độc lập không đòi hỏi máy chủ, trong khi xử lý yêu cầu, để thu thập được bất kỳ ngữ cảnh hoặc trạng thái của ứng dụng. Một ứng dụng (hoặc máy khách) dịch vụ mạng REST bao gồm giữa phần đầu và phần thân trang HTTP của một yêu cầu các tham số, ngữ cảnh và dữ liệu cần thiết bởi thành phần của máy chủ để đưa ra một phản hồi. Phi trạng thái theo nghĩa này nâng cao tính hiệu quả của dịch vụ Web, đơn giản hoá thiết kế và sự thi hành của các thành phần của máy chủ vì khi máy chủ không có trạng thái sẽ huỷ bỏ nhu cầu để đồng bộ hoá các mảng dữ liệu với một ứng dụng bên ngoài.

Hình 1 minh hoạ một dịch vụ trạng thái, từ đó một ứng dụng có thể yêu cầu trang sau trong một tập hợp các trang kết quả, giả sử rằng dịch vụ theo sát ứng dụng dừng lại ở nơi trong khi điều chỉnh tập hợp đó. Đối với thiết kế trạng thái, dịch vụ gia tăng và lưu giữ một `previousPage` (trang trước) thay đổi ở nơi để có thể phản hồi các lệnh tiếp theo.
**Hình 1. Thiết kế trạng thái**
![Thiết kế trạng thái](http://www.ibm.com/developerworks/vn/library/ws-restful/figure1.gif)

Dịch vụ trạng thái như thế này trở nên phức tạp. Trong môi trường Nền tảng Java, Phiên bản Doanh nghiệp (EE), dịch vụ trạng thái yêu cầu rất cẩn thận lúc ban đầu để lưu trữ hiệu quả và cho phép đồng bộ hoá dữ liệu phiên qua một vùng của các thành phần chứa (containers) Java EE. Trong môi trường này, có một vấn đề quen thuộc đối với các chuyên viên phát triển servlet/JavaServer Pages (JSP) và Enterprise JavaBeans (EJB), những người này thường gặp khó khăn khi tìm gốc rễ nguyên nhân của` java.io.NotSerializableException` trong khi sao bản phiên. Liệu nó được chuyển bởi thành phần chứa Servelet trong khi` HttpSession` sao bản hoặc chuyển đi bởi thành phần chứa EJB trong khi sao bản EJB trạng thái, đó là vấn đề mà có thể làm các chuyên viên phát triển mất nhiều ngày để xác định mấu chốt một đối tượng mà không thực thi `Serializable`, đôi khi trong một đồ thị phức tạp của các đối tượng mà đóng góp nên trạng thái của máy chủ. Ngoài ra, phần tối ưu hoá làm đội thêm chi phí ảnh hưởng đến hiệu quả của máy chủ.

Mặt khác, các thành phần máy chủ phi trạng thái ít phức tạp hơn để thiết kế, viết và phân bổ thông qua máy chủ được cân bằng tải. Dịch vụ phi trạng thái không chỉ hoạt động tốt hơn, nó còn chuyển hầu hết vai trò duy trì trạng thái sang ứng dụng ở máy khách. Trong một dịch vụ mạng RESTful, máy chủ chịu trách nhiệm đưa ra các phản hồi và cung cấp một giao diện cho phép máy khách duy trì trạng thái ứng dụng của chính nó. Ví dụ, trong yêu cầu tập hợp trang kết quả, máy khách sẽ gồm số trang thực tế khi truy xuất thay vì đơn giản chỉ là yêu cầu _tiếp theo_ (xem hình 2).
**Hình 2. Thiết kế phi trạng thái**
![Thiết kế phi trạng thái](http://www.ibm.com/developerworks/vn/library/ws-restful/figure2.gif)

Một dịch Web phi trạng thái sinh ra một phản hồi liên kết với số trang tiếp theo trong một tổng thể và để máy khách làm những gì mà nó cần để giữ giá trị này ở mức nhất định. Khía cạnh này của thiết kế dịch vụ Web RESTful có thể được tách thành hai phần trách nhiệm như là mức phân chia cao nhất mà chỉ rõ một dịch vụ phi trạng thái có thể được duy trì như thế nào.

**Máy chủ**



	
  * Phát ra các phản hồi bao gồm các đường kết nối tới các tài nguyên khác cho phép các ứng dụng điều hướng giữa các tài nguyên liên quan. Loại phản hồi này nhúng các liên kết. Tương tự, nếu các yêu cầu đối với máy chủ hoặc các kho tài nguyên, thì các phản hồi dịch vụ RESTful điển hình có thể bao gồm các đường dẫn đến các máy con hoặc các tài nguyên phụ sao cho những phản hồi này được duy trì kết nối.

	
  * Phát ra các phản hồi mà xác định chúng có thể lưu trữ hoặc không phải để nâng cao được hiệu quả bằng cách giảm số lượng yêu cầu đối với các tài nguyên trùng nhau và bằng cách loại trừ một vài yêu cầu toàn bộ. Máy chủ làm được như vậy bằng cách gộp một phản hồi phần đầu HTTP Last - Modified (lần sửa gần nhất) (giá trị ngày) và Cache-Control (bộ điều khiển lưu trữ).


**Ứng dụng máy khách**



	
  * Sử dụng phần đầu phản hồi Cache-Control (bộ điều khiển lưu trữ tạm) để xác định lưu trữ tài nguyên (lập một vùng sao chép nội bộ) hay không. Máy khách cũng đọc phần đầu phản hồi Last-Modified (lần sửa gần nhất) và gửi lại giá trị ngày vào phần đầu If-Modified-Since (nếu-sửa) để truy vấn máy chủ xem tài nguyên có thay đổi không. Việc này được gọi là truy vấn có điều kiện, và hai phần đầu đi với nhau trong phản hồi của máy chủ là mã 304 chuẩn (không sửa đổi) và bỏ qua tài nguyên thực được yêu cầu nếu nó không thay đổi. Một mã phản hồi HTTP có nghĩa rằng máy khách có thể sử dụng an toàn một vùng sao lưu nội bộ, được lưu trữ của đại diện tài nguyên một cách cập nhật nhất, hiệu quả bằng cách vượt qua yêu cầu GET tiếp theo cho đến khi tài nguyên thay đổi.

	
  * Gửi các yêu cầu hoàn chỉnh mà có thể được đáp ứng độc lập bởi các yêu cầu khác. Điều này đòi hỏi máy khách sử dụng toàn bộ các phần đầu HTTP như chỉ định bởi giao diện dịch vụ mạng và để gửi các đại diện tài nguyên hoàn chỉnh trong phần giữa của yêu cầu. Máy khách gửi yêu cầu lập một vài giả thuyết về các yêu cầu trước đó, sự tồn tại của một vùng của máy chủ, khả năng của máy chủ để thêm các ngữ cảnh vào yêu cầu, hoặc về các trạng thái ứng dụng mà được giữ giữa các yêu cầu.


Sự hợp tác này giữa ứng dụng máy khách và máy chủ là cần thiết để có một phi trạng thái trong một dịch vụ mạng RESful. Nó nâng cao hiệu quả bằng cách tiết kiệm băng thông và tối thiểu hoá trạng thái ứng dụng về phía máy chủ.

[Về đầu trang](http://www.ibm.com/developerworks/vn/library/ws-restful/#ibm-pcon)

Đưa ra cấu trúc thư mục giống URIs

Từ điểm hiện có của tài nguyên địa chỉ ứng dụng máy khách, các đường dẫn xác định tính hiện thực của dịch vụ mạng REST như thế nào, và được sử dụng theo cách các chuyên viên thiết kế có thể tham gia. Tính năng thứ ba của dịch vụ mạng RESful về tất cả đường dẫn.

Các địa chỉ dịch vụ mạng REST nên có tính hiện thực theo nghĩa rằng chúng dễ dàng đối với người dùng khách. Có thể nghĩ rằng một địa chỉ đường dẫn như là giao diện tự đóng gói mà đòi hỏi ít lý giải hoặc tham chiếu, nếu có, đối với một nhà phát triển để hiểu nó nhắm đến điểm gì và phân phát tài nguyên liên quan. Cuối cùng, cấu trúc của một địa chỉ nên rõ ràng, có thể đoán được và dễ hiểu.

Một cách để đạt được mức độ sử dụng này là xác định cấu trúc thư mục giống URIs. Loại URI này có thứ bậc, có điểm khởi nguồn tại một đường dẫn đơn giản, và có nhánh đi ra là các nhánh phụ thể hiện các vùng chính của dịch vụ. Theo định nghĩa này, một URI không chỉ là một chuỗi bị cắt không giới hạn, mà còn là một cây với các nhánh chính và nhánh dọc nối với nhau tại các nút. Ví dụ, trong một thảo luận dịch vụ nhỏ thu thập các chủ đề từ Java tới bài viết, bạn có thể định nghĩa một tập hợp được cấu trúc bởi URIs giống như sau:

` http://www.myservice.org/discussion/topics/{topic}`

Phần gốc, `/discussion`, có một nút `/topics` bên dưới nó. Phía dưới là một chuỗi tên các tên chủ đề, như chuyện xã hội, kỹ thuật, v.v.., mỗi chủ đề chỉ ra một mạch thảo luận. Trong cấu trúc này, dễ dàng kéo các mạch thảo luận bằng cách gõ một vài thứ sau /topics/.

Trong một vài trường hợp, đường dẫn tới một tài nguyên cho mượn chính nó đặc biệt tốt với cấu trúc giống cây thư mục. Ví dụ, tài nguyên được cấu trúc bởi ngày, điều mà phối hợp rất tốt để sử dụng một cú pháp đẳng cấp.

Ví dụ này trực quan vì nó dựa trên các nguyên tắc:

` http://www.myservice.org/discussion/2008/12/10/{topic}`

Phân mảnh đường dẫn đầu tiên là năm có bốn chữ số, phân mảnh thứ hai là ngày có hai chữ số, và phân mảnh thứ ba là tháng có hai chữ số. Có vẻ hơi ngu ngốc khi giải thích theo cách này, nhưng đây là mức độ đơn giản. Con người và máy móc có thể dễ dàng sinh ra các cấu trúc URIs giống như vậy vì chúng dựa trên các nguyên tắc. Bổ sung vào các phần đường dẫn trong các khe của một cú pháp làm cho chúng tốt hơn vì có một mẫu xác định từ đó để soạn chúng.

` http://www.myservice.org/discussion/{year}/{day}/{month}/{topic}`

Một vài hướng dẫn bổ sung để lưu ý trong khi nói về cấu trúc địa chỉ của dịch vụ mạng RESTful là:



	
  * Giấu các đuôi tài liệu mở rộng của bản gốc trong máy chủ (.jsp, .php, .asp), nếu có, vì vậy bạn có thể giấu một số thứ mà không cần thay đổi địa chỉ Urls.

	
  * Để mọi thứ là chữ thường.

	
  * Thay thế các khoảng trống bằng gạch chân hoặc hoặc gạch nối (một trong hai loại).

	
  * Tránh các chuỗi yêu cầu càng nhiều càng tốt.

	
  * Thay vì sử dụng mã (404 Not Found) khi yêu cầu địa chỉ cho một phần đường dẫn, luôn luôn cung cấp một trang mặc định hoặc tài nguyên như là một phản hồi.


Các địa chỉ (URIs) nên không thay đổi để khi tài nguyên thay đổi hoặc khi tiến hành thay đổi dịch vụ, đường liên kết sẽ giữ nguyên. Việc này cho phép đánh dấu lại vị trí đang đọc. Nó cũng rất quan trọng vì mối liên quan giữa các tài nguyên mà được mã hoá trong các địa chỉ được giữ nguyên độc lập với các mối liên quan đại diện khi chúng được lưu trữ.

[Về đầu trang](http://www.ibm.com/developerworks/vn/library/ws-restful/#ibm-pcon)

Chuyển đổi XML, JSON, hoặc cả hai

Một tài nguyên đại diện điển hình phản ánh trạng thái hiện tại của một tài nguyên, và các thuộc tính của nó, tại thời điểm một ứng dụng máy khách yêu cầu nó. Các đại diện tài nguyên theo nghĩa này là chỉ các bản tóm tắt lúc đó. Điều này có thể đơn giản như một đại diện của một bản ghi trong một cơ sở dữ liệu, bao gồm một tổng thể giữa tên các cột và các thẻ XML, nơi các giá trị thành phần trong XML bao gồm các giá trị dòng. Hoặc nếu hệ thống có một mô hình dữ liệu, thì theo định nghĩa này một tài nguyên đại diện là một bản tóm tắt các thuộc tính của những thứ trong mô hình dữ liệu hệ thống. Đây là những điều bạn muốn dịch vụ mạng REST mang đến.

Những trở ngại cuối cùng, đi kèm với thiết kế dịch vụ mạng RESTful, phải làm với định dạng dữ liệu mà ứng dụng và trao đổi dịch vụ trong mức đáp ứng yêu cầu/phản hồi hoặc trong phần thân của HTTP. Đây chính là điều nó làm để giữ mọi thứ đơn giản, con người có thể đọc được và được kết nối.

Các chủ thể trong mô hình dữ liệu của bạn thường liên quan đến nhau theo cách nào đó, và mối liên hệ giữa mô hình dữ liệu chủ thể (tài nguyên) nên được phản ánh theo chúng được đại diện để chuyển đến một ứng dụng máy khách. Trong dịch vụ chuỗi thảo luận, một ví dụ của đại diện tài nguyên được kết nối có thể bao gồm một chủ đề thảo luận gốc và các thuộc tính của nó, và các đường dẫn được nhúng vào các phản hồi nhất định của chủ đề đó.
**Ví dụ 6. Đại diện XML của một chuỗi thảo luận**
<table cellpadding="0" width="50%" cellspacing="0" border="0" >
<tbody >
<tr >

<td >

    
            
    <?xml version="1.0"?>
    <discussion date="{date}" topic="{topic}">
      <comment>{comment}</comment>
      <replies>
        <reply from="joe@mail.com" href="/discussion/topics/{topic}/joe"/>
        <reply from="bob@mail.com" href="/discussion/topics/{topic}/bob"/>
      </replies>
    </discussion>



</td>
</tr>
</tbody>
</table>


Cuối cùng, để đưa đến khả năng yêu cầu loại nội dung cụ thể cho các ứng dụng máy khách mà phù hợp nhất với chúng, hãy cấu trúc dịch vụ của bạn sao cho nó tận dụng được phần đầu chấp nhận HTTP sẵn có bên trong, nơi giá trị của phần đầu là một loại MIME. Một vài loại MIME thông thường được sử dụng bởi dịch vụ RESTful được thể hiện trong Bảng 1.
**Bảng 1. Loại MIME phổ biến được sử dụng bởi dịch vụ RESTful**
<table cellpadding="0" width="50%" cellspacing="0" border="0" summary="" >
<tbody >
<tr >
MIME-Type
Content-Type
</tr>
<tr >
JSON

<td >application/json
</td>
</tr>
<tr >
XML

<td >application/xml
</td>
</tr>
<tr >
XHTML

<td >application/xhtml+xml
</td>
</tr>
</tbody>
</table>
Nó cho phép dịch vụ được nhiều khách hàng khác nhau sử dụng, viết bằng các ngôn ngữ khác nhau, chạy trên nền và thiết bị khác nhau. Sử dụng kiểu MIME và phần đầu HTTP Accept là một cơ chế được biết như là _nội dung thương thuyết_, cái mà cho phép máy khách chọn định dạng dữ liệu nào là đúng với chúng và tối thiểu hoá sự nối lại giữa dịch vụ và các ứng dụng mà sử dụng nó.

[Về đầu trang](http://www.ibm.com/developerworks/vn/library/ws-restful/#ibm-pcon)

Kết luận

REST không phải là sự lựa chọn luôn đúng. Đã có trường hợp khi thiết kế dịch vụ mạng, nó có sự kém độc lập đối với phần mềm trung gian (ví dụ: một ứng dụng máy chủ) so với loại dựa trên SOAP hặc WSDL. Theo nghĩa này, REST là một sự quay lại con đường mạng trước thời đại ứng dụng máy chủ rất lớn, kể cả ấn tượng các chuẩn của internet thời kỳ đầu, địa chỉ và HTTP. Bạn vừa nghiên cứu nguyên tắc gọi là thiết kế giao diện RESTful, XML so với HTTP là một giao diện vượt trội cho phép các ứng dụng bên trong, như các giao diện người dùng dựa trên Asynchronous JavaScript + XML (Ajax), dễ dàng kết nối, xác định, và tiêu thụ tài nguyên. Thực tế, sự tương thích lớn giữa Aax và REST đã nhận được rất nhiều sự chú ý gần đây.

Đưa một tài nguyên hệ thống thông qua một RESTful API là một cách linh động để cung cấp các loại ứng dụng khác nhau với dữ liệu đã được định dạng theo cách tiêu chuẩn. Nó giúp đáp ứng các yêu cầu tích hợp, điều rất quan trọng để xây dựng hệ thống khi dữ liệu được kết hợp dễ dàng (mashups) và để mở rộng hoặc xây dựng trên một gói hệ thống căn bản. Dịch vụ RESTful có thể rất lớn đối với một số thứ. Bài viết này hướng dẫn dựa vào nguyên lý cơ bản trên và hy vọng bằng cách nào đó sẽ khuyến khích bạn khám phá chủ đề này.



Tài nguyên

**Học tập**



	
  * Đọc chương 5 luận án của Roy Fielding [Architectural Styles and the Design of Network-based Software Architectures (Phong cách kiến trúc và thiết kế kiến trúc phần mềm dựa trên mạng)](http://www.ics.uci.edu/%7Efielding/pubs/dissertation/rest_arch_style.htm)."

	
  * Tìm thêm thông tin tại [RFC 2616: Hypertext Transfer Protocol -- HTTP/1.1](ftp://ftp.isi.edu/in-notes/rfc2616.txt)

	
  * Đọc sách _ [RESTful Web Services](http://www.oreilly.com/catalog/9780596529260/) _.

	
  * Địa chỉ [SOA and Web services zone](http://www.ibm.com/developerworks/webservices?S_TACT=105AGY75) trên trang web của IBM developerWorks, đăng hàng trăm thông tin về các bài viết phong phú thông tin và các bài giảng về giới thiệu, trung cấp, hoặc cao cấp để làm sao phát triển ứng dụng dịch vụ mạng.

	
  * Thực hành tại [IBM SOA Sandbox](http://www.ibm.com/developerworks/downloads/soasandbox/?S_TACT=105AGY75)! Nâng cao kỹ năng SOA của bạn thông qua thực hành, kinh nghiệm thực tế cùng với các bài nhập môn IBM SOA.

	
  * [Trang web IBM SOA](http://www.ibm.com/software/solutions/soa/) đưa ra một tổng thể của SOA và làm thế nào IBM có thể giúp bạn ở đây.

	
  * Hãy tham gia [các sự kiện kỹ thuật developerWorks và web quảng bá ](http://www.ibm.com/developerworks/offers/techbriefings?S_TACT=105AGY75).

	
  * Tìm các sách cùng hoặc khác chủ đề kỹ thuật tại [Hiệu sách Safari](http://safari.bvdep.com/?x=1&portal=bvdep&uicode=&%20Key=&GUID=D1F1DB57-50AF-4998-99-DA-6D-BB-A5-E0-E4-0B).

	
  * Đọc thêm các tài liệu [Web services on demand demo](http://www.ibm.com/developerworks/offers/lp/demos/?S_TACT=105AGY75).


**Lấy sản phẩm và công nghệ**



	
  * Tải về [JSR 311: JAX-RS: The Java API for RESTful Web Services](http://www.jcp.org/en/jsr/detail?id=311).

	
  * Lấy [Jersey (GlassFish)](https://jersey.dev.java.net/).

	
  * Tải về [Restlet](http://www.restlet.org/), the REST framework for Java.

	
  * Tải về [Phiên bản đánh giá sản phẩm của IBM](http://www.ibm.com/developerworks/downloads/?S_TACT=105AGY75) và bạn có các công cụ phát triển ứng dụng và các phần mềm trung gian từ DB2®, Lotus®, Rational®, Tivoli®, and WebSphere®.


