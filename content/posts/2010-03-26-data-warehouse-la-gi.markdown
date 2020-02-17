---
author: admin
comments: true
date: 2010-03-26 05:03:15+00:00
template: "post"
link: https://quachson.com/data-warehouse-la-gi/
slug: data-warehouse-la-gi
title: Data Warehouse là gì
wordpress_id: 130
categories:
- Data WareHouse
tags:
- Data WareHouse
---

Một định nghĩa chính thức của data warehouse trong wikipedia chẳng hạn cũng mất cả một trang để giải thích. Bản thân tôi nếu được hỏi, có lẽ câu trả lời sẽ là: data warehouse là một cơ sở dữ liệu được tập hợp từ nhiều nguồn của một tổ chức và chủ yếu được dùng cho việc báo cáo (reporting) và phân tích (analysis). Cách tốt nhất để hiểu khái niệm này theo tôi là nên trực tiếp xây dựng một data warehouse database.

Trước hết, có lẽ những ai học xong 4 năm IT trong trường đều biết một cơ sở dữ liệu là như thế nào. Một ứng dụng (application) thường có một database để chứa các thông tin hoạt động của ứng dụng đó. Một tổ chức (organization, company...etc) có thể có nhiều ứng dụng, do vậy nhiều database khác nhau. Mỗi ứng dụng thường tập trung vào một lĩnh vực hoạt động hay kinh doanh (domain) cụ thể nào đó. Lấy ví dụ một ngân hàng thường sẽ có một ứng dụng banking để quản lý các tài khoản và giao dịch cá nhân như checking account (debit card), saving account, credit card... Đồng thời, ngân hàng cũng có một ứng dụng khác chuyên quản lý về các khoản vay, chẳng hạn vay tiền để mua nhà hoặc để đi học. Như vậy trong trường hợp này, ít nhất có 2 operational database cùng tồn tại trong một ngân hàng.

Operational database thứ nhất chuyên về các giao dịch cá nhân (banking transaction) hàng ngày. Cuối tháng công ty của bạn trả lương bằng cách nạp (deposit) một khoản tiền vào tài khoản. Còn bạn thì hăm hở đi ra ATM ở Vincom để rút tiền (credit) vào tối thứ sáu trước khi đưa bạn gái đi ăn tối ở tầng 15 khách sạn Melia và xem phim Mùa hè 500 ngày ở rạp Tháng Tám. Do đó, có ít nhất 2 transaction records đã được chèn vào database.

Tương tự, khi bạn cần vay ngân hàng tiền để mua một căn hộ mới ở khu Mỹ Đình để chung sống cùng cô vợ mới cưới (với điều kiện dinner + movie worked pretty well), thông tin về bạn sẽ được nạp vào một operational database chuyên về các khoản vay. Mỗi tháng ngân hàng yêu cầu bạn đóng một khoản tiền để trả nợ bao gồm cả lãi suất trong đó. Một transaction record sẽ được đưa vào database chuyên về cho vay này hàng tháng.

Như vậy có thể thấy 2 cơ sở dữ liệu ở trên được dùng với mục đích duy trì hoạt động hàng ngày của ngân hàng. Do vậy, được gọi là **Operational Database**.

Một ngày đẹp trời, ngân hàng của bạn quyết định đưa ra một chiến lược kinh doanh mới để thúc đẩy các hoạt động trong mảng cho vay bởi đây là thị trường rất tiềm năng. Để làm được điều này, ngân hàng cần biết đối tượng nào có nhu cầu mua nhà nhất, thường mua nhà loại nào, giá nhà nằm trong khoảng nào, khả năng chi trả ra sao. Một cách để biết được điều này là ngân hàng có thể so sánh số liệu của 2 năm 2008 và 2009 nhằm vào đối tượng là tầng lớp trung lưu văn phòng tuổi 25-30, thu nhập hàng tháng $500-$700, nhà mua là loại căn hộ 2 phòng ngủ, địa điểm là quanh khu đô thị mới Phạm Hùng. Nếu số liệu của năm 2009 cao hơn 2008, có thể dự đoán là nhu cầu của nhóm này tăng lên, do vậy ngân hàng có thể phát động các gói khuyến mãi dành riêng cho lớp này. Chẳng hạn, khoản vay có thể lớn hơn, lãi suất ưu đãi hơn, ngân hàng sẽ chịu trách nhiệm trong việc làm sổ đỏ...vv.

