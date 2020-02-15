---
author: admin
comments: true
date: 2011-04-25 06:43:02+00:00
layout: post
link: https://quachson.com/design-pattern-singleton/
slug: design-pattern-singleton
title: 'Design Pattern: Singleton'
wordpress_id: 540
categories:
- Design Pattern
- Java
tags:
- Creational Patterns
- Design Pattern
- Java
---

**Singleton Pattern** là một trong những pattern thuộc **Creational Patterns** (Abstract Factory, Builder, Factory Method, [Prototype](http://wp.me/pimex-8O), [Singleton](http://quachson.wordpress.com/2011/04/25/design-pattern-singleton/))

Singleton Pattern là một pattern nhằm hạn chế việc khởi tạo nhiều instantiation của một class hoặc là chỉ dùng chung 1 instantiation của một class.

Hiện thực Singleton Pattern theo kiểu **Lazy initialization** (khái niệm của lazy nghĩa là instantiation của clas sẽ không được tạo sẵn khi ta chưa gọi đến hay là chưa dùng đến) theo kiểu thuật _double-checked locking_.

[code lang="java"]

package java.designpattern.creational;

public class SingletonLazy {
  private static SingletonLazy instance = null;

  // To make sure that the object cannot be instantiated any other way
  private SingletonLazy() {  }

  // double-checked locking
  public static SingletonLazy getInstance() {
    if (instance == null) {
      synchronized (SingletonLazy.class) {
        if (instance == null) {
          instance = new SingletonLazy();
        }
      }
    }
    return instance;
  }
}

[/code]

Hiện thực Singleton Pattern theo kiểu **Eager initialization**. Nếu chương trình lúc nào cũng cần instance này và việc khởi tạo không tốn quá nhiều thời gian và tài nguyên thì ta dùng kỹ thuật Eager.

[code lang="java"]
package java.designpattern.creational;

public class SingletonEager {
  private static final SingletonEager instance = new SingletonEager();

  private SingletonEager() {}

  public static SingletonEager getInstance() {
    return instance;
  }

}
[/code]

- Không cần _synchronize_ cho phương thức** getInstance(), **tất cả mọi threads đều thấy chung 1 instance và không cần phải khóa.

- Từ khóa final nghĩa là instance buộc không được override (định nghĩa, khai báo) lại.

Static block initialization

Có vài người lại thích dùng theo kiểu pre-processing với từ khóa static, tuy nhiên cơ chế class loader cũng sẽ giống nhau.

[code lang="java"]
package java.designpattern.creational;

public class SingletonEagerStatic {
private static final SingletonEagerStatic instance;

static {
instance = new SingletonEagerStatic();
}

private SingletonEagerStatic() {    }

public static SingletonEagerStatic getInstance() {
return instance;
}

}

[/code]

The solution of Bill Pugh

[code lang="java"]

package java.designpattern.creational;

public class Singleton {

  // Private constructor prevents instantiation from other classes
  private Singleton() {  }

  /**
  * SingletonHolder is loaded on the first execution of Singleton.getInstance()
  * or the first access to SingletonHolder.INSTANCE, not before.
  */
  private static class SingletonHolder {
    public static final Singleton INSTANCE = new Singleton();
  }

  public static Singleton getInstance() {
    return SingletonHolder.INSTANCE;
  }

}

[/code]
