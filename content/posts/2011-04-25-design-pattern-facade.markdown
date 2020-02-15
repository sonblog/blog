---
author: admin
comments: true
date: 2011-04-25 16:44:06+00:00
layout: post
link: https://quachson.com/design-pattern-facade/
slug: design-pattern-facade
title: 'Design Pattern: Facade'
wordpress_id: 554
categories:
- Design Pattern
- Java
tags:
- Design Pattern
- Java
---

**Định nghĩa:** Facade, đọc là fei sơ, có ý nghĩa như 1 bộ khung. Ví dụ như trong 1 máy tính sẽ có các bộ phận khác nhau như CPU, RAM, Harddrive. Khi bật nút power, các đối tượng như CPU, RAM, và Hard drive sẽ tự động thực hiện các công việc của mình.

[code lang="java"]

public class Computer {
   private CPU cpu;
   private RAM ram;
   private HardDrive hardDrive;

   public Computer() {
      cpu = new CPU();
      ram = new RAM();
      hardDrive = new HardDrive();
   }
   public void start() {
      cpu.boot();
      ram.load();
      hardDrive.read();
   }
}

public class CPU {
   void boot() {
      System.out.println("Booting CPU");
   }
}

public class RAM {
   void load() {
      System.out.println("Load memory from RAM");
   }
}
[/code]
