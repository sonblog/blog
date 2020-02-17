---
author: admin
comments: true
date: 2011-09-17 06:14:41+00:00
template: "post"
link: https://quachson.com/gi%e1%bb%9bi-thi%e1%bb%87u-v%e1%bb%81-spring-framwork/
slug: gi%e1%bb%9bi-thi%e1%bb%87u-v%e1%bb%81-spring-framwork
title: Giới thiệu về Spring framwork
wordpress_id: 643
categories:
- Spring
tags:
- Spring
---

**1. Lịch sử của Spring:**

Spring được phát minh bởi Rod Johnson. Nó được giới thiệu lần đầu tiên trong cuốn Expert One-on-One J2EE Design and Development, vào năm 2002. Trong đó, Rod giải thích các kinh nghiệm làm việc với J2EE và làm thế nào EJB mang đến thành công cho các project. Rod tin rằng một framework lightweight như JavaBean thì phù hợp cho nhu cầu của developer.

Framework được mô tả đó được gọi Spring khi nó được đưa lên SourceForge vào tháng 2-2003. Vào lúc đó, Juergen Hoeller đã tham gia với Rod để cùng phát triển Spring, họ trở thành cánh tay phải của Spring. Sau đó họ cộng tác thêm một vài developer nữa. Gần đây, Rod và Juergen đã viết một cuốn sách có tên là:“Expert One-on-One J2EE Development without EJB” để mô tả Spring giải quyết nhiều vấn đề của J2EE như thế nào. Cơ sở kiến trúc của Spring được phát triển bởi Rod vào năm 2000 (trước Struts). Cơ sở này được xây dựng từ kinh nghiệm xây dựng cơ sở hạ tầng trong một số project của Rod. ** **

**2. Về Spring:**

**** Spring là một J2EE application framework được cung cấp để quản lý các đối tượng nghiệp vụ và sự phụ thuộc giữa chúng. Ví dụ, với IoC (Inversion of Control), nó cho phép bạn xác định DAO (Data Access Object) phụ thuộc vào DataSource. Nó cũng cho phép developer viết các giao tiếp và đơn giản định nghĩa cài đặt trong XML file. Spring chứa nhiều lớp hỗ trợ các framework khác (như Hibernate và Struts) để tạo sự tích hợp dễ dàng hơn. Áp dụng J2EE Design Pattern thì cồng kềnh và không cần thiết ở một số trường hợp. Spring thì giống design pattern nhưng mọi thứ thì đơn giản hơn. Ví dụ: thay vì viết ServerLocator để tìm Hibernate Session, bạn có thể cấu hình SessionFactory trong Spring. Điều này giúp bạn tập trung vào kỹ thuật (best practices) nhiều hơn là hình dung vào mẫu gần nhất.

** 3. Tại sao mọi người thích nó:**

Spring không chỉ giải quyết các vấn đề cho developer, mà nó còn bắt tuân theo thói quen lập trình tốt như code các giao diện, giảm sự kết nối và kiểm tra (test) dễ dàng. Theo mô hình lập trình mới thì developer tốt phải viết các Test Driven Development (TDD). TDD là cách để test những lớp bạn viết. Theo cách này, bạn biết chính xác những gì bạn muốn phát triển. Spring có một bộ test riêng của nó để cho phép test dễ dàng hơn. So sánh điều này với kỹ thuật tốt nhất từ J2EE, nó khuyến khích bạn nên sử dụng EJB để điều khiển tầng nghiệp vụ. Nhưng EJB thì yêu cầu một container để có thể chạy nó, vì thế bạn phải khởi động container để test chúng. ** **

**4. Lời phê bình:**

Có một số phê bình rằng Spring không phải là chuẩn, nghĩa là nó không phải là một thành phần của đặc tả J2EE và nó không được phát triển bởi Java Community Process. Tuy nhiên, lý do chính cho chuẩn là đảm bảo tương thích với nhiều appserver. Code mà bạn phát triển trên một server nên chạy trên một server khác, nhưng đem EJB từ container này sang container khác thì không dễ dàng. Những vendor khác yêu cầu file triển khai khác và không có cách chung để cấu hình data source hoặc phụ thuộc vào các container khác. Tuy nhiên coding tầng nghiệp vụ với Spring thì có thể tương thích với nhiều container - không cần thay đổi code hoặc file deployment. ****

**5. Spring làm việc như thế nào:**

Spring là cách cấu hình ứng dụng với JavaBean. Khi nói tới JavaBean, có nghĩa là các lớp với phương thức getter và setter cho các biến của nó. Đặc biệt, nếu một lớp đưa ra setters, Spring sẽ cấu hình lớp đó. Sử dụng Spring, bạn có thể đưa ra bất kỳ sự phụ thuộc nào với setter và sau đó cấu hình Spring để thiết lập sự phụ thuộc này. Thậm chí tốt hơn, thay vì bạn phải viết một lớp để thiết lập kết nối đến database, bạn có thể cấu hình điều đó trong Spring. Cách giải quyết sự phụ thuộc này có tên là: Inversion of Control hoặc Dependency Injection. Spring có 7 module riêng, mỗi module sẽ có các file JAR riêng.

** 6. Spring làm cho J2EE dễ dàng hơn:** ****

**6.1. Coding các giao tiếp:**

Cho phép developer khai báo các phương thức chứa các đối tượng sẽ được sử dụng. Sẽ có ích khi thiết kế ứng dụng sử dụng các giao tiếp bởi vì bạn sẽ thu được nhiều uyển chuyển trong việc cài đặt. Hơn nữa, giao tiếp với các tầng khác sử dụng inteface sẽ giảm code móc nối. ****

**6.2. Test dễ dàng:**