Để thực hiện điều này, rõ ràng ngân hàng của bạn sẽ phải thu gom dữ liệu từ 2 cơ sở dữ liệu trên hoặc mua dữ liệu từ một cơ quan chuyên về địa ốc nào đó. Do tên của bạn có thể sẽ xuất hiện trong các operational database khác nhau, người ta sẽ phải tìm cách để đồng nhất các thông tin này rồi dựa trên đó áp dụng các công thức tính toán thích hợp để dẫn đến cái báo cáo như ở trên.

Do đây là một quá trình không hề đơn giản, nhiều khả năng ngân hàng sẽ phải dùng một câu lệnh SQL cực kỳ phức tạp và dài ngoằng. Gặp trường hợp dữ liệu đến từ nhiều nguồn khác nhau (csv, xml...), thậm chí có thể sẽ phải xây dựng các temp tables ngay trong operational database để thực hiện các bước trung gian. Một cách khác có thể là lập trình riêng một module cho báo cáo này. Tất cả những cách tiếp cận nói trên đều không mang tính hệ thống và thậm chí ảnh hưởng đến operational database.

Từ những lý do này, một cơ sở dữ liệu riêng cần phải được thành lập để có thể tập hợp thông tin từ nhiều nguồn khác nhau, chuẩn hóa nó, tối ưu tốc độ để phục vụ cho việc phân tích và lập báo cáo. Nói cách khác, đó là một **data warehouse**.

**_Nhận xét của cá nhân:_**

Data warehouse nên được xây dựng từ trên yêu cầu của business. Thường thì các yêu cầu này liên quan đến việc sử dụng các số liệu tổng hợp, chẳng hạn count, sum, max, min, average... Thường thì người ta sử dụng các số liệu kiểu này để phân tích xu hướng (trend).

Nếu không được định hướng bởi business, hoặc đơn giản chỉ bởi vì ai đó muốn xây dựng data warehouse... theo phong trào, một data warehouse như vậy nhiều khi không khác gì một bản copy của operational database với khác biệt duy nhất là nó chạy trên một máy tính mà thôi. Hiển nhiên là như vậy là lãng phí tiền bạc và công sức, trừ khi người ta thực sự muốn như thế.

Một data warehouse thường làm việc với hàng trăm, hàng nghìn, hàng triệu record một lúc. Trong khi đó, một operational database thường làm việc với 1 record.

**Một Data Warehouse phải đảm bảo được các mục tiêu sau**:

**Truy cập dễ dàng:**
Thông tin lưu trữ trong data warrehouse phải trực quan và dễ hiểu đối với người dùng. Nói cách khác, dữ liệu nên được trình bày thông qua các tên gọi quen thuộc và gần gũi với nghiệp vụ của người dùng.

Qua một số dự án đã làm tôi thấy có thể phân chia businiess user ra 2 loại. Người dùng cấp thấp chủ yếu thao tác trên các thông tin chi tiết. Chẳng hạn như nhập số liệu về một khách hàng, theo dõi các giao dịch của khách hàng cụ thể đó... Report cho dạng công việc kiểu này thường là thông tin chi tiết về một khách hàng, hoặc một danh sách các khách hàng. Những report kiểu này có thể lấy ra trực tiếp từ operational database.

Người dùng cấp cao lại chủ yếu xử lý dữ liệu ở mức độ tổng hợp, để từ đó phân tích rồi đưa ra các quyết định mang tính định hướng cho nghiệp vụ. Họ không quan tâm đến một khách hàng cụ thể nào cũng như không cần phải để ý cả một danh sách 1000 khách hàng. Thay vào đó, cái làm họ bận tâm là số lượng khách hàng sử dụng dịch tăng/giảm 25% trong quý IV so với quý III cùng năm và tăng/giảm 45% so với cùng quý IV năm ngoái. Từ các thông số này, họ mới đưa ra quyết định sẽ làm gì để cải thiện tình hình hoặc đặt ra mục tiêu tăng trưởng 30% cho quý IV năm tới. Đây là đối tượng chủ yếu của Data Warehouse.

