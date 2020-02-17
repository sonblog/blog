---
author: admin
comments: true
date: 2011-04-25 06:31:56+00:00
template: "post"
link: https://quachson.com/design-pattern-factory/
slug: design-pattern-factory
title: 'Design Pattern: Factory'
wordpress_id: 535
categories:
- Design Pattern
- Java
tags:
- Design Pattern
- Java
---

**Định nghĩa:**

Factory là 1 nhà máy sản xuất. Ý tưởng đưa ra là 1 nhà máy có thể sản xuất ra nhiều loại đối tượng khác nhau tùy theo yêu cầu đầu vào.
Ví dụ, ta có lớp Namer có 2 thuộc tính: First Name và Last Name. Tùy theo văn hóa từng nước mà thứ tự của First Name và Last Name sẽ xuất hiện khác nhau. Giả sử ta có 2 lớp con của Namer là FirstNameFirst và LastNameFirst. Hai lớp này sẽ căn cứ vào chuỗi tên truyền vào, bóc tách ra họ, tên, sau đó gán vào 2 thuộc tính firstName và lastName.

[code lang="java"]
public class Namer {
   protected String firstName;
   protected String lastName;
}
[/code]

[code lang="java"]
public class LastFirst extends Namer {
   public LastFirst(String fullName) {
      int i = fullName.indexOf(",");
      if (i>0) {
         lastName = fullName.substring(0,i);
         firstName = fullName.substring(i+1, fullName.length());
      } else {
         lastName = fullName;
         firstName = "";
      }
   }
}
[/code]

[code lang="java"]
public class FirstFirst extends Namer {
   public FirstFirst(String fullName) {
      int i = fullName.indexOf(" ");
      if (i > 0) {
         firstName = fullName.substring(0, i + 1);
         lastName = fullName.substring(i, fullName.length());
      } else {
         lastName = fullName;
         firstName = "";
      }
   }
}
[/code]


Ta dùng 1 factory ở đây để trả về đối tượng phù hợp căn cứ vào dữ liệu đầu vào:

[code lang="java"]
public class FactoryNamer {
   public Namer getNamer(String enterText) {
      if (enterText.indexOf(",") > 0) {
         return new LastFirst(enterText);
      }
      return new FirstFirst(enterText);
   }
}
[/code]
Nguồn: [http://javadevelopervietnam.blogspot.com/2010/10/factory-loai-creation-o-kho-trung-binh.html](http://javadevelopervietnam.blogspot.com/2010/10/factory-loai-creation-o-kho-trung-binh.html)
