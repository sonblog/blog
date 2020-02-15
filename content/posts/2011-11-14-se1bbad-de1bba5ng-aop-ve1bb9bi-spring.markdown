---
author: admin
comments: true
date: 2011-11-14 03:25:04+00:00
layout: post
link: https://quachson.com/s%e1%bb%ad-d%e1%bb%a5ng-aop-v%e1%bb%9bi-spring/
slug: s%e1%bb%ad-d%e1%bb%a5ng-aop-v%e1%bb%9bi-spring
title: Sử dụng AOP với Spring
wordpress_id: 664
categories:
- Java
tags:
- AOP
- Java
---

#### I. AOP là cái gì?


-Ai chẳng biết AOP là từ viết tắt của Aspect Oriented Programming, dịch ra tiếng Việt thì bảo rằng AOP là “phương pháp lập trình hướng khía cạnh”. AOP hồi năm 2008 đã có một số trường Đại Học dạy rồi mà sao mình không được học. Lúc đó thì OOP còn chưa lĩnh hội hết chứ đừng nói AOP, bởi vậy xem xong cũng chẳng hiểu chi cả. ![:bbpcuoi3:](http://igame.vn/f/images/smilies/BBP_smilies/17.gif)Đến bây giờ khi đã hiểu được những khái niệm cơ bản, tôi thích gọi AOP là “A Ô Pê” hơn, khỏi dịch ra chi cho lôi thôi. Trong bài viết này, tôi sẽ giới thiệu về AOP và cách sử dụng AOP với Spring.

- Trong khi xây dựng các chương trình ứng dụng, chúng ta sẽ có rất nhiều những vấn đề liên quan đến phần mềm mà ta phải quan tâm. Tôi xin lấy ví dụ sau đây: tôi phải viết một chương trình để upload files, folders lên một server. Vấn đề khá đơn giản phải không? Nếu object được chọn là file thì chỉ việc upload cái file đó lên. Còn nếu object được chọn là một folder thì upload hết các file con bên trong folder đó, sau đó lại duyệt các folder con của nó và gọi hàm đệ quy. Hê hê, nhưng công việc không chỉ có vậy, tôi được yêu cầu phải thêm nhiều cái linh tinh khác như phải kiểm tra xem 1 folder, 1 file có tồn tại chưa, phải kiểm tra xem user hiện tại có đủ quyền hay không, phải ghi mọi thao tác ghi xóa hay thông báo lỗi xuống file log, phải hiển thị process bar, phải thế này, phải thế kia. Kết quả là hàm upload của tui trở thành một đống bùi nhùi, phần code phục vụ cho việc đọc, ghi file chỉ có vài dòng trong khi những code cho các việc kiểm tra, thông báo lỗi, hiển thị process bar chiếm rất nhiều nội dung của một hàm. Ngoài ra code của tôi bị phụ thuộc lẫn nhau ở nhiều nơi, chẳng hạn như những xử lý đọc ghi file do cần phải update process trên process bar rất khó maintain và rất là rối.

- Trong chương trình này, vấn đề quan tâm chính của tôi là upload folder/files và bên cạnh đó sẽ có một số vấn đề khác cần phải thực hiện. Các bạn có thể thấy rằng trong khi viết phần mềm, ta thường gặp hai loại “concern”: core concerns và cross-cutting concerns:

+ Core concern: là requirement chính của chương trình, ví dụ như upload file/folder, đọc danh sách user, …

+ Cross-cutting concerrns: là những xử lý phụ cần được thực hiện khi “core concern” được gọi. Cross-cuttong concerns thường xảy ra nhiều nơi trong chương trình, nó có thể xảy ra trong nhiều layer của ứng dụng, nhiều class, nhiều method; chẳng hạn như tính toán thời gian chạy các hàm đọc ghi database, ghi log lại mỗi lần cập nhật thông tin user, …

- Đã từ lâu, người ta đã nghĩ ra chiêu thức AOP để giải quyết vấn đề trên. Aspect-Oriented Programming(AOP) còn được gọi là Aspect-Oriented Software Development (AOSD) là một nguyên tắc thiết kế giúp tách rời các yêu cầu hay các vấn đề được quan tâm (separation of concerns) trong chương trình thành các thành phần độc lập và từ đó tăng tính uyển chuyển cho chương trình. “Separation of concerns” là một trong những kĩ thuật được quan tâm nhất trong ngành phần mềm. Người ta cho rằng những vấn đề tương tự nhau nên được giải quyết trong một “unit of code”. Khi lập trình thủ tục, một “unit of code” là 1 function, 1 method. Còn trong lập trình hướng đối tượng thì “unit of code” là một class.![:bbpraroi:](http://igame.vn/f/images/smilies/BBP_smilies/50.gif)


#### II. Những lợi ích của “separate of concerns”


- Trong AOP, từ “Aspect” chính là vấn đề [concern] người lập trình quan tâm và nó xuất hiện trong rất nhiều class cũng như nhiều method khác nhau. Kĩ thuật AOP thường được sử dụng để giải quyết các vấn đề như caching, tracking, security hay failure injections. Vì thế, nhiều tài liệu nói rằng AOP giúp module hóa ứng dụng, biến chương trình thành các module hoạt động độc lập, mỗi module làm một chức năng riêng, từ đó dễ bảo trì và nâng cấp.

- Ở vai trò của người thiết kế phần mềm, chúng ta nên đưa ra các cách làm đơn giản nhất. Để thỏa mãn yêu cầu của chương trình, người ta sẽ tạo ra thành phần chính của chương trình (gồm các class/component/method); các chức năng bổ sung như loging, tính toán performance, .. cũng sẽ được xem xét để tạo ra. Vì do các chứng năng bổ xung này không phải là yêu cầu chính của hệ thống nên người ta sẽ có yêu cầu bật tắt chúng theo ý muốn. Vậy làm thế nào để có thể tạo ra chương trình có thể linh hoạt được như thế? Câu trả lời là “Separate of concerns”

- Ở vai trò của người lập trình, chúng ta có hai vấn đề cần quan tâm là xử lý logic chính của chương trình và các xử lý logic cho những thành phần phụ. Do đó tất nhiên sẽ phải tạo ra các class/method cho các yêu cầu thực sự, và tạo ra những class/method khác độc lập để thực hiện các yêu cầu phụ kia. Tất cả các class/method này có thể được kết hợp lúc runtime theo ý muốn. Chẳng hạn như trong môi trường test, người ta có thể bật chức năng log, đo đạc performance để theo dõi nhưng khi cài đặt trên môi trường Production, các chức năng phụ này có thể được disable. Và trên nguyên tắc, trong code của những xử lý logic chính sẽ không có code để thực hiện các yêu cầu phụ.

**- Tóm lại, ta có thể liệt kê một số lợi ích như sau:**
+ Chức năng chính của chương trình không cần biết đến các chức năng phụ khác
+ Các chức năng phụ có thể được thêm thắt, bật tắt lúc runtime tùy theo yêu cầu
+ Các thay đổi, sửa lỗi, nâng cấp nếu có đối với các chức năng phụ sẽ không ảnh hưởng đến chương trình chính.
+ Hệ thống sẽ uyển chuyển và giảm thiểu tính phụ thuộc lẫn nhau của các module


#### III. Các thuật ngữ thường gặp trong AOP


+ Join point: Một điểm trong chương trình. Ví dụ như ta cần ghi log lại sau khi chạy method thì điểm ngay sau method đó được thực thi gọi là một jointpoint để có thể chạy những xử lý ghi file log. Join point theo nghĩa của nó có thể hiểu là những nơi có thể được chèn những “custom action” của bạn.

+ Pointcut: Có nhiều cách để xác định joinpoint, những cách như thế được gọi là pointcut.

+ Advice: là những xử lý phụ được thêm vào xử lý chính. Code để thực hiện các xử lý đó được gọi là Advice. Vì các xử lý phụ có thể thêm vào trước hoặc sau hoặc cả hai đối với những xử lý chính nên có nhiều loại Advice khác nhau mà ta sẽ đề cập trong những phần sau.

+ Aspect: thường dùng ở dạng annotation (`@Aspect`J), thay vì tạo class implement MethodBeforeAdvice thì ta dùng **@Before** trên method. Xem thêm chi tiết và ví dụ ở bài sau.


### IV. AOP trong Spring




#### 1. Sử dụng Advice


Xin nhắc lại điều này: tôi gọi Advice là những “custom action” mà bạn thêm vào chương trình của mình. Cụ thể hơn nữa, Advice là code bạn viết để xử lý những “custom action” đó, và tất nhiên theo nguyên tắc của AOP thì những code này không hề phụ thuộc vào chương trình chính. Có thể tạo ra những class, thậm chí là những project riêng biệt để xử lý các “custom action” sau đó add vào project chính. Tất nhiên các class Advice sử dụng AOP của Spring phải được viết theo quy tắc của Spring AOP Framework, nó sẽ phải implement interface MethodInterceptor  (Có nhiều interface tương tự ứng với các loại Advice khác nhau như là MethodBeforeAdvice, AfterReturningAdvice,  MethodInterceptor, ThrowsAdvice ). Và cuối cùng, các Advice mà bạn viết sẽ được gắn vào nơi cần thiết dựa vào xml config của Spring.

- Chúng ta hãy xem một ví dụ đơn giản để thấy Advice hoạt động như thế nào. Code sample dưới đây sẽ thêm chức năng print vài messages ra console trước và sau khi method chính được gọi. Do Advice được hiểu như một “custom action” cho một method nào đó (các bạn chú ý đối tượng được thêm “custom action” thường là các method, và chúng được hiểu là các “target of the advice”), nên trong các tài liệu ta sẽ thấy ghi là “advised method”. Như vậy “advised method” sẽ là method chính, còn các “Advice” chứa các xử lý được thêm vào “advised method”. Cũng phải thừa nhận rằng sample dưới đây không thể hiện hết tất cả khả năng của AOP, nhưng nó sẽ giúp bạn hiểu rõ về khái niệm Advice trong AOP. Và khi đã nắm được rồi, bạn sẽ có thể apply những Advice của chính bạn viết cho những chương trình của bạn.

[code]

package com.sample.customer.services;

public interface Service {
     public void execute();
}

[/code]



[code]
package com.example.aop;

import java.lang.reflect.Method;
import org.springframework.aop.MethodBeforeAdvice;

public class HijackBeforeMethod implements MethodBeforeAdvice {

     public void before(Method method, Object[] args, Object target)    throws Throwable {
           System.out.println("HijackBeforeMethod : Before method hijacked!");
     }
}
[/code]

Spring-Customer.xml

[code]
<beans xmlns="http://www.springframework.org/schema/beans"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.springframework.org/schema/beans
http://www.springframework.org/schema/beans/spring-beans-2.5.xsd">

<bean id="customerService"  class="com.sample.customer.services.CustomerService">
<property name="name" value="Quach Truong Son" />
<property name="url" value="http://www.vienthonga.com" />
</bean>

<bean id="hijackBeforeMethod" class="com.mkyong.aop.HijackBeforeMethod"/>

<bean id="customerServiceProxy" class="org.springframework.aop.framework.ProxyFactoryBean">

<property name="target" ref="customerService" />
<property name="interceptorNames">
<list>
<value>hijackBeforeMethod</value>
</list>
</property>

</bean>
</beans>
[/code]



[code]
package com.sample.common;

import org.springframework.context.ApplicationContext;
import org.springframework.context.support.ClassPathXmlApplicationContext;

import com.sample.customer.services.Service;

public class App {
public static void main(String[] args) {
ApplicationContext appContext = new ClassPathXmlApplicationContext(    new String[] { "Spring-Customer.xml" });

Service cust = (Service) appContext.getBean("customerServiceProxy");
cust.execute();
}
}
[/code]


**Chú ý
**Để sử dụng Spring proxy, bạn cần thêm thư viện CGLIB2.
[code]
	<dependency>
		<groupId>cglib</groupId>
		<artifactId>cglib</artifactId>
		<version>2.2.2</version>
	</dependency>
[/code]

Kết quả là HijackBeforeMethod : Before method hijacked! sẽ được thêm vào trước khi hàm execute() được gọi.

[code]
 HijackBeforeMethod : Before method hijacked!
 Customer name : Quach Truong Son
 Customer website : http://www.vienthonga.com

[/code]




Bài viết có tham khảo từ blog của nthoai.
