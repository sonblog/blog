---
author: admin
comments: true
date: 2010-01-31 02:09:13+00:00
layout: post
link: https://quachson.com/polymorphism-in-java/
slug: polymorphism-in-java
title: Polymorphism in Java
wordpress_id: 29
categories:
- Design Pattern
- Java
tags:
- Design Pattern
- Java
---

Ví dụ về tính đa hình trong thế giới thực là nước: Khi bị đóng băng, nước sẽ thành đá. Khi nước đá tan chảy sẽ xuất hiện dạng lỏng. Khi đun sôi nước ở thể lỏng sẽ bốc hơi thành khí.

Tính đa hình của ngôn ngữ máy tính có 4 loại: _coercion, overloading, parametric, _và_inclusion_.

- **Coercion polymorphism** (ép kiểu) : dùng để chỉ một hoạt động đơn lẻ một số loại hình phục vụ thông qua các loại hình chuyển đổi tiềm ẩn. Ví dụ như toán hạng trừ (-) chỉ cho phép số nguyên trừ số nguyên (5 - 3), số thực trừ số thực (5.5 - 3.3). Tuy nhiên nếu 5.5 - 3 ( một bên là số nguyên, một bên là số thực ) thì trình biên dịch (compiler) sẽ chuyển số nguyên thành số thực, nếu không sẽ xuất hiện lỗi kiểu bởi vì toán hạng trừ của java không trừ số nguyên từ số thực và ngược lại. Một ví dụ khác của coercion polymorphism khi gọi phương thức. Nếu lớp con khai báo phương thức với tham số là lớp cha và nếu gọi phương thức đó với đối số là lớp con, trình biên dịch sẽ chuyển đổi kiểu tham số lớp con thành lớp cha. Bằng cách này, chỉ định nghĩa lớp cha làm tham số là hợp lý.

- **Overloading polymorphism**: cùng tên phương thức, khác tham số.
Nhiều người không chú ý đến coercion and overloading polymorphism cũng là dạng chuẩn của tính đa hình. Xét kỹ thì coercion and overloading được xem là kiểu chuyển đổi. Ngược lại parametric và inclusion polymorphism được xem là tính đa hình thật sự.

- **Parametric polymorphism**: định nghĩa một lớp cho phép cùng tên field và phương thức liên kết với kiểu khác nhau trong mỗi lần khởi tạo lớp. Ví dụ: tạo lớp LinkedList với field là bất kỳ kiểu dữ liệu nào. LinkedList có thế add bất kỳ data type nào như là: String, Long, Float...

- **Inclusion polymorphism**: dc biết với tên khác là subtype polymorphism. Nên hiểu Java binds method gọi tới classes và objects như thế nào.
**Method binding**
class (dc biết như là static) and instance (dc biết như là nonstatic). Class methods associate with classes, and instance methods associate with objects. When you call a method, Java binds that method call to either a class or an object, depending on that method's category.

Listing 1 shows how Java statically binds class method calls to classes at compile time:
// SMB.java
class Superclass
{
_**static**_ void method ()
{
System.out.println ("Superclass method");
}
}

class Subclass extends Superclass
{
**_static_** void method ()
{
System.out.println ("Subclass method");
}
}

class SMB
{
public static void main (String [] args)
{
Superclass sc = new Superclass ();
sc.method ();

sc = new Subclass ();
sc.method ();
}
}

output:
Superclass method
Superclass method

--------------------------


----------------------------------------------------------------
Listing 2. DMB1.java
// DMB1.javaclass Superclass
{
void method ()
{
System.out.println ("Superclass method");
}
}

class Subclass extends Superclass
{
void method ()
{
System.out.println ("Subclass method");
}
}

class DMB1
{
public static void main (String [] args)
{
Superclass sc = new Superclass ();
sc.method ();

sc = new Subclass ();
sc.method ();
}
}

output:
Superclass method
Subclass method

------------------------------------------------------------------------------------------
Listing 3. DMB2.java
// DMB2.java

interface StartStop
{
void start ();
void stop ();
}

class Conference implements StartStop
{
public void start ()
{
System.out.println ("Start the conference.");
}

public void stop ()
{
System.out.println ("Stop the conference.");
}
}

class PoliticalConvention extends Conference
{
public void start ()
{
System.out.println ("Introduce the guest speaker.");
}

public void stop ()
{
System.out.println ("Grab some refreshments.");
}
}

class Vehicle implements StartStop
{
public void start ()
{
}

public void stop ()
{
}
}

class Car extends Vehicle
{
public void start ()
{
System.out.println ("Insert key in ignition and turn.");
}

public void stop ()
{
System.out.println ("Turn key in ignition and remove.");
}
}

class LawnMower extends Vehicle
{
public void start ()
{
System.out.println ("Move sliding switch to on and pull cord.");
}

public void stop ()
{
System.out.println ("Move sliding switch to off.");
}
}

class DMB2
{
public static void main (String [] args)
{
Vehicle v = new LawnMower ();

StartStop [] ss =
{
new Car (),
v,
new PoliticalConvention (),
new Conference ()
};

for (int i = 0; i < ss.length; i++)
{
ss [i].start ();
ss [i].stop ();
System.out.println ("");
}
}
}

output:
Insert key in ignition and turn.
Turn key in ignition and remove.

Move sliding switch to on and pull cord.
Move sliding switch to off.

Introduce the guest speaker.
Grab some refreshments.

Start the conference.
Stop the conference.

Để dễ hiểu ví dụ này, thì ta nên vẽ hình xuống giấy.


