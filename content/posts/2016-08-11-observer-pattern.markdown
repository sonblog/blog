---
author: quachson
comments: true
date: 2016-08-11 07:24:35+00:00
template: "post"
link: https://quachson.com/observer-pattern/
slug: observer-pattern
title: Observer Pattern
wordpress_id: 1260
categories:
- Design Pattern
tags:
- Behavioral Patterns
- Design Pattern
- Java
---

Observer: An object notifies other object(s) if it changes

ngữ cảnh: được sử dụng khi nhấn subscriber 1 channel youtube nào đó, email của bạn sẽ được add vào List. Mỗi khi có video mới thì sẽ gởi email thông báo đến bạn.

Cách hiện thực: là tạo List<Interface> lưu những email đó, mỗi khi có người nhấn subscriber thì sẽ add email người đó vào, mỗi khi channel có thêm 1 video thì sẽ send email.


[code lang="java"]
public class App {
public static void main(String[] args) {
Channel channel = new Channel();
channel.subscribe(new Client1());
channel.subscribe(new Client2());

channel.addVideo("new video");

}

}

public class client1 implements Observer {
@Override
public void update(Message message) {
sendEmail();
// bla bla bla
}

public void wantChange() {
super.notifyAll(new Message);
}
}

public class client1 implements Observer {
@Override
public void update(Message message) {
sendEmail();
// send money
// send like
}
}


public interface Observer {
public void update(Message message);

}

public class Channel {
private List<Observer> observers = new ArrayList<>();

public Channel() {
}

public void subscribe(Observer client) {
observers.add(client);
}

public void unsubscribe(Observer client) {
observers.remove(client);
}

public void addVideo(String video) {
// bla bla bla with message
notifyAll(message);
}

public void notifyAll(Message message) {
for (final client : observers) {
client.update(message);
}
}

}

[/code]
