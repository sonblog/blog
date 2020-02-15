---
author: admin
comments: true
date: 2011-04-25 06:38:57+00:00
layout: post
link: https://quachson.com/design-pattern-abstract-factory/
slug: design-pattern-abstract-factory
title: 'Design Pattern: Abstract Factory'
wordpress_id: 537
categories:
- Design Pattern
- Java
tags:
- Design Pattern
- Java
---

**Định nghĩa:**

Abstract Factory trừu tượng hơn Factory 1 mức. Thay vì chỉ cần 1 interface Factory, pattern này đòi hỏi thêm 2 lớp Factory hiện thực interface này. Ví dụ interface Factory có 1 phương thức là createButton(), 2 lớp hiện thực là WindowFactory và MacFactory. Hai lớp này sẽ trả về lần lượt 2 đối tượng là WindowButton và MacButton tương ứng. Trong đó WindowButton và MacButton lần lượt là 2 lớp hiện thực của interfact Button.

[code lang="java"]
public interface Button {
void paint();
}
[/code]

[code lang="java"]
public class OSXButton implements Button {
   public void paint() {
      System.out.println("Draw OSX button");
   }
}
[/code]

[code lang="java"]
public class WindowButton implements Button {
   public void paint() {
      System.out.println("Drawing Window button");
   }
}
[/code]

[code lang="java"]
public interface Factory {
   Button createButton();
}
[/code]

[code lang="java"]
public class WindowFactory implements Factory {
   public Button createButton() {
      return new WindowButton();
   }
}
[/code]

[code lang="java"]
public class OSXFactory implements Factory {
   public Button createButton() {
      return new OSXButton();
   }
}
[/code]


Chạy test:

[code lang="java"]
public static void main(String[] args) {
   Factory factory = new WindowFactory();
   Button button = factory.createButton();
   button.paint();
}
[/code]
Nguồn: http://javadevelopervietnam.blogspot.com/2010/10/abstract-factory-loai-creation-o-kho.html