Do vậy, thông tin cho loại đối tượng này càng dễ hiểu và gần với thực tế càng tốt. Một ví dụ dễ thấy là thay vì sử dụng các code, data warehouse nên thể hiện thông tin bằng các description hoặc name.

Một điều nữa cần bàn đến là tốc độ truy cập data warehouse phải nhanh. Do phải xử lý một số lượng lớn bản ghi cùng một lúc, performance là một trong những yêu cầu phải có của một dw. Đây là nơi mà các kỹ thuật tuning database được dịp phát huy hết công suất: query tuning, query hints, indexes, parallel processing, partition, materialized views....

Riêng bản thân tôi nghĩ, đối với những người xây dựng dw, đây là mảnh đất tốt để nâng cao khả năng làm việc với database lên mức expert. Mặc dù không chính thức bắt buộc, nhưng phần lớn những người làm dw tốt đều có kiến thức rất sâu về database. Nhiều người thậm chí còn ở mức DB Administrator. Với nhu cầu về dữ liệu càng lúc càng lớn như hiện nay, sở hữu nhiều kỹ năng tốt cùng một lúc có thể đem lại cho bạn nhiều lựa chọn và lợi thế hơn trong thị trường việc làm.

**Thông tin nhất quán:**

Dữ liệu trong một data warehouse nhìn chung thường đến từ nhiều nguồn khác nhau. Do vậy, cùng một thông tin nhưng các nguồn khác nhau có thể trình bày nó theo các kiểu khác nhau, thậm chí còn sai lệch ít nhiều. Một ví dụ đơn giản là cùng khách hàng tên Huy Nguyen, database A lưu trữ thông tin này trong 2 trường First_Name và Last_Name, trong khi database B có thể chỉ có một trường duy nhất Ho_va_Ten. Một cái tên công ty như International Business Trading trong database A được thể hiện đầy đủ như trên, nhưng trong database B có khi lại được trình bày dưới dạng viết tắt như Intl. Biz Trading.

Một đặc điểm nữa của dữ liệu database là không có database nào chứa dữ liệu sạch 100%. Cho dù có là dữ liệu của một công ty hàng đầu về IT như Google, Amazon, Microsoft... đảm bảo vẫn có lỗi. Database càng to càng dễ có dữ liệu không sạch. Một ví dụ dễ thấy là một trường Description có thể chứa các ký tự điều khiển CR LF. Điều này xảy ra khi người dùng nhấn Enter nhiều lần để tạo ra các đoạn văn bản trong cùng một ô area box. Nhiều lúc dữ liệu sai xuất hiện trong database là do lỗi lập trình. Tôi đã gặp một trường hợp như sau. Một trường datetime trong Oracle database có giá trị hẳn hoi (not null) nhưng không sao convert được sang kiểu varchar2. Tìm hiểu một hồi mới thấy trong một số bản ghi, giá trị thực của trường đó là... vô định, tức là dữ liệu thì có nhưng nó không mang một giá trị cụ thể nào. Lý do có lẽ là một Java developer nào đó khi tạo lập một Date instance .... quên mất không assign một giá trị nào cho đối tượng đó. Do vậy, đối tượng thì có nhưng giá trị thực trong nó thì vô định. Về mặt kỹ thuật mà nói, điều này vẫn hợp lệ nên vẫn được chèn vào database. Chỉ khi nào convert dữ liệu thì lỗi này mới xuất hiện, nếu không nó sẽ "nằm im" trong suốt cả vòng đời của ứng dụng mà không ai biết.

Nói vậy để thấy, trước khi được đưa vào data warehouse, dữ liệu cần phải được làm sạch và đảm bảo về chất lượng. Có làm sạch rồi thì việc đồng nhất dữ liệu mới trở nên dễ dàng. Một nguyên tắc đơn giản được đặt ra cho quá trình này là:
- Nếu dữ liệu có cùng tên, chúng bắt buộc phải cùng chỉ đến một thực thể.
- Ngược lại, nếu dữ liệu chỉ đến các thực thể khác nhau, chúng phải được đặt tên khác nhau.

Đây chính là những công việc chủ đạo của quá trình ETL (Extract - Transform - Load).

