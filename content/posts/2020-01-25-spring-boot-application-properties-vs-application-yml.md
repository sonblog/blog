---
author: hanson
comments: false
date: 2020-01-25 05:22:22+00:00
template: "post"
link: https://quachson.com/spring-boot-application-properties-vs-application-yml/
slug: spring-boot-application-properties-vs-application-yml
title: Spring boot | application.properties vs application.yml
wordpress_id: 2037
categories:
- Java
- springboot
tags:
- Java
- springboot
---

#### **1/ .properties**



Cấu trúc của properties là không cấp bặc và dùng `=`

Spring profiles: phải tách ra mổi profile là 1 file properties: local.properties, staging.properties, prod.properties


#### **2/ .yml**




Cấu trúc của yml thì có cấp bậc và dùng `:`

Spring profiles: cấu hình nhiều profiles trong 1 file yml

Khi dùng yml file thì chú ý, sẽ support @PropertySource để đọc file yml (Mình thì hem thích dùng chung 1 file sẽ làm file dài ra, khó đọc)

Nhiều người khuyên nên dùng yml, nào là thế này, nào là thế kia, chém gió theo lý thuyết, theo cộng đồng Cá nhân mình thì cái nào quen, thuận mắt thì dùng, vì 2 cách cũng như nhau mà thôi.



* * *



Dùng @Value và @ConfigurationProerties để load value.

@Value("${app.description: default value}}")
