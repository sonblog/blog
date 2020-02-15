---
author: admin
comments: true
date: 2011-12-26 09:47:56+00:00
layout: post
link: https://quachson.com/generic-persistent-layer-hibernate-spring/
slug: generic-persistent-layer-hibernate-spring
title: Generic Persistent Layer Hibernate and spring 3.1
wordpress_id: 712
categories:
- Hibernate
tags:
- Hibernate
---

**Ở Spring 3.1 thì không cần dùng HibernateTemplate nữa**

Bắt đầu từ Spring 3.0 và Hibernate 3.0.1, quản lý Hibernate Session với Springs _HibernateTemplate_ là không còn cần thiết nữa. Bây giờ có thể dùng [**contextual sessions**](http://docs.jboss.org/hibernate/core/3.6/reference/en-US/html/architecture.html#architecture-current-session) - sessions được quản lý trực tiếp bởi Hibernate và được giữ sống xuyên suốt trong tầm vực của một transaction.

Kết quả là, bây giờ cách thực hành tốt nhất là sử dụng trực tiếp API Hibernate thay vì _HibernateTemplate_, sẽ hiệu quả để  decouple the DAO layer hiện thực từ Spring entirely.


#### **Exception Translation without the template**


One of the responsibilities of _HibernateTemplate_ is **exception translation** – translating the low level Hibernate exceptions – which tie the API to Hibernate as the single possible ORM – into higher level, generic Spring exceptions.

Without the template to do that, exception translation can still be enabled by annotating the DAOs with the _@Repository_ annotation. That, coupled with a Spring bean postprocessor will advice all @Repository beans with all the implementations of _PersistenceExceptionTranslator_ found in the Spring context – to provide exception translation without using the template.

Exception translation is done through proxies; in order for Spring to be able to create proxies around the DAO classes, these must **not** be declared _**final**_.

****NOTE: As of Hibernate 3.0.1, transactional Hibernate access code can also be coded in plain Hibernate style. Hence, for newly started projects, consider adopting the standard Hibernate3 style of coding data access objects instead, based on {@link org.hibernate.SessionFactory#getCurrentSession()}.****

Spring configuration thì có 2 cách: java configuration và xml configuration, nhưng mình vẫn thích dùng cách truyền thống hơn đó là xml configuration. Tùy thói quen của mỗi người miễn sao thấy tiện cho mình là được.

Mục đích của bài viết này không nhằm hướng dẫn configuration mà generic persistence layer, nên chỉ một số lưu ý khi configuration.


# **Potential for Exceptions**




#### **The Transaction Factory
**


The Hibernate contract for creating **transactions** is specified by the _TransactionFactory_ interface. In order for Spring to fully manage transactions, the default implementation of this contract – _JDBCTransactionFactory_ – is replaced by default with it’s Spring-aware counterpart – _SpringTransactionFactory_.

This can also be done manually, in the Hibernate properties (it is however redundant):

_transaction.factory_class=org.springframework.orm.hibernate3.SpringTransactionFactory_


#### **The Current Session Context**


When the Hibernate _SessionFactory_ is created in the Spring context by it’s factory bean, it will create the _CurrentSessionContext_. This is the **contract for supporting the current session** concept and its implementation is decided by analyzing the _“hibernate.current_session_context_class”_ Hibernate property.

Setting this property to **_“managed”_** means using the managed implementation for contextual sessions – _ManagedSessionContext_ – which assumes that the current session is **managed by an external entity**. In our Spring context, that would fail with:


<blockquote>org.springframework.orm.hibernate3.HibernateSystemException: No session currently bound to execution context</blockquote>


Setting the property to _**“thread”**_ would enable the thread-bound strategy in the Hibernate configuration; this would also conflict with Spring Transaction management and would result in:


<blockquote>org.springframework.orm.hibernate3.HibernateSystemException: persist is not valid without active transaction</blockquote>


To let Spring manage transactions, this property needs to be _“org.springframework.orm.hibernate3.SpringSessionContext”_; because this is also the default, the explicit definition of the property can be removed.

to be continue...
