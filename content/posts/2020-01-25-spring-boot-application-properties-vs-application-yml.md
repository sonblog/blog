---
author: hanson
comments: false
date: 2020-01-25 05:22:22+00:00
template: "post"
link: https://quachson.com/spring-boot-application-properties-vs-application-yml/
slug: spring-boot-application-properties-vs-application-yml
title: Spring boot | application.properties vs application.yml
wordpress_id: 2037
category: "Spring Boot"
tags:
- Java
- springboot
description: ".properties và .yml khác biệt nhau như thế nào ? Khi nào thì dùng properties, khi nào thì dùng yml."
---

#### **1/ .properties**
```md


# Mail server 
spring.mail.host=smtp.office365.com
spring.mail.port=587
spring.mail.username=admin@quachson.com
spring.mail.password=fkd%^865
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true

```
Cấu trúc của properties là không cấp bặc và dùng `=`

**Spring profiles**: phải tách ra mổi profile là 1 file properties: `local.properties`, `staging.properties`, `prod.properties`


#### **2/ .yml**
```md
spring:
  mail:
    host:smtp.office365.com
    port:587
    username=admin@quachson.com
    password=fkd%^865
    properties:
      mail:
        smtp:
          auth:true
          starttls:
            enable:true
```
Cấu trúc của yml thì có cấp bậc và dùng `:`

**Spring profiles**: cấu hình nhiều profiles trong 1 file `yml`

Khi dùng yml file thì chú ý, sẽ support @PropertySource để đọc file yml (Mình thì hem thích dùng chung 1 file sẽ làm file dài ra, khó đọc)

Nhiều người khuyên nên dùng yml, nào là thế này, nào là thế kia, chém gió theo lý thuyết, theo cộng đồng Cá nhân mình thì cái nào quen, thuận mắt thì dùng, vì 2 cách cũng như nhau mà thôi.

* * *

Dùng `@Value` cho biến và `@ConfigurationProperties` cho class để load toàn bộ properties hay load theo prefix như spring.mail. * để load value.
```md
@Value("${app.description: default value}}")
```
