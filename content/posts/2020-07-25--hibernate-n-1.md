---
title: Hibernate N+1 problem
date: 2020-07-25 10:30:00+00:00
template: "post"
draft: false
slug: "hibernate-n1"
category: "Hibernate"
tags:
  - "Hibernate"
description: "Hibernate n+1 rất phổ biến và thường gặp khi dùng Hibernate. Khi dùng cần phải lưu ý để performance tốt hơn. "
---
## **Context**

Khi dùng `@ManyToOne`, `@OneToOne`. 

`FetchType.LAZY` hay Eager đều bị n+1 hết. Lazy là khi gọi getXXX vào sẽ load data, còn Eager thì luôn luôn load data lên sẵn.

Dễ bị một cách không tường minh nhất là dùng thư viện copy properties `BeanUtils.copyproperties` hay là code tự viết, quét qua object gọi hết tất cả hàm get và những object con lồng con.

## **Solutions**
Cách dễ nhất để kiểm tra có bị hibernate +1 hay không là bật `format_sql=true`, example for Spring 

```
spring.jpa.properties.hibernate.format_sql=true
```  
### **Cách 1:**
Dùng join load ngay lặp tức trong 1 câu query, lưu ý khi dùng phân trang sẽ không còn đúng.

**Ưu điểm:** Tiện lợi trong viết coding, khai báo annotation là xong.

**Khuyết điểm:** 
  - Nhiều nguy cơ tiềm ẩn không kiểm soát, do lúc nào cũng load data lên khi entity có nhiều liên kết và entity lồng entity và liên kết lồng liên kết, có nhiều configurations để load data liên kết sẽ khó maintain. 
  - Inner join thì không sao, nhưng dùng outer left join sẽ rất chậm khi có nhiều data so với tách ra 1 query riêng sẽ nhanh hơn.

### **Cách 2:** 
Không dùng `@ManyToOne` hay `@OneToOne` cho Entity, tự viết code để load vào model.

**Ưu điểm:** Do mình tự code, cần load gì thì load, sẽ tối ưu hơn, dễ custom.

**Khuyết điểm:** viết code nhiều hơn (1).

### Implement in coding for solution 1:

1. Join: dùng trong query
2. Entity Graph (NamedEntityGraph)

### Implement in coding for solution 2:
- Dùng nhiều query 



