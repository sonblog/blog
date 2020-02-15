---
author: admin
comments: true
date: 2011-04-11 04:07:55+00:00
layout: post
link: https://quachson.com/different-get-and-load-in-hibernate/
slug: different-get-and-load-in-hibernate
title: Different Get and Load in Hibernate
wordpress_id: 480
categories:
- Hibernate
- Java
tags:
- Hibernate
- Java
---

[code lang="java"]

public Account loadAccount(int id) {
return (Account) sessionFactory.getCurrentSession().get(Account.class,id);
}

[/code]



[code lang="java"]

public Account loadAccount(int id) {
 return (Account) sessionFactory.getCurrentSession().load(Account.class,id);
}

[/code]

Get: mỗi lần thực thi sẽ truy xuất vào database. Nếu không tìm thấy thì _return nul_l

Load: không truy xuất vào database mà tìm kiểm những Object persistent sau đó _return proxy_ nên truy xuất sẽ nhanh hơn GET,  nếu không tìm thấy dữ liệu thì sẽ throw Hibernate Exception (ObjectNotFoundException). Nhưng để kiểm tra đối tượng có tồn tại hay không thì nên dùng GET, như check Account exist or not.
