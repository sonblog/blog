---
author: quachson
comments: true
date: 2016-11-08 08:44:37+00:00
template: "post"
link: https://quachson.com/dealing-with-org-hibernate-lazyinitializationexception/
slug: dealing-with-org-hibernate-lazyinitializationexception
title: Dealing with org.hibernate.LazyInitializationException
wordpress_id: 1266
categories:
- Hibernate
---

Câu chuyện lâu rồi bây giờ nhớ mới kể. Hổi đó đi phỏng vấn bị hỏi về vấn đề lazy loading trong Hibernate. Có 1 Object trong đó có 1 List<Object> như quan hệ 1-n, sau khi query object thì KHÔNG getList object con dc và cách giải quyết là làm sao. Lúc này mình cũng ngạc nhiên, vì mình cũng hay thường dùng lazy loading, khi getList bình thường. Câu hỏi lạ thật, sau này về google thì mới biết là vấn đề LazyInitializationException nhưng ai mà hỏi vậy.

Vấn đề LazyInitializationException là khi query Object có chứa List<> sau đó close session rồi gọi object.getList thì mới bị lỗi LazyInitializationException.

    
    Session s = sessions.openSession();
    Transaction tx = s.beginTransaction();
    
    Employee e = (Employee) s.createQuery("from Employee e where e.name=:empName").setString("empName", eName).uniqueResult();
    List roles = u.getRoles();
    
    tx.commit();
    s.close();
    
    String role = roles.get(0); //  This line will throw error



    
    Exception in thread "main" org.hibernate.LazyInitializationException: could not initialize proxy - no Session
       at org.hibernate.proxy.AbstractLazyInitializer.initialize(AbstractLazyInitializer.java:57)
       at org.hibernate.proxy.AbstractLazyInitializer.getImplementation(AbstractLazyInitializer.java:111)
       at org.hibernate.proxy.pojo.cglib.CGLIBLazyInitializer.invoke(CGLIBLazyInitializer.java:150)




 Vấn đề này có rất nhiều cách giải quyết,




1/ Best solution: Bị lỗi là do object đã bị detached rồi session của hibernate, thì mình reattach nó lại bằng cách: session.update(object);




2/ Không dùng kiểu Lazy nữa mà dùng Eager, performance sẽ bị chậm vì lúc nào nó cũng load hết nhánh con.




3/ nếu dùng JPA thì: @PersistenceContext(type = PersistenceContextType.EXTENDED)







Còn nhiều cách nữa mà thấy phức tạp, ko tối ưu, ai còn cách nào hay thì xin comment chỉ giáo nhé.
