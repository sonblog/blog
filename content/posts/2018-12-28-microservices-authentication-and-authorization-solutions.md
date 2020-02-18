---
author: hanson
comments: false
date: 2018-12-28 02:15:22+00:00
template: "post"
link: https://quachson.com/microservices-authentication-and-authorization-solutions/
slug: microservices-authentication-and-authorization-solutions
title: Microservices Authentication and Authorization Solutions
wordpress_id: 1538
category: "Java"
---
  * Authentication: who you are.
  * Authorization: what you can do.
## **1. Distributed Session Management**
### **1.1. Sticky session**:
Bảo đảm rằng tất cả requests của users sẽ trên cùng server giống như request ban đầu, sẽ phụ thuộc là load balancer. Session sẽ bị mất nếu requests không đi đúng servers ban đầu có chứ session vì bất kỳ lý do nào đó như server chứa session đó bị chết, bị quá tải...nên phải đổi servers khác.
### **1.2. Session replication**:
Nhân rộng session, mỗi instance đều có session giống nhau và đồng bộ hoá thông qua network nên có thể gây tắt nghẽn băng thông. Mỗi khi có 1 session được thay đổi thì phải thay đổi đồng bộ lại trên tất cả instance. Cồng kềnh, nặng nề, tốn nhiều chi phí
### **1.3. Centralized session storage**:
Xây dựng 1 hệ thống lưu trữ session độc lập riêng. Tất cả microservice sẽ truy xuất vào hệ thống này để lấy session. Nhược điểm là cần phải có giao thức bảo mật giữa các microservice và Distribution Session Store.

## **2. Client Token**:

## **3. Single sign-on**:
chỉ cần login 1 lần là có thể dùng cho mọi hệ thống. Dùng cách nào cũng được miễn thoả mãn khái niệm này là dc. Cách hay dùng là token, JWT, ....
## **4. Client Token with API Gateway**:
Gateway giống cơ chế 1 cửa, chỉ cần biết và gọi 1 API Gateway, đằng sau cánh cửa đó sẽ gọi hàng chục APIs khác để trả về kết quả cuối cùng. Nên user sẽ không biết đến những APIs phía sau cánh cửa.

## **5. Third-party application access**
### **5.1. API Token**:
Được add vào header của requests - Dùng token để truy xuất vào hệ thống thay thế cho username/password, nếu có lộ token thì cũng không biết password để thay đổi. - Những hệ thống hay dùng API Token: Github, Bitbucket, Gitlab, Facebook, Twitter..
### **5.2. OAuth2**:
grant authorization, trao quyền truy xuất, trao access token.

A: Tao muốn truy xuất vào facebook của mày để lấy thông tin profile, contacts dc hem.
B: OK, để tao login vào facebook lấy access token cho mày, có token này thì mày có thể vào nhưng sẽ không thay đổi được password. Tao cho mày vào 1 tuần tao sẽ remove token này.

OAuth authentication process

## **6. Mutual Authentication**:

Xác thực lẫn nhau. Trước hết server chứa tài nguyên kiểm tra “giấy phép truy cập” của client, sau đó client kiểm tra lại “giấy phép cấp tài nguyên” của server. Điều này giống như khi bạn giao dịch với bank thì bạn cần kiểm tra xem server bank đó là thật hay không, hay là 1 cái bẫy của hacker giăng ra và ngược lại server bank sẽ kiểm tra bạn.

**OAuth** và **JWT** được sử dụng nhiều và phổ biến nhất bởi vì nó nhẹ và gọn và không cần transaction. Dĩ nhiên là tuỳ vào trường hợp mà nên áp dụng loại nào cho phù hợp.
