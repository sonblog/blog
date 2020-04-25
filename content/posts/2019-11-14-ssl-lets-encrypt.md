---
author: hanson
comments: false
date: 2019-11-14 16:35:19+00:00
template: "post"
link: https://quachson.com/ssl-lets-encrypt/
slug: ssl-lets-encrypt
title: SSL Lets Encrypt with Beanstalk Elasticsearch Amazon
wordpress_id: 1632
category: "aws"
tags:
- aws
- beanstalk
- letsencrypt
- nodejs
- ssl
description: "Cài đặt SSL let's encrypy (free) cho một host linux là như thế nào ?"
---

**Ngữ cảnh:**
 	
  * Có 1 domain `staging.quachson.com` được đăng ký ở trang abc

 	
  * Có 1 instance beanstalk của amazon tên là `aabbcc-09-amazon.com` đang chạy nodejs (reactjs), cần cấu hình ssl (https) cho domain `staging.quachson.com chỏ vào`.

 	
  * Cấn https để test, thử nghiệm này nọ, ko có tính chất thương mại điện hay fintech này nọ nên nhu cầu dùng free ssl


**Cách làm:** 	
  * **Tạo SSH** 	
    * Tạo pair key 	
    * Add pair key vào beanstalk instance 	
    * Open port 22 cho SSH
 	
  * **Cấu hình ngnix, install letsencrypt** 	
    * Map domain port 80 	
    * Install cerbot. 	
    * Add cronjob 90 ngày.

**Chi Tiết:** 	
  * **Tạo SSH** 	
    * Tạo pair key: Services/ec2/NETWORK & SECURITY/ Key Pairs / Create Key Pair 	
       [![](https://quachson.com/wp-content/uploads/mlqflfsvzt-150x150.png)](https://quachson.com/wp-content/uploads/mlqflfsvzt.png) 	
      * Sau khi tạo pair key xong, key sẽ được download về, mất key phải tạo key mới, không thể download lại	
    * Add pair key vào beanstalk instance: Services/elasticbeanstalk/ chọn instance / Configuration / Security / Modify 	
       [![](https://quachson.com/wp-content/uploads/gettingstarted-dashboard-300x161.png)](https://quachson.com/wp-content/uploads/gettingstarted-dashboard.png) 	
       [![](https://quachson.com/wp-content/uploads/aeb-env-config-security-page-300x131.png)](https://quachson.com/wp-content/uploads/aeb-env-config-security-page.png) 	
    * Open port 22 cho SSH: Services/ec2/Security Groups/ chọn group / Inbound / Edit 	
       [![](https://quachson.com/wp-content/uploads/ztzcpcxhdb.png)](https://quachson.com/ztzcpcxhdb/) 	
       [![](https://quachson.com/wp-content/uploads/wxygtxgutf.png)](https://quachson.com/wxygtxgutf/) 	
       Chọn connect, không phải image vì hình lấy trên net. 	
       [![](https://quachson.com/wp-content/uploads/tkv-ec2-create-ami-menu2.png)](https://quachson.com/ssl-lets-encrypt-with-beanstalk-elasticsearch-amazon-nodejs/tkv-ec2-create-ami-menu2/) 	
       [![](https://quachson.com/wp-content/uploads/node-connection.png)](https://quachson.com/ssl-lets-encrypt-with-beanstalk-elasticsearch-amazon-nodejs/node-connection/)

      * Nếu dùng `macOS` hay `ubuntu` thì cần `chmod 400`, nếu windows thì khỏi.
 	
  * **Cấu hình ngnix, install letsencrypt** 	
    * From domain staging.quachson.com --> dns record type: A tới IP host. 	
    * From hosting: Maping domain với port 80, tạo mới file: allow-ssl-domain.config, copy vào /etc/nginx/conf.d/elastic-beanstalk

```md
server {
listen 80 default_server;
listen [::]:80 default_server;
root /var/www/html;
server_name staging.quachson.com;
}
```

* Install certbot and ssl 	
```bash
sudo mkdir -p /opt/certbot 	
sudo wget https://dl.eff.org/certbot-auto -O /opt/certbot/certbot-auto;sudo chmod a+x /opt/certbot/certbot-auto
sudo /opt/certbot/certbot-auto certonly --debug --non-interactive --email son.quach.aavn@gmail.com --agree-tos --domains staging.quachson.com --keep-until-expiring --webroot -w /var/app/current/public
sudo ln -sf /etc/letsencrypt/live/staging.quachson.com /etc/letsencrypt/live/ebcert
```
Tạo ssl key cho server tomcat muốn run https
```bash
openssl pkcs12 -export -in fullchain.pem -inkey privkey.pem -out keystore.p12 -name tomcat -CAfile chain.pem -caname root
```
Sau khi install ssl xong, xoá allow-ssl-domain.config vì phải config forward port 80 sang https và SSL chỏ vào file key
 	
* Configuration SSL 	
  * Tạo folder .ebextensions, hỗ trợ .conf và .yaml 	
  * Cấu trúc thư mục cho react project 	

[![](https://quachson.com/wp-content/uploads/structure_react.png)](https://quachson.com/structure_react/)

  * Cấu trúc thư mục cho spring boot (Java SE), zip folder  .ebextensions  và  file  example-api-2.3.jar  ->  deployment.zip (tên gì cũng dc)
 	
[![](https://quachson.com/wp-content/uploads/java-folder-structure.png)](https://quachson.com/ssl-lets-encrypt-with-beanstalk-elasticsearch-amazon-nodejs/java-folder-structure/)
	
* Cấu hình cho nginx, nên upload config file lên server rồi restart nginx để test, test thành công thì mới copy vào .ebextensions, upload deployment.zip lên test lại.

**Một vài lưu ý:** 	
  * /etc/nginx 	
  * /etc/letsencrypt/live 	
  * /var/www/html 	
```bash
sudo service nginx start | stop | restart 	
```   
  * Command check java heap (bytes)
```bash 	
java -XX:+PrintFlagsFinal {your-java-program} | grep HeapSize
```
```md    
        uintx InitialHeapSize                          := 536870912       {product}
        uintx MaxHeapSize                              := 1073741824      {product}
        uintx PermSize                                 := 67108864        {pd product}  
        uintx MaxPermSize                              := 134217728       {pd product}  
        intx ThreadStackSize                          := 512             {pd product}
```
 	
  * Nếu bị lỗi **413 Request Entity Too Large - File Upload Issue **thì cách fix như sau: tìm **/etc/nginx/nginx.conf**
```md    
    http {
        client_max_body_size 100M;
    }
```

nhớ là M, dùng MB hay Mb sẽ hem chạy đâu.

----

Thảm khảo:
https://gist.github.com/dborin/dd501b28967d3784fa646534dbea6ffa
https://gist.github.com/tony-gutierrez/198988c34e020af0192bab543d35a62a
https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/java-se-nginx.html
