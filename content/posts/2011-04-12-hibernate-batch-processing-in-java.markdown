---
author: admin
comments: true
date: 2011-04-12 11:04:51+00:00
template: "post"
link: https://quachson.com/hibernate-batch-processing-in-java/
slug: hibernate-batch-processing-in-java
title: Hibernate Batch processing in Java
wordpress_id: 488
categories:
- Hibernate
- Java
tags:
- Hibernate
- Java
---

[code lang="java"]

Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();
for ( int i=0; i<<strong>100000</strong>; i++ ) {
Customer customer = new Customer(.....);
session.save(customer);
}
tx.commit();
session.close();

[/code]

Viết code như vậy sẽ bị _OutOfMemoryException _khi chạy tới khoảng dòng thứ 50,000, Vì Hibernate caches tất cả những Customer vừa mới được thêm vào trong _session-level._

Để không bị lỗi như vậy ta sẽ thực hiện Batch processing. Muốn thực hiện batch processing có rất nhiều cách.

**Cách 1:** batch size and disable second cache

Set JDBC batch size (10-50) trong

hibernate.jdbc.batch_size 20

Disable second cache để tăng tốc thôi chứ không nhất thiết lúc nào cũng phải disable. Không disable cũng không sao

hibernate.cache.use_second_level_cache false

**Cách 2**: Sử dụng _flush()_ và _clear()_ của Session

[code lang="java"]

Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();
for ( int i=0; i<<strong>100000</strong>; i++ ) {
Customer customer = new Customer(.....);
session.save(customer);
if ( i % 20 == 0 ) { //20, same as the JDBC batch size
        // flush a batch of inserts and release memory:
        session.flush();
        session.clear();
}
}
tx.commit();session.close();
[/code]

Dùng cách này thì không cần set batch size hay disable second cache, giống như xử lý bằng tay.

Update thì cũng tương tự như vậy.

[code lang="java"]

Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();
ScrollableResults customers = session.getNamedQuery("GetCustomers")
.setCacheMode(CacheMode.IGNORE)
.scroll(ScrollMode.FORWARD_ONLY);
int count=0;
while ( customers.next() ) {
Customer customer = (Customer) customers.get(0);
customer.updateStuff(...);
if ( ++count % 20 == 0 ) {
//flush a batch of updates and release memory:
session.flush();
session.clear();
}
}
tx.commit();
session.close();
[/code]



**Cách 3**: **The StatelessSession**

StatelessSession sẽ **không cache **lại ở bất cứ mức nào: first-level cache, second-level hay query cache. Cách này thì sẽ không sợ cache làm OutOfMemory. Xem ví dụ minh hoạt sẽ hiểu rõ hơn.

[code lang="java"]

<strong>StatelessSession </strong>session = sessionFactory.<strong>openStatelessSession</strong>();
Transaction tx = session.beginTransaction();
ScrollableResults customers = session.getNamedQuery("GetCustomers")
.scroll(ScrollMode.FORWARD_ONLY);
while ( customers.next() ) {
Customer customer = (Customer) customers.get(0);
customer.updateStuff(...);
session.update(customer);
}
tx.commit();
session.close();

[/code]

Để giải quyết vấn đề này dừng lại có cách thử 3 là đã đủ nhưng vẫn còn 1 cách thứ 4 có lẽ dùng để tham khảo.

**Cách 4**: DML-style operations

DML = SQL **D**ata **M**anipulation **L**anguage. Dùng cách này thì chọc thẳng vào Database (INSERT, UPDATE, DELTE) mà không ảnh hưởng đến in-memory state. Vì ORM persistence Objects and Database. Những thay đổi Object này sẽ được cập nhật vào database khi _flush()._

[code lang="java"]
Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();
String hqlUpdate = "update Customer c set c.name = :newName where c.name = :oldName";
// or String hqlUpdate = "update Customer set name = :newName where name = :oldName";
int updatedEntities = s.createQuery( hqlUpdate )
     .setString( "newName", newName )
     .setString( "oldName", oldName )
     .executeUpdate();
tx.commit();
session.close();
[/code]

[code lang="java"]
Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();
String hqlDelete = "delete Customer c where c.name = :oldName";
// or String hqlDelete = "delete Customer where name = :oldName";
int deletedEntities = s.createQuery( hqlDelete )
     .setString( "oldName", oldName )
     .executeUpdate();
tx.commit();
session.close();
[/code]

[code lang="java"]
Session session = sessionFactory.openSession();
Transaction tx = session.beginTransaction();
String hqlVersionedUpdate = "update versioned Customer set name = :newName where name = :oldName";
int updatedEntities = s.createQuery( hqlUpdate )
.setString( "newName", newName )
.setString( "oldName", oldName )
.executeUpdate();
tx.commit();
session.close();
[/code]

Cách này ít dùng chỉ mang tính chất giới thiệu, muốn tìm hiểu thêm thì google thêm nhé :p