Sử dụng TDD là cách tốt nhất để phát triển code có chất lượng một cách nhanh chóng. Nó cho phép bạn chạy thiết kế bởi client (các test) trước khi bạn code các giao tiếp hoặc cài đặt. Project sử dụng Spring thì dễ dàng để test vì: Bạn có thể load và sử dụng các bean được quản lý bởi Spring trong JUnit test. Điều này cho phép bạn giao tiếp với chúng bình thường như từ bất kỳ client nào. Các lớp của bạn sẽ không phụ thuộc vào thư viện của nó. Điều này cho phép bạn không cần quan tâm đến Spring trong các test và các thiết lập phụ thuộc. ****

**6.3. Giảm code móc nối: Factory Pattern vs Spring**

Để dễ dàng bảo trì và mở rộng ứng dụng, chúng ta không muốn gắn chặt code vào resource xác định (ví dụ: bạn phải code để sử dụng chức năng SQL là xác định loại CSDL). Khi hoàn tất code các chức năng vào trong lớp, J2EE Pattern sẽ sử dụng Factory Pattern để kết nối các lớp lại với nhau. Nhìn chung, thật tốt để tạo các giao tiếp cho các tầng khác của ứng dụng. Điều này cho phép các tầng khác không biết cài đặt tồn tại. Ứng dụng J2EE có 3 tầng: _
Data Layer_: các lớp giao tiếp với database hoặc hệ thống lưu trữ dữ liệu khác.
_Business Logic_: các lớp giữ nghiệp vụ cung cấp cầu nối giữa tầng GUI và tầng Data.
_User Interface_: các lớp và các file view được sử dụng để đưa ra trang web hoặc giao diện desktop cho người dùng. ****

**6.4. Cấu hình và gắn sự phụ thuộc giữa các lớp:**

**** Factory Pattern là một J2EE pattern phức tạp. Không chỉ yêu cầu thiết lập 2 lớp, mà nó còn phải quản lý sự phụ thuộc của các đối tượng "factoried" đó. Ví dụ, nếu bạn lấy một DAO từ factory, làm thế nào bạn chuyển vào một connection?. Bạn có thể chuyển nó vào như một phần của constructor, nhưng nếu DAO yêu cầu một Hibernate Session, thì bạn phải tạo tham số constructor là một java.lang.Object và sau đó ép nó sang loại được yêu cầu, nhưng nó thì không đẹp lắm. Cách tốt nhất là sử dụng Spring để gắn các giao diện. Mỗi thứ được cấu hình trong XML file và bạn có thể dễ dàng thay đổi cài đặt bằng cách sửa file này. Thậm chí, bạn có thể viết unit test vì thế nếu ai đó muốn biết những gì bạn cài đặt, bạn có thể chạy chúng. Nó thì làm việc tốt với iBATIS và Hibernate. Test gần như là client, nó là cách tốt để đảm bảo tầng nghiệp vụ sẽ làm việc với DAO. Ví dụ lấy một UserDAO sử dụng Spring:

[code]
ApplicationContext ctx = new ClassPathXmlApplicationContext("/WEB-INF/applicationContext.xml");
UserDAO dao = (UserDAO) ctx.getBean("userDAO");
[/code]

Bạn sẽ phải cấu hình bean "userDAO" trong /WEB-INF/applicationContext.xml file.

[code]
<bean id="userDAO">
     <property name="sessionFactory">
          <ref local="sessionFactory"/>
     </property>
</bean>
[/code]

Nếu bạn muốn thay đổi cài đặt của UserDAO, tất cả những gì bạn cần thay đổi là thuộc tính "class" trong khối XML trên. Nó là pattern rõ ràng hơn mà bạn có thể sử dụng trong ứng dụng. Tất cả những gì bạn cần là thêm một vài dòng vào file định nghĩa các bean. Hơn nữa, Spring quản lý Hibernate Session này cho bạn thông qua thuộc tính "sessionFactory". Bạn không cần phải lo lắng về bất kỳ cái gì nữa. Spring được xem như một lightweight container bởi vì bạn dùng ApplicationContext để khởi tạo các đối tượng. Các đối tượng được định nghĩa trong context file (được gọi là file định nghĩa bean). File này thì đơn giản là XML file với một số element <bean>. Ý nghĩa khác, nó là bean container hoặc object library mà mọi thứ được thiết lập hoặc sẵn sàng để sử dụng. Nó không thực sự là một container theo ý nghĩa truyền thống (như Tomcat hoặc WebLogic), nhưng nhiều hơn một "configured beans provider".

**6.5. Relational Mapping Tools:**

Một hữu ích khác của Spring là hỗ trợ ORM tool. Thuận lợi đầu tiên của việc sử dụng các hỗ trợ ORM là bạn không cần nhiều try/catch. Spring đã gói các checked exception với runtime exception, cho phép developer sử dụng nếu muốn catch exception. Ví dụ về phương thứ getUsers() của UserDAOHibernate không sử dụng Spring:
[code]
public List getUsers() throws DAOException {
List list = null;
try {
list = ses.find("from User u order by upper(u.username)");
} catch (HibernateException he) {
he.printStackTrace();
throw new DAOException(he);
}
return list;
}
[/code]

Sau đây là ví dụ sử dụng hỗ trợ Hibernate của Spring:

[code]
public List getUsers() {
return getHibernateTemplate() .find("from User u order by upper(u.username)");
}
[/code]


=> ngắn gọn và đơn giản hơn. Từ ví dụ này, bạn có thể thấy được Spring thì dễ dàng để móc nối các tầng trong ứng dụng, sự phụ thuộc. Nó đơn giản các API để sử dụng ORM tool như Hibernate.

_Nguồn: Javavietnam.org_
