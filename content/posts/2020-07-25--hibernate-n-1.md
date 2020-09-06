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

The most implicit n+1 is to use library to copy properties `BeanUtils.copyproperties` or write your own code using reflection copy properties then all getter and all getter of nested object are called.

## **Solutions**
An easy way to check hibernate n+1 that show query hibernate `format_sql=true`, example for Spring 

```
spring.jpa.properties.hibernate.format_sql=true
```  
### **Solution 1:**
Using join load immediately in one query, incorrect when using pagination.

**Advantages:** Write code less, only declare annotation is done.

**Disadvantages:** 
  - Many potential risks are out of control, cause always load join data. Adding more and more anotation `@ManyToOne` makes the entity bigger and bad performance.
  - Inner join will be OK, but using outer left join will be very slower when got a lot of data than separate another query.

### **Solution 2:** 
Don't using `@ManyToOne` or `@OneToOne` for Entity, Write code by hand to load data for model.

**Advantages:** Write your own code, load/get enought data to use, easy to custom and maintenance.

**Disadvantages:** Write more codes than (1).

### Implement in coding for solution 1:

1. Join: using in query query
2. Entity Graph (NamedEntityGraph)

### Implement in coding for solution 2:
- Using multiple queries 
