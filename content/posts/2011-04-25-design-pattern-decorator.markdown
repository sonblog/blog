---
author: admin
comments: true
date: 2011-04-25 16:38:26+00:00
layout: post
link: https://quachson.com/design-pattern-decorator/
slug: design-pattern-decorator
title: 'Design Pattern: Decorator'
wordpress_id: 550
categories:
- Design Pattern
- Java
tags:
- Design Pattern
- Java
---

**Định nghĩa**: Decorator là trang trí. Decorator cho 1 class nghĩa là thêm thuộc tính hoặc hành vi, hoặc mở rộng hành vi cho lớp đó mà không dùng subclass.

Ví dụ có lớp Number với phương thức in ra số ngẫu nhiên

[code lang="java"]
public class Number {
   public void print() {
      System.out.println(new Random().nextInt());
   }
}

public class Decorator {
   public Decorator() {
      System.out.println("This is random number: ");
      new Number().print();
   }
}
public static void main(String[] args) {
   Decorator decorator = new Decorator();
}


[/code]
