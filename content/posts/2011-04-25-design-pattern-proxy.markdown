---
author: admin
comments: true
date: 2011-04-25 16:48:02+00:00
layout: post
link: https://quachson.com/design-pattern-proxy/
slug: design-pattern-proxy
title: 'Design Pattern: Proxy'
wordpress_id: 556
categories:
- Design Pattern
- Java
tags:
- Design Pattern
- Java
---

Định nghĩa:

Proxy tiếng Anh có nghĩa là người được ủy nhiệm. Khi việc khởi tạo 1 đối tượng mất nhiều thời gian ví dụ như đọc file từ ổ đĩa hoặc load file từ Internet, chương trình sẽ tạo 1 file giả. Đến khi cần sử dụng thực sự file này thì lúc đó file có thể đã được load xong. Ví dụ như ở trình duyệt, khi load 1 trang web trình duyệt sẽ hiện các image holder trước sau đó mới lấp nội dung ảnh vào.
Xem xét ví dụ sau đây:
Ta có lớp trừu tượng Graphic với 2 phương thức load và draw. Lớp Image hiện thực lớp Graphic. Lớp ProxyImage cũng hiện thực lớp Graphic. Do load Image có thể mất nhiều thời gian nên ta tạo lớp ImageProxy để có sẵn đối tượng một cách nhanh chóng:

[code lang="java"]
abstract class Graphic {
public abstract void load();
   public abstract void draw();
}
[/code]
[code lang="java"]
public class Image extends Graphic {
   private String filename;
   public Image(String filename) {
      this.filename = filename;
      load();
   }

   public void draw() {
      System.out.println("Drawing...");
   }

   public void load() {
      System.out.println("Loading...");
   }
}
[/code]
[code lang="java"]
public class ProxyImage extends Graphic {
   private String filename;
   private Graphic image;

   public ProxyImage(String filename) {
      this.filename = filename;
   }

   public void draw() {
      if (image==null) image = new Image(filename);
      image.draw();
   }

   public void load() {}
}
[/code]
[code lang="java"]
public static void main(String[] args) {
   Graphic image1 = new ProxyImage("file1.jpg");
   Graphic image2 = new ProxyImage("file2.jpg");

   image1.draw();
   image2.draw();
}
[/code]
