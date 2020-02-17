---
author: admin
comments: true
date: 2011-04-22 07:41:45+00:00
template: "post"
link: https://quachson.com/what-is-classloader-in-java/
slug: what-is-classloader-in-java
title: What is ClassLoader in Java ?
wordpress_id: 502
categories:
- Java
tags:
- Java
---

** ClassLoader là gì?**




**
**




ClassLoader như tên gọi của nó là một thành phần của Máy Ảo Java được dùng để load các class java vào trong máy ảo để thực thi. Với cách hiểu như vậy, ta hoàn toàn có thể dự đoán cách thức mà ClassLoader hoạt động.





Để chạy 1 ứng dụng Java ta cần có các thư viện của Java là những file jar chứa trong jre/lib. Như vậy những Class chứa trong các thư viện này phải được nạp vào trước thông qua Bootstrap ClassLoader. Sau đó AppClassLoader sẽ nạp các Class của bản thân ứng dụng và các lớp chứa trong những gói jar mà ứng dụng cần đến ví dụ như logging.





Việc nạp một Class sẽ do ClassLoader đảm trách thông qua phương thức loadClass
