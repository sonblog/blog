---
author: quachson
comments: true
date: 2016-01-04 06:41:19+00:00
layout: post
link: https://quachson.com/30-regex-codes-ma-lap-trinh-vien-web-nen-biet/
slug: 30-regex-codes-ma-lap-trinh-vien-web-nen-biet
title: 30 regex codes mà lập trình viên web nên biết
wordpress_id: 930
categories:
- Uncategorised
tags:
- developer
- regex
---

**Biểu thức chính quy** (hay regex) là một công cụ mạnh mẽ mà mỗi nhà phát triển nên biết. Nó có thể khớp với một chuỗi các ký tự dựa trên các thông số rất phức tạp mà có thể giúp bạn tiết kiệm rất nhiều thời gian khi xây dựng các trang web động.

Dù các nhà phát triển Web phải đối mặt với nhiều nhiệm vụ khác nhau hơn so với các nhà phát triển phần mềm, nhưng đa số trong đó vẫn có cùng mã nền tảng. Biểu thức chính quy hơi khó học lúc đầu, nhưng có thể rất mạnh mẽ khi được sử dụng một cách chính xác.

Phần khó khăn nhất là việc tìm hiểu cú pháp và học cách để viết mã regex của riêng bạn từ đầu. Để tiết kiệm thời gian, tôi đã chọn ra 30 đoạn mã regex khác nhau mà bạn có thể sử dụng trong các dự án của bạn. Và kể từ khi regex không giới hạn cho một ngôn ngữ cụ thể, bạn có thể áp dụng những đoạn dưới đây vào bất cứ ngôn ngữ nào từ Javascript đến PHP hoặc Python.


