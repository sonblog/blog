---
author: admin
comments: true
date: 2011-04-22 08:16:17+00:00
template: "post"
link: https://quachson.com/design-pattern-adapter/
slug: design-pattern-adapter
title: 'Design Pattern: Adapter'
wordpress_id: 506
categories:
- Design Pattern
- Java
tags:
- Design Pattern
- Java
---

**Định Nghĩa**:

Convert the existing interfaces to a new interface to achieve compatibility and reusability of the unrelated classes in one application. Also known as **Wrapper pattern**.

Adapter nôm na là một bộ chuyển đối. Laptop cũng cần adapter để chuyển từ điện AC sang DC. Đi nước ngoài thì phải xem họ xài ổ cắm tròn hay dẹt, 3 chấu hay 2 chấu. Nếu không phải mua adapter.

_**Vậy adapter là 1 bộ chuyển đổi dùng để kết nối 2 hay nhiều thiết bị khác nhau lại.**_

**Khi nào ứng dụng và những lợi ích**:

- Cố gắng giống như Interface ( như WindowAdapter... )

- Make a pluggable kit: To reuse classes and make new class compatible with existing ones. For example, A **clean** system is already designed, you want to add more job in, the **Extra** interface uses adapter pattern to **plug in** the existing system.

Xem ví dụ:

- Những Adapter class nổi tiếng của Java API như là: WindowAdapter,ComponentAdapter, ContainerAdapter, FocusAdapter, KeyAdapter, MouseAdapter và MouseMotionAdapter

[code lang="java"]

public interface Windowlistener {
     public void windowClosed(WindowEvent e);
     public void windowOpened(WindowEvent e);
     public void windowIconified(WindowEvent e);
     public void windowDeiconified(WindowEvent e);
     public void windowActivated(WindowEvent e);
     public void windowDeactivated(WindowEvent e);
     public void windowClosing(WindowEvent e);
}

[/code]

[code lang="java"]

public class WindowAdapter implements WindowListener{
     public void windowClosed(WindowEvent e){}
     public void windowOpened(WindowEvent e){}
     public void windowIconified(WindowEvent e){}
     public void windowDeiconified(WindowEvent e){}
     public void windowActivated(WindowEvent e){}
     public void windowDeactivated(WindowEvent e){}
     public void windowClosing(WindowEvent e){}
}

[/code]

WindowListener interface có 7 method(), nếu implement thì phải hiện thực hết 7 phương thức, có những phương thức ta không có dùng. WindowAdapter implement WindowListener với 7 phương thức rỗng (empty method). Ta chỉ cần extend từ WindowAdapter thì chỉ override lại phương thức nào cần dùng, không cần phải hiện thực lại hết 7 phương thức.

[code lang="java"]
import javax.swing.*;
import java.awt.event.*;
class Test extends JFrame {
    public Test () {
        setSize(200,200);
        setVisible(true);
        addWindowListener(new Closer());
    }
    public static void main(String[] args) {
        new Test();
    }
    class Closer extends WindowAdapter {
        public void windowClosing(WindowEvent e) {
            System.exit(0);
        }
    }
}
[/code]

-  Make a pluggable kit

    
    interface Clean {
        public void makeClean();
    }
    class Office implements Clean{
        public void makeClean() {
            System.out.println("Clean Office");
        }
    }
    class Workshop implements Clean{
        public void makeClean() {
            System.out.println("Clean Workshop");
        }
    }
    
    interface Extra extends Clean{
        public void takeCare();
    }
    class Facility implements Extra{
        public void makeClean() {
            System.out.println("Clean Facility");
        }
        public void takeCare() {
            System.out.println("Care has been taken");
        }
    }
    In order to reuse Workshop and Office classes,
    we create an adapter interface Extra and
    add new job takeCare in the system.
    
    class Test {
       static void Jobs (Extra job) {
           if (job instanceof Clean)
               ((Clean)job).makeClean();
           if (job instanceof Extra)
               ((Extra)job).takeCare();
       }
       public static void main(String[] args) {
           Extra e = new Facility();
           Jobs(e);
           Clean c1 = new Office();
           Clean c2 = new Workshop();
           c1.makeClean();
           c2.makeClean();
           e.makeClean();
       }
    }


- Wrapper:  class Data có sẵn trong hệ thống đã được test cẩn thận, ta muốn kế thừa những method() từ class Data và viết thêm một số tính năng.

[code lang="java"]
//well-tested class
class Data {
   public void add(Info){}
   public void delete(Info) {}
   public void modify(Info){}
   //...
}
[/code]
[code lang="java"]
//Use Data class in your own class
class AdaptData {
   Data data;
   public void add(Info i) {
       data.add(i);
       //more job
   }
   public void delete(Info i) {
      data.delete(i);
      //more job
   }
   public void modify(Info i) {
      data.modify(i);
      //more job
   }
   //more stuff here
   //...
}
[/code]
