---
author: admin
comments: true
date: 2011-04-25 06:18:51+00:00
layout: post
link: https://quachson.com/design-pattern-iterator/
slug: design-pattern-iterator
title: 'Design Pattern: Iterator'
wordpress_id: 530
categories:
- Design Pattern
- Java
tags:
- Design Pattern
- Java
---

**Định nghĩa:**

Iterator là một dạng vòng lặp. Đối với 1 danh sách các đối tượng không đồng nhất nhau thì việc đưa vào các danh sách như List, Sort, Map sẽ giúp cho việc duyệt qua danh sách dễ dàng mà không cần quan tâm đến sự hiện diện bên trong của danh sách.

Ví dụ có interface Employee và 2 class hiện thực là HourlyEmployee - nhân viên làm theo giờ và RegularEmployee - nhân viên lãnh lương tháng.

[code lang="java"]
interface Employee {
     double earnings();
}
[/code]



[code lang="java"]
public class HourlyEmployee implements Employee {
   private double salaryPerHour;
   private String name;

   public HourlyEmployee(double salaryPerHour, String name) {
      super();
      this.salaryPerHour = salaryPerHour;
      this.name = name;
   }

   public double earnings() {
      return 40*salaryPerHour;
   }

   public String toString() {
      return name;
   }
}
[/code]



[code lang="java"]
public class RegularEmployee implements Employee {
   private double salaryPerMonth;
   private String name;

   public RegularEmployee(double salaryPerMonth, String name) {
      super();
      this.salaryPerMonth = salaryPerMonth;
      this.name = name;
   }

   public double earnings() {
      return salaryPerMonth;
   }

   public String toString() {
      return name;
   }
}
[/code]

Sử dụng pattern này:

[code lang="java"]
public static void main(String[] args) {
   List list = new ArrayList();
   list.add(new HourlyEmployee(30, "Petter"));
   list.add(new RegularEmployee(20000000, "Mary"));
   Iterator itr = list.iterator();
   while(itr.hasNext()) {
      Employee em = (Employee)itr.next();
      System.out.println(em + " earns "+em.earnings());
   }
}
[/code]


Source: http://javadevelopervietnam.blogspot.com/2010/10/iterator-loai-behavioral-o-kho-thap.html