### 1. [Độ mạnh của mật khẩu](http://stackoverflow.com/a/5142164/477958)



    
    <code class="ui segment hljs bash">^(?=.*[A-Z].*[A-Z])(?=.*[!@<span class="hljs-comment">#$&*])(?=.*[0-9].*[0-9])(?=.*[a-z].*[a-z].*[a-z]).{8}$</span>
    </code>


Kiểm tra độ mạnh của một mật khẩu thường là chủ quan nên không có câu trả lời chính xác tuyệt đối. Nhưng tôi cảm thấy đoạn regex này là một điểm khởi đầu tuyệt vời nếu bạn không muốn phải viết riêng hàm kiểm tra độ mạnh mật khẩu của bạn từ đầu.


### 2. [Mã màu Hex](http://snipplr.com/view/65915/hexadecimal-color-regex-match/)



    
    <code class="ui segment hljs bash">\<span class="hljs-comment">#([a-fA-F]|[0-9]){3, 6}</span>
    </code>


Mã màu hex rất phố biến trong lĩnh vực phát triển web. Đoạn regex này có thể được sử dụng để lấy mã hex phù hợp từ chuỗi bất kỳ cho bất cứ mục đích nào.


### 3. [Xác thực địa chỉ Email](http://www.sitepoint.com/javascript-validate-email-address-regex/)



    
    <code class="ui segment hljs erlang">/[<span class="hljs-variable">A</span>-<span class="hljs-variable">Z0</span>-<span class="hljs-number">9</span>.<span class="hljs-variable">_</span><span class="hljs-comment">%+-]+@[A-Z0-9-]+.+.[A-Z]{2,4}/igm</span>
    </code>


Một trong những nhiệm vụ phổ biến nhất đối với một nhà phát triển là kiểm tra một chuỗi có phải là một địa chỉ Email hay không. Đối với PHP, các bạn có thể sử dụng hàm filter_var: `filter_var($email, FILTER_VALIDATE_EMAIL)`


### 4. [Địa chỉ IPv4](http://snipplr.com/view/43002/regex--match-ipv4-address/)



    
    <code class="ui segment hljs markdown">/\b(?:(?:25[<span class="hljs-link_label">0-5</span>]|2[<span class="hljs-link_label">0-4</span>][<span class="hljs-link_reference">0-9</span>]|[<span class="hljs-link_label">01</span>]?[<span class="hljs-link_label">0-9</span>][<span class="hljs-link_reference">0-9</span>]?)\.){3}(?:25[<span class="hljs-link_label">0-5</span>]|2[<span class="hljs-link_label">0-4</span>][<span class="hljs-link_reference">0-9</span>]|[<span class="hljs-link_label">01</span>]?[<span class="hljs-link_label">0-9</span>][<span class="hljs-link_reference">0-9</span>]?)\b/
    </code>


Tương tự như một địa chỉ email là địa chỉ IP - được sử dụng để xác định một máy tính cụ thể truy cập Internet. Biểu thức chính quy này sẽ kiểm tra một chuỗi xem nó có tuân theo cú pháp địa chỉ IPv4 hay không.


### 5. [Địa chỉ IPv6](http://stackoverflow.com/a/17871737/477958)



    
    <code class="ui segment hljs lisp"><span class="hljs-list">(<span class="hljs-list">([<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>}:)</span>{<span class="hljs-number">7</span>,<span class="hljs-number">7</span>}[<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>}|<span class="hljs-list">([<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>}:)</span>{<span class="hljs-number">1</span>,<span class="hljs-number">7</span>}:|<span class="hljs-list">([<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>}:)</span>{<span class="hljs-number">1</span>,<span class="hljs-number">6</span>}:[<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>}|<span class="hljs-list">([<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>}:)</span>{<span class="hljs-number">1</span>,<span class="hljs-number">5</span>}<span class="hljs-list">(:[<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>})</span>{<span class="hljs-number">1</span>,<span class="hljs-number">2</span>}|<span class="hljs-list">([<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>}:)</span>{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>}<span class="hljs-list">(:[<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>})</span>{<span class="hljs-number">1</span>,<span class="hljs-number">3</span>}|<span class="hljs-list">([<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>}:)</span>{<span class="hljs-number">1</span>,<span class="hljs-number">3</span>}<span class="hljs-list">(:[<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>})</span>{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>}|<span class="hljs-list">([<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>}:)</span>{<span class="hljs-number">1</span>,<span class="hljs-number">2</span>}<span class="hljs-list">(:[<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>})</span>{<span class="hljs-number">1</span>,<span class="hljs-number">5</span>}|[<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>}:<span class="hljs-list">(<span class="hljs-list">(:[<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>})</span>{<span class="hljs-number">1</span>,<span class="hljs-number">6</span>})</span>|:<span class="hljs-list">(<span class="hljs-list">(:[<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>})</span>{<span class="hljs-number">1</span>,<span class="hljs-number">7</span>}|:)</span>|fe<span class="hljs-number">80</span>:<span class="hljs-list">(:[<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">0</span>,<span class="hljs-number">4</span>})</span>{<span class="hljs-number">0</span>,<span class="hljs-number">4</span>}%[<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-zA-Z]{<span class="hljs-number">1</span>,}|::<span class="hljs-list">(<span class="hljs-keyword">ffff</span><span class="hljs-list">(:<span class="hljs-number">0</span>{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>})</span>{<span class="hljs-number">0</span>,<span class="hljs-number">1</span>}:)</span>{<span class="hljs-number">0</span>,<span class="hljs-number">1</span>}<span class="hljs-list">(<span class="hljs-list">(<span class="hljs-number">25</span>[<span class="hljs-number">0</span><span class="hljs-number">-5</span>]|<span class="hljs-list">(<span class="hljs-number">2</span>[<span class="hljs-number">0</span><span class="hljs-number">-4</span>]|<span class="hljs-number">1</span>{<span class="hljs-number">0</span>,<span class="hljs-number">1</span>}[<span class="hljs-number">0</span><span class="hljs-number">-9</span>])</span>{<span class="hljs-number">0</span>,<span class="hljs-number">1</span>}[<span class="hljs-number">0</span><span class="hljs-number">-9</span>])</span>\.)</span>{<span class="hljs-number">3</span>,<span class="hljs-number">3</span>}<span class="hljs-list">(<span class="hljs-number">25</span>[<span class="hljs-number">0</span><span class="hljs-number">-5</span>]|<span class="hljs-list">(<span class="hljs-number">2</span>[<span class="hljs-number">0</span><span class="hljs-number">-4</span>]|<span class="hljs-number">1</span>{<span class="hljs-number">0</span>,<span class="hljs-number">1</span>}[<span class="hljs-number">0</span><span class="hljs-number">-9</span>])</span>{<span class="hljs-number">0</span>,<span class="hljs-number">1</span>}[<span class="hljs-number">0</span><span class="hljs-number">-9</span>])</span>|<span class="hljs-list">([<span class="hljs-number">0</span><span class="hljs-number">-9</span>a-fA-F]{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>}:)</span>{<span class="hljs-number">1</span>,<span class="hljs-number">4</span>}:<span class="hljs-list">(<span class="hljs-list">(<span class="hljs-number">25</span>[<span class="hljs-number">0</span><span class="hljs-number">-5</span>]|<span class="hljs-list">(<span class="hljs-number">2</span>[<span class="hljs-number">0</span><span class="hljs-number">-4</span>]|<span class="hljs-number">1</span>{<span class="hljs-number">0</span>,<span class="hljs-number">1</span>}[<span class="hljs-number">0</span><span class="hljs-number">-9</span>])</span>{<span class="hljs-number">0</span>,<span class="hljs-number">1</span>}[<span class="hljs-number">0</span><span class="hljs-number">-9</span>])</span>\.)</span>{<span class="hljs-number">3</span>,<span class="hljs-number">3</span>}<span class="hljs-list">(<span class="hljs-number">25</span>[<span class="hljs-number">0</span><span class="hljs-number">-5</span>]|<span class="hljs-list">(<span class="hljs-number">2</span>[<span class="hljs-number">0</span><span class="hljs-number">-4</span>]|<span class="hljs-number">1</span>{<span class="hljs-number">0</span>,<span class="hljs-number">1</span>}[<span class="hljs-number">0</span><span class="hljs-number">-9</span>])</span>{<span class="hljs-number">0</span>,<span class="hljs-number">1</span>}[<span class="hljs-number">0</span><span class="hljs-number">-9</span>])</span>)</span>
    </code>


Hoặc có thể bạn sẽ muốn kiểm tra một địa chỉ theo cú pháp IPv6 mới hơn với đoạn regex nâng cao hơn này. Sự khác biệt là rất nhỏ mặc dù nó quan trọng trong quá trình phát triển.


### 6. [Dấu phân cách hàng nghìn](http://snipplr.com/view/72657/thousand-separator/)



    
    <code class="ui segment hljs gradle"><span class="hljs-regexp">/\d{1,3}(?=(\d{3})+(?!\d))/g</span>
    </code>


Mã regex này hoạt động trên bất kỳ số nào và sẽ áp dụng bất cứ dấu phân cách nào bạn chọn cho mỗi chữ số thứ ba phân tách thành hàng ngàn, hàng triệu,...


### 7. [Thêm HTTP vào trước liên kết](http://stackoverflow.com/a/3543207/477958)



    
    <code class="javascript ui segment hljs "><span class="hljs-keyword">if</span> (!s.match(<span class="hljs-regexp">/^[a-zA-Z]+:\/\//</span>))
    {
        s = <span class="hljs-string">'http://'</span> + s;
    }
    </code>


Cho dù bạn đang làm việc trong JavaScript, Ruby hay PHP, biểu thức này có thể tỏ ra rất hữu ích. Nó sẽ kiểm tra bất kỳ chuỗi URL nào để xem nếu nó có tiền tố HTTP/HTTPS hay không, và nếu không, thêm vào trước chuỗi đó cho phù hợp.


### 8. [Lấy tên miền từ URL](http://snipplr.com/view/67095/domain-regex/)



    
    <code class="ui segment hljs groovy"><span class="hljs-regexp">/https?:\/\/</span>(?:[-\w]+\.)?([-\w]+)\.\w+(?:\.\w+)?\/?.*/i
    </code>


Mỗi tên miền trang web đều chứa giao thức ở đầu (HTTP hoặc HTTPS) và đôi khi có tên miền phụ với đường dẫn trang bổ sung. Bạn có thể sử dụng đoạn regex này để cắt qua tất cả những điều đó và chỉ trả lại tên miền.


### 9. [Sắp xếp các từ khóa bằng cách đếm số từ](http://snipplr.com/view/53358/segment-keywords-by-number-of-words-in-ga/)



    
    <code class="ui segment hljs css">^<span class="hljs-attr_selector">[^\s]</span>*$        <span class="hljs-tag">matches</span> <span class="hljs-tag">exactly</span> 1<span class="hljs-tag">-word</span> <span class="hljs-tag">keyword</span>
    ^<span class="hljs-attr_selector">[^\s]</span>*\<span class="hljs-tag">s</span><span class="hljs-attr_selector">[^\s]</span>*$    <span class="hljs-tag">matches</span> <span class="hljs-tag">exactly</span> 2<span class="hljs-tag">-word</span> <span class="hljs-tag">keyword</span>
    ^<span class="hljs-attr_selector">[^\s]</span>*\<span class="hljs-tag">s</span><span class="hljs-attr_selector">[^\s]</span>*     <span class="hljs-tag">matches</span> <span class="hljs-tag">keywords</span> <span class="hljs-tag">of</span> <span class="hljs-tag">at</span> <span class="hljs-tag">least</span> 2 <span class="hljs-tag">words</span> (2 <span class="hljs-tag">and</span> <span class="hljs-tag">more</span>)
    ^(<span class="hljs-attr_selector">[^\s]</span>*\<span class="hljs-tag">s</span>)<span class="hljs-rules">{<span class="hljs-rule">2}</span></span><span class="hljs-attr_selector">[^\s]</span>*$    <span class="hljs-tag">matches</span> <span class="hljs-tag">exactly</span> 3<span class="hljs-tag">-word</span> <span class="hljs-tag">keyword</span>
    ^(<span class="hljs-attr_selector">[^\s]</span>*\<span class="hljs-tag">s</span>)<span class="hljs-rules">{<span class="hljs-rule">4}</span></span><span class="hljs-attr_selector">[^\s]</span>*$    <span class="hljs-tag">matches</span> 5<span class="hljs-tag">-words-and-more</span> <span class="hljs-tag">keywords</span> (<span class="hljs-tag">longtail</span>)
    </code>


Những ai dùng Google Analytics và Webmaster Tools sẽ thực sự thích biểu thức chính quy này. Nó có thể sắp xếp các từ khoá dựa trên số các từ được sử dụng trong một tìm kiếm.

Đây có thể là số lượng cụ thể (tức là chỉ có 5 từ) hoặc nó có thể phù hợp với một loạt các từ (tức là 2 hoặc nhiều hơn). Khi được sử dụng để sắp xếp và phân tích dữ liệu, nó là một trong những biểu thức chính quy mạnh mẽ.


### 10. [Tìm một chuỗi Base64 hợp lệ trong PHP](http://snipplr.com/view/57477/find-valid-base64-string-in-php-files/)



    
    <code class="ui segment hljs bash">\?php[ \t]<span class="hljs-built_in">eval</span>\(base64_decode\(\<span class="hljs-string">'(([A-Za-z0-9+/]{4})*([A-Za-z0-9+/]{3}=|[A-Za-z0-9+/]{2}==)?){1}\'</span>\)\)\;
    </code>


Nếu bạn là một nhà phát triển PHP thì đôi khi bạn có thể cần phân tích qua code để tìm kiếm các đối tượng nhị phân đã mã hóa Base64 (ví dụ như tìm shell được giấu trong một tập tin PHP chẳng hạn). Đoạn regex này có thể áp dụng với tất cả code PHP và sẽ kiểm tra bất cứ chuỗi Base64 nào đang tồn tại.


### 11. [Xác thực số điện thoại](http://snipplr.com/view/24284/valid-phone-number/)



    
    <code class="ui segment hljs css">^\+?\<span class="hljs-tag">d</span><span class="hljs-rules">{<span class="hljs-rule">1,3}</span></span>?<span class="hljs-attr_selector">[- .]</span>?\(?(?:\<span class="hljs-tag">d</span><span class="hljs-rules">{<span class="hljs-rule">2,3}</span></span>)\)?<span class="hljs-attr_selector">[- .]</span>?\<span class="hljs-tag">d</span>\<span class="hljs-tag">d</span>\<span class="hljs-tag">d</span><span class="hljs-attr_selector">[- .]</span>?\<span class="hljs-tag">d</span>\<span class="hljs-tag">d</span>\<span class="hljs-tag">d</span>\<span class="hljs-tag">d</span>$
    </code>


Ngắn gọn, ngọt ngào và đi thẳng vào vấn đề. Đoạn regex này sẽ xác thực bất cứ cú pháp số điện thoại nào dựa trên phong cách số điện thoại Mỹ.

Điều này có thể biến thành một chủ đề khá phức tạp, tôi khuyên bạn nên đọc lướt qua [chủ đề stack này](http://stackoverflow.com/questions/123559/a-comprehensive-regex-for-phone-number-validation) cho câu trả lời chi tiết hơn.


### 12. [Khoảng trắng ở đầu và cuối](http://snipplr.com/view/70938/regex-leading-and-trailing-whitespace/)



    
    <code class="ui segment hljs ruby">^[ \s]+|[ \s]+<span class="hljs-variable">$
    </span></code>


Sử dụng đoạn mã này để lấy ra khoảng trắng ở đầu/cuối từ một chuỗi. Đây có thể không phải là một việc lớn, nhưng đôi khi nó ảnh hưởng đến đầu ra khi lấy kết quả ra từ một cơ sở dữ liệu hoặc áp dụng vào mã hóa tài liệu.


### 13. [Lấy nguồn ảnh](http://snipplr.com/view/12110/regular-expression-catch-img-src-attribute-in-html/)



    
    <code class="ui segment hljs markdown">\<span class="xml"><span class="hljs-tag">< *[<span class="hljs-attribute">img</span>][^\></span></span>]<span class="hljs-emphasis">*[src] *</span>= <span class="hljs-emphasis">*[\"\']{0,1}([^\"\'\ >]*</span>)
    </code>


Nếu vì một số lý do nào đó mà bạn cần lấy ra một nguồn ảnh trực tiếp từ HTML thì đoạn mã này là giải pháp hoàn hảo. Mặc dù nó có thể chạy trơn tru trên Backend, các nhà phát triển JS nên dựa vào phương thức[.attr()](http://api.jquery.com/attr/) của jQuery cho Frontend.


### 14. [Xác thực ngày trong định dạng DD/MM/YYYY](http://stackoverflow.com/a/15504877/477958)



    
    <code class="ui segment hljs markdown">^(?:(?:31(\/|-|\.)(?:0?[<span class="hljs-link_label">13578</span>]|1[<span class="hljs-link_label">02</span>]))\1|(?:(?:29|30)(\/|-|\.)(?:0?[<span class="hljs-link_label">1,3-9</span>]|1[<span class="hljs-link_label">0-2</span>])\2))(?:(?:1[<span class="hljs-link_label">6-9</span>]|[<span class="hljs-link_label">2-9</span>]\d)?\d{2})$|^(?:29(\/|-|\.)0?2\3(?:(?:(?:1[<span class="hljs-link_label">6-9</span>]|[<span class="hljs-link_label">2-9</span>]\d)?(?:0[<span class="hljs-link_label">48</span>]|[<span class="hljs-link_label">2468</span>][<span class="hljs-link_reference">048</span>]|[<span class="hljs-link_label">13579</span>][<span class="hljs-link_reference">26</span>])|(?:(?:16|[<span class="hljs-link_label">2468</span>][<span class="hljs-link_reference">048</span>]|[<span class="hljs-link_label">3579</span>][<span class="hljs-link_reference">26</span>])00))))$|^(?:0?[1-9]|1\d|2[0-8])(\/|-|\.)(?:(?:0?[1-9])|(?:1[0-2]))\4(?:(?:1[6-9]|[2-9]\d)?\d{2})$
    </code>


Các ngày khó khăn vì chúng có thể xuất hiện dưới dạng văn bản + số, hoặc chỉ là số với các định dạng khác nhau. PHP có một hàm ngày tuyệt vời nhưng điều này không phải luôn là lựa chọn tốt nhất khi lấy ra từ một chuỗi thô (raw). Cân nhắc việc thay thế bằng cách sử dụng biểu thức chính quy này cho các cú pháp ngày cụ thể.


### 15. [Khớp ID Video Youtube](http://snipplr.com/view/33375/youtube-url-matcher-video-id-catcher/)



    
    <code class="ui segment hljs groovy"><span class="hljs-regexp">/https?:\/\/</span>(?:youtu\.be\<span class="hljs-regexp">/|(?:[a-z]{2,3}\.)?youtube\.com\/</span>watch(?:\?|#\!)v=)([\w-]{11}).*/gi
    </code>


Youtube đã giữ cấu trúc URL giống nhau trong nhiều năm chỉ bởi nó hoạt động. Đây cũng là trang chia sẻ video phổ biến nhất trên web, vì thế các video Youtube có xu hướng điều phối lưu lượng truy cập nhiều nhất.

Nếu bạn cần lấy ra một ID video Youtube từ một URL thì đoạn regex này là hoàn hảo và hoạt động tốt với tất cả các biến thể của cấu trúc URL Youtube.


### 16. [Xác thực ISBN](http://stackoverflow.com/a/14096142/477958)



    
    <code class="ui segment hljs ruby">/\b(?:<span class="hljs-constant">ISBN</span>(?<span class="hljs-symbol">:</span><span class="hljs-symbol">:</span> ?| ))?((?:<span class="hljs-number">97</span>[<span class="hljs-number">89</span>])<span class="hljs-string">?\d</span>{<span class="hljs-number">9</span>}[\dx])\b/i
    </code>


Sách được in theo một hệ thống số gọi là ISBN. Điều này có thể lấy khá khó khăn khi bạn xem xét sự khác biệt giữa ISBN-10 và ISBN-13.

Tuy nhiên đoạn regex đáng kinh ngạc này cho phép bạn để xác nhận một số ISBN và kiểm tra xem nó là ISBN10 hay 13. Tất cả các mã được viết bằng PHP vì vậy điều này có thể tỏ ra đặc biệt hữu ích cho các nhà phát triển web.


### 17. [Kiểm tra mã bưu điện](http://stackoverflow.com/a/2577239/477958)



    
    <code class="ui segment hljs css">^\<span class="hljs-tag">d</span><span class="hljs-rules">{<span class="hljs-rule">5}</span></span>(?:<span class="hljs-attr_selector">[-\s]</span>\<span class="hljs-tag">d</span><span class="hljs-rules">{<span class="hljs-rule">4}</span></span>)?$
    </code>


Tác giả của đoạn regex này không chỉ chia sẻ nó miễn phí mà còn dành thời gian để giải thích nó. Bạn sẽ thấy nó hữu ích cho dù bạn đang khớp một mã bưu điện loại 5 chữ số hay phiên bản dài 9 chữ số dài hơn.

Hãy nhớ rằng nó chủ yếu dành cho hệ thống mã bưu điện của Mỹ nên có thể bạn sẽ cần điều chỉnh cho các quốc gia khác.


### 18. [Tên người dùng Twitter hợp lệ](http://stackoverflow.com/a/4424288/477958)



    
    <code class="ui segment hljs python">/<span class="hljs-decorator">@([A-Za-z0-9_]{1,15})/</span>
    </code>


Đây là một đoạn mã regex rất nhỏ để khớp tên người dùng Twitter tìm thấy trong một chuỗi. Nó kiểm tra dựa trên cú pháp đề cập ([@mention](http://kipalog.com/users/mention/mypage)).


### 19. [Số thẻ tín dụng](http://stackoverflow.com/a/9315696/477958)



    
    <code class="ui segment hljs markdown">^(?:4[<span class="hljs-link_label">0-9</span>]{12}(?:[<span class="hljs-link_label">0-9</span>]{3})?|5[<span class="hljs-link_label">1-5</span>][<span class="hljs-link_reference">0-9</span>]{14}|6(?:011|5[<span class="hljs-link_label">0-9</span>][<span class="hljs-link_reference">0-9</span>])[<span class="hljs-link_label">0-9</span>]{12}|3[<span class="hljs-link_label">47</span>][<span class="hljs-link_reference">0-9</span>]{13}|3(?:0[<span class="hljs-link_label">0-5</span>]|[<span class="hljs-link_label">68</span>][<span class="hljs-link_reference">0-9</span>])[0-9]{11}|(?:2131|1800|35\d{3})\d{11})$
    </code>


Chứng thực số thẻ tín dụng thường bắt buộc một nền tảng máy chủ an toàn. Nhưng regex có thể được sử dụng cho các yêu cầu tối thiểu của một số thẻ tín dụng điển hình.


### 20. [Tìm thuộc tính CSS](http://snipplr.com/view/17903/find-css-attributes/)



    
    <code class="ui segment hljs css">^\<span class="hljs-tag">s</span>*<span class="hljs-attr_selector">[a-zA-Z\-]</span>+\<span class="hljs-tag">s</span>*<span class="hljs-attr_selector">[:]</span><span class="hljs-rules">{<span class="hljs-rule">1}</span></span>\<span class="hljs-tag">s</span><span class="hljs-attr_selector">[a-zA-Z0-9\s.#]</span>+<span class="hljs-attr_selector">[;]</span><span class="hljs-rules">{<span class="hljs-rule">1}</span></span>
    </code>


Có thể rất hiếm để chạy regex trên CSS nhưng nó không phải là một tình huống lạ.

Đoạn mã này có thể được sử dụng để lấy ra mọi thuộc tính và giá trị CSS khớp từ selector cụ thể. Nó có thể được sử dụng cho bất kỳ lý do nào, ví dụ như loại bỏ thuộc tính trùng lặp.


### 21. [Loại bỏ chú thích HTML](http://stackoverflow.com/a/1084759/477958)



    
    <code class="ui segment hljs xml"><span class="hljs-comment"><!--(.*?)--></span>
    </code>


Nếu vì bất cứ lý do nào mà bạn cần phải loại bỏ tất cả các chú thích từ một khối HTML thì đây là mã regex cần dùng. Bạn sẽ tìm thấy một ví dụ PHP sử dụng [preg_replace](http://php.net/manual/en/function.preg-replace.php).


### 22. [URL trang cá nhân Facebook](http://stackoverflow.com/a/11519661/477958)



    
    <code class="ui segment hljs groovy"><span class="hljs-regexp">/(?:http:\/\/</span>)?(?:www\.)?facebook\.com\/(?:(?:\w)*#!\<span class="hljs-regexp">/)?(?:pages\/</span>)?(?:[\w\-]*\<span class="hljs-regexp">/)*([\w\-]*)/</span>
    </code>


Facebook rất phổ biến và có nhiều sự sắp đặt URL khác nhau. Trong một tình huống mà bạn đang lấy URL hồ sơ từ người sử dụng thì đoạn regex này có thể hữu ích để phân tích chuỗi và xác nhận rằng chúng có cấu trúc đúng. Đoạn này có thể làm chính xác điều đó và nó hoàn hảo cho tất cả các kiểu liên kết FB.


### 23. [Kiểm tra phiên bản Internet Explorer](http://stackoverflow.com/a/29296626/477958)



    
    <code class="ui segment hljs ruby">^.*<span class="hljs-constant">MSIE</span> [<span class="hljs-number">5</span>-<span class="hljs-number">8</span>](?<span class="hljs-symbol">:</span>\.[<span class="hljs-number">0</span>-<span class="hljs-number">9</span>]+)?(?!.*<span class="hljs-constant">Trident</span>\/[<span class="hljs-number">5</span>-<span class="hljs-number">9</span>]\.<span class="hljs-number">0</span>).*<span class="hljs-variable">$
    </span></code>


Trình duyệt IE vẫn đang có thị phần người dùng lớn và các nhà phát triển thường phải kiểm tra phiên bản IE để xử lý tính tương thích của trang web.

Đoạn này có thể được sử dụng trong JavaScript để kiểm tra phiên bản của Internet Explorer (5-11) đang được sử dụng dựa trên chuỗi User-Agent.


### 24. [Bóc tách giá](http://stackoverflow.com/a/2430709/477958)



    
    <code class="ui segment hljs ruby">/(\<span class="hljs-variable">$[</span><span class="hljs-number">0</span>-<span class="hljs-number">9</span>,]+(\.[<span class="hljs-number">0</span>-<span class="hljs-number">9</span>]{<span class="hljs-number">2</span>})?)/
    </code>


Giá cả đi kèm trong một loạt các định dạng có chứa số thập phân, dấu phẩy và ký hiệu tiền tệ. Biểu thức này có thể kiểm tra tất cả các định dạng khác nhau để lấy ra một mức giá từ bất kỳ chuỗi nào.


### 25. [Phân tích tiêu đề Email](http://stackoverflow.com/a/3885902/477958)



    
    <code class="ui segment hljs erlang">/\b[<span class="hljs-variable">A</span>-<span class="hljs-variable">Z0</span>-<span class="hljs-number">9</span>.<span class="hljs-variable">_</span><span class="hljs-comment">%+-]+@(?:[A-Z0-9-]+\.)+[A-Z]{2,6}\b/i</span>
    </code>


Với một dòng code này bạn có thể phân tích thông qua một tiêu đề email để lấy ra thông tin "to" từ tiêu đề. Nó có thể được sử dụng song song với nhiều email liên kết với nhau.


### 26. [Khớp một loại tập tin cụ thể](http://stackoverflow.com/a/18086622/477958)



    
    <code class="ui segment hljs ruby">/^(.*\.(?!(htm|html|<span class="hljs-class"><span class="hljs-keyword">class</span>|<span class="hljs-title">js</span>)$))?[^.]*$/<span class="hljs-title">i</span></span>
    </code>


Khi bạn đang làm việc với các định dạng tập tin khác nhau như .xml, .html và .js, nó có thể giúp kiểm tra các tập tin cả nội bộ (local) và được tải lên bởi người dùng. Đoạn này lấy ra một phần mở rộng tập tin để kiểm tra xem nó có giá trị nằm trong một danh sách các phần mở rộng hợp lệ hay không.


### 27. [Khớp một chuỗi URL](http://stackoverflow.com/a/3809435/477958)



    
    <code class="ui segment hljs bash">/[<span class="hljs-operator">-a</span>-zA-Z0-<span class="hljs-number">9</span>@:%_\+.~<span class="hljs-comment">#?&//=]{2,256}\.[a-z]{2,4}\b(\/[-a-zA-Z0-9@:%_\+.~#?&//=]*)?/gi</span>
    </code>


Đoạn này có thể sử dụng cho cả chuỗi HTTP và HTTPS để kiểm tra xem nó có khớp với cú pháp tên miền mức cao nhất (TLD) hay không. Cũng có một phiên bản đơn giản hơn đoạn này sử dụng [RegExp](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp) của JavaScript.


### 28. [Thêm rel="nofollow" vào các liên kết](http://stackoverflow.com/a/3257169/477958)



    
    <code class="ui segment hljs bash">(<a\s*(?!.*\brel=)[^>]*)(href=<span class="hljs-string">"https?://)((?!(?:(?:www\.)?'.implode('|(?:www\.)?', <span class="hljs-variable">$follow_list</span>).'))[^"</span>]+)<span class="hljs-string">"((?!.*\brel=)[^>]*)(?:[^>]*)>
    </span></code>


Nếu bạn đang làm việc với hàng loạt mã HTML có thể nó thật khủng khiếp khi phải làm thủ công các nhiệm vụ lặp đi lặp lại. Biểu thức chính quy là hoàn hảo cho công việc này và họ sẽ tiết kiệm được rất nhiều thời gian.

Đoạn regex này có thể lấy ra tất cả liên kết từ một khối HTML và thêm thuộc tính rel="nofollow" vào mỗi phần tử.


### 29. [Khớp Media Query](https://regex101.com/r/tE4sT3/1)



    
    <code class="ui segment hljs ruby">/<span class="hljs-variable">@media</span>([^{]+)\{([\s\<span class="hljs-constant">S</span>]+?})\s*}/g
    </code>


Chia tách các Media Query CSS vào từng tham số và thuộc tính của chúng. Điều này có thể giúp bạn phân tích CSS bên ngoài với sự tập trung trực tiếp hơn vào cách mà code hoạt động.


### 30. [Cú pháp tìm kiếm Google](https://regex101.com/r/rR1fI0/1)



    
    <code class="ui segment hljs ruby">/([+-]?(?<span class="hljs-symbol">:<span class="hljs-string">'.+?'</span>|<span class="hljs-string">".+?"</span>|</span>[^+\- ]{<span class="hljs-number">1</span>}[^ ]*))/g
    </code>


Bạn có thể xây dựng mã regex của riêng bạn cho các thao tác tìm kiếm nội dung bằng cách sử dụng cú pháp độc quyền của Google. Các dấu cộng (+) biểu thị các từ khóa bổ sung và dấu trừ (-) biểu thị rằng nên bỏ qua và loại bỏ khỏi kết quả.

Đó là một đoạn khá phức tạp nhưng được sử dụng đúng cách thì nó có thể cung cấp một cơ sở cho việc xây dựng thuật toán tìm kiếm của riêng bạn.

_Dịch bởi [Juno_okyo](https://blog-j2team.rhcloud.com/30-doan-bieu-thuc-chinh-quy-huu-ich/) theo [Hongkiat.com](http://www.hongkiat.com/blog/regex-web-developers/)._
