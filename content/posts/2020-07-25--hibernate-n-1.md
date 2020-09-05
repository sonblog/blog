---
title: Hibernate N+1 problem
date: 2020-07-25 10:30:00+00:00
template: "post"
draft: false
slug: "hibernate-n1"
category: "Hibernate"
tags:
  - "Hibernate"
description: "Hibernate n+1 is very common and usually meet when use Hibernate. Attention when using to get good performance."
---
## **Context**

Using `@ManyToOne`, `@OneToOne` annotation

`FetchType.LAZY` or Eager is get n+1. Lazy when call getXXX then will load/fetch data, Eager is always get data already.

Dễ bị một cách không tường minh nhất là dùng thư viện copy properties `BeanUtils.copyproperties` hay là code tự viết, quét qua object gọi hết tất cả hàm get và những object con lồng con.

## **Solutions**
An easy way to check hibernate n+1 that show query hibernate `format_sql=true`, example for Spring 

```
spring.jpa.properties.hibernate.format_sql=true
```  
### **Solution 1:**
Using join load immediately in one query, lưu ý khi dùng phân trang sẽ không còn đúng.

**Ưu điểm:** Write code less, only declare annotation is done.

**Khuyết điểm:** 
  - Nhiều nguy cơ tiềm ẩn không kiểm soát, do lúc nào cũng load data lên khi entity có nhiều liên kết và entity lồng entity và liên kết lồng liên kết, có nhiều configurations để load data liên kết sẽ khó maintain. 
  - Inner join will be OK, but using outer left join will be very slower when got a lot of data than separate another query.

### **Solution 2:** 
Don't using `@ManyToOne` or `@OneToOne` for Entity, Write code by hand to load data for model.

**Ưu điểm:** Do mình tự code, cần load gì thì load, sẽ tối ưu hơn, dễ custom.

**Khuyết điểm:** Write more codes than (1).

### Implement in coding for solution 1:

1. Join: dùng trong query
2. Entity Graph (NamedEntityGraph)

### Implement in coding for solution 2:
- Using multiple queries 



