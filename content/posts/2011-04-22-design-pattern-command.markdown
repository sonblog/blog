---
author: admin
comments: true
date: 2011-04-22 10:30:45+00:00
layout: post
link: https://quachson.com/design-pattern-command/
slug: design-pattern-command
title: 'Design Pattern: Command'
wordpress_id: 519
categories:
- Design Pattern
- Java
tags:
- Design Pattern
- Java
---

**Định nghĩa:**

Command nghĩa là ra lệnh. Sĩ quan chỉ huy gọi là commander, người này không làm mà chỉ ra lệnh cho người khác làm. Như vậy, phải có người nhận lệnh và thi hành lệnh.

Ra lệnh - cung cấp một class đóng gói những mệnh lệnh.

Người nhận mệnh lệnh cần phân biệt những interface nào để thực hiện đúng mệnh lệnh.

Bây giờ ta lấy ví dụ sau. Bóng đèn Light có 2 phương thức switchOn và switchOff.

    
    [code lang="java"]
    
    public class Light {
         void switchOn() {
              System.out.println("Switch light on");
         }
    
         void switchOff() {
              System.out.println("Switch light off");
         }
    }
    
    [/code]


Tuy vậy, để giống trong quân đội, ta làm 1 interface tên là Command không trực tiếp tắt bật đèn mà chỉ ra lệnh cho bóng đèn bật tắt.

    
    [code lang="java"]
    
    interface Command(){
         void execute();
    }
    
    [/code]


Ta hiện thực interface này bằng 2 class: CommandOff và CommandOn

    
    [code lang="java"]
    public class CommandOff implements Command {
         Light light;
         public CommandOff(Light light) {
              this.light = light;
         }
    
         @Override
         public void execute() {
              light.switchOff();
         }
    }
    [/code]



    
    [code lang="java"]
    public class CommandOn() {
         Light light;
         public CommandOn(Light light) {
              this.light = light;
         }
    
         @Override
         public void execute(){
              light.switchOn();
         }
    }
    [/code]


Bây giờ đã đóng gói các command này vào trong 1 bộ điều khiển gọi là Remote Control

    
    [code lang="java"]
    public class RemoteControl {
       private Command command;
       public setCommand(Command command){
          this.command = command;
       }
       public void pressButton() {
          command.execute();
       }
    }
    [/code]


Sử dụng remote control này như sau:

    
    [code lang="java"]
    public static void main(String[] args) {
       RemoteControl rc = new RemoteControl();
       Light light = new Light();
       Command c1 = new CommandOff(light);
       Command c2 = new CommandOn(light);
       rc.setCommand(c1);
       rc.pressButton();
    
       rc.setCommand(c2);
       rc.pressButton();
    }
    [/code]


Như vậy, ta có thể truyền bất cứ command nào vào Remote control để yêu cầu thực hiện. Khi đó, yêu cầu thực hiện đã được đóng gói vào trong 1 object như mô tả trong GoF book:

_Encapsulate a request as an object, thereby letting you parameterize clients with different requests, queue or log requests, and support undoable operations_