**Thích nghi với thay đổi:**
Thay đổi là điều không thể tránh khỏi cho bất cứ ứng dụng nào, không riêng gì data warehouse. Do vậy, data warehouse cần phải được thiết kế để xử lý những thay đổi có thể xảy ra. Nói vậy có nghĩa là khi có thay đổi mới, dữ liệu cũ trong data vẫn phải được bảo tồn tính đúng đắn.

**Bảo mật:**
Dữ liệu trong data warehouse đến từ nhiều nguồn khác nhau, do vậy hiển nhiên việc bảo đảm những thông tin không lộ ra ngoài là một yêu cần thiết yếu. Để lộ dữ liệu của một database đã là cực kỳ nghiêm trọng. Để lộ dữ liệu từ nhiều database là thảm họa.

**Hỗ trợ ra quyết định:**
Đây có thể nói là mục tiêu quan trọng nhất của doanh nghiệp khi xây dựng data warehouse. Mặc dù có những trường hợp xây dựng một cơ sở dữ liệu tập trung để thu thập data từ nhiều nguồn khác nhau, nhưng tôi cho rằng những trường hợp như vậy nên gọi là data integration (tích hợp dữ liệu) chứ không phải data warehouse. Một doanh nghiệp trước khi xây dựng data warehouse, nên tự đặt câu hỏi liệu data warehouse đó có giúp ích gì trong việc ra quyết định kinh doanh của doanh nghiệp không.

Lý thuyết về các hệ hỗ trợ quyết định (Decision Support System) thì có lẽ đủ để viết mấy quyển sách dày hàng trăm trang. Tôi còn nhớ hồi đi học ở khoa Công nghệ đã từng được học một môn như vây, nhưng chỉ dừng ở mức lý thuyết. Đến khi đi làm về data warehouse, mới dần dần nắm bắt được thế nào là một DSS. Nói một cách nôm na trong phạm vi của data warehouse, người ta muốn dựa vào thông tin để từ đó thấy được cần phải làm những gì để kinh doanh đạt kết quả tốt nhất.

Công cụ gần nhất và dễ dùng nhất là dựa trên các báo cáo (report) và phân tích. Kinh nghiệm của tôi cho thấy người dùng thường tạo ra các trend report để thể hiện _xu hướng _hoạt động thay đổi như thế nào theo thời gian. Đây là một chỉ số quan trọng và thông dụng trong nhiều tổ chức. Các KPI (Key Performance Indicators) có lẽ được xây dựng dựa trên thực tế này. Một kiểu report nữa hay gặp là dashboard, trong đó thực ra là chứa rất nhiều reports liên quan với nhau được thể hiện dưới dạng các biểu đồ (chart). Lợi thế của dashboard là nó rất trực quan, nhìn vào đó người ta có thể ngay lập tức hình dung được tình hình hoạt động của công ty.

Với data warehouse, người dùng có thể dễ dàng xây dựng các report như trên. Đồng thời, từ data warehouse, người ta có thể xây dựng các cube mà không tốn quá nhiều công sức. Dựa trên cube, các công cụ phân tích sẽ được dùng để phân tích dữ liệu cực kỳ nhanh chóng và trực quan.

**Thành công:**
Hiển nhiên sản phẩm được tạo ra cũng phải hướng đến thành công. Trong trường hợp của data warehouse, nó phải đem lại giá trị thực tế cho người dùng như đã nói ở trên và phải được dùng liên tục thì mới được coi là thành công. Việc có hay không có Data Warehouse trong một tổ chức hoàn toàn không mang tính bắt buộc. Không có data warehouse, người ta vẫn có thể tạo ra report nhưng dĩ nhiên mất nhiều công sức hơn. Để được công nhận, giá trị business mà data warehoue đem lại phải lớn hơn công sức và tiền của bỏ ra đầu tư vào nó.

Trong nhiều tổ chức, business user ban đầu thường không hề có chút ý niệm về data warehouse hoặc thậm chí hoài nghi về nó. Nhưng một khi người dùng đã quen với nó, người ta sẽ thích nó và muốn ngày càng có nhiều dữ liệu hơn trong data warehouse đơn giản bởi vì nó cung cấp rất nhiều lựa chọn và hỗ trợ ra quyết định khá tốt. Đó gọi là thành công.

Nguồn: www.fotech.org
