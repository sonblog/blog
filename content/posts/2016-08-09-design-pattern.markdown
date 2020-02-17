---
author: quachson
comments: true
date: 2016-08-09 12:21:30+00:00
template: "post"
link: https://quachson.com/design-pattern/
slug: design-pattern
title: Design Patterns
wordpress_id: 1258
categories:
- Design Pattern
tags:
- Design Pattern
- Java
---

Tổng hợp những bài viết về Design Pattern

I/ Creational Patterns (6)
- [Singleton](https://quachson.wordpress.com/2011/04/25/design-pattern-singleton/): hạn chế việc khởi tạo nhiều Objects
- [Builder](https://quachson.wordpress.com/2016/08/10/builder-patterns/): constructor có quá nhiều parameters, dùng builder để group lại
- Factory: như nhà máy sản xuất, chỉ cần cho đúng nguyên liệu thì sẽ cho ra đúng sản phẩm.
- Factory Method: (1 method cho nhiều interface implements)
- Abstract Factory: giống Factory nhưng trả về Abstract
- Prototype (Clone)

II/ Structural Patterns (7)
- [Adapter](https://quachson.wordpress.com/2011/04/22/design-pattern-adapter/): replace Interface, dùng Composite or Decorator (has-a or is-a)
- Bridge: giống giống Dependency Inversion, trong lớp con extend Abstract chứa Interface
- Decorator: (wrapper) extend
- Composite: chứa trong
- Proxy: như 1 vị luật sư đại diện cho mình
- Facade: 1 method tập hợp nhiều services, giống như thủ tục 1 cửa.
- Flyweight: cache

III/ Behavioral Patterns:
- [Observer](https://quachson.wordpress.com/2016/08/11/observer-pattern/): notify to others class when have 1 class update
- [Chain of Resposibility](https://quachson.wordpress.com/2016/08/11/chain-of-responsibility-pattern/): servlet Filter, những classes trong chain sẽ được duyệt qua 1 lần. Cách thực thi cũng giống Observer nhưng về bản chất thì khác nhau. Hiện thực giống như liên kết đơn hay dùng List đều dc.
- Iterial: giống như For
- [Command](https://quachson.wordpress.com/2016/08/12/command-pattern/): encapsulation, đóng gói tất cả thông tin vào trong 1 class, bao gồm cả methods. Có 4 terms trong: command, invoker, target, client (như void main).
- Interperter: trình thông dịch, Define a macro language and syntax, parsing input into objects which perform the correct opertaions.
- State: An object appears to change its` class when the class it passes calls through to switches itself for a related class.
- [Strategy](https://quachson.wordpress.com/2016/08/12/strategy-pattern/): method(interface)
- Template Method: method(abstract)
- [Visitor](https://quachson.wordpress.com/?p=1014&preview=true): One or more related classes have the same method, which calls a method specific for themselves in another class.
- Mememtor: undo, redo, stack

- Java 7 new features
+ Try with multi cache
+ Diamond operators
+ Using strings in switch statements
+ Automatic resource management: using open close file, connections, Input/Output
+ Numeric literals with underscores

- Java 8 new features
+ Lambda expression − Adds functional processing capability to Java.
+ Method references − Referencing functions by their names instead of invoking them directly. Using functions as parameter.
+ Default method − Interface to have default method implementation.
+ New tools − New compiler tools and utilities are added like ‘jdeps’ to figure out dependencies.
+ Stream API − New stream API to facilitate pipeline processing.
+ Date Time API − Improved date time API.
+ Optional − Emphasis on best practices to handle null values properly.
+ Nashorn, JavaScript Engine − A Java-based engine to execute JavaScript code.
