---
author: admin
comments: true
date: 2011-08-27 07:51:49+00:00
layout: post
link: https://quachson.com/module-search-of-ibm-portal/
published: false
slug: module-search-of-ibm-portal
title: Module Search of IBM portal
wordpress_id: 597
categories:
- Portal
- Websphere Portal
tags:
- Portal
- Websphere Portal
---

- Bước 1: Vào Administration/ Search Administration/ Manage Search /Search Collections/ New Collection

![](http://quachson.files.wordpress.com/2011/08/newcollection1.png)
Tên thư mục sẽ tự động được tạo, nhớ là nên tạo mới. Chọn OK.

- Bước 2: Vào Quản trị tin / Site Areas / check vào Portal Nội Bộ VTA chọn Edit

![](http://quachson.files.wordpress.com/2011/08/editportalvta.png)

- Bước 3: map Search collection mình vừa mới tạo. Chọn OK

![](http://quachson.files.wordpress.com/2011/08/map_collection.png)
- Bước 4: remove portlet "Kết quả tìm kiếm của VTA nội bộ" của trang "tìm kiếm" ở manage pages và add portlet đó lại
Edit
![](http://quachson.files.wordpress.com/2011/08/manage_pages.png)

Delete portlet
![Delete portlet](http://quachson.files.wordpress.com/2011/08/delete_portlet.png)

Add the portlet
![](http://quachson.files.wordpress.com/2011/08/readd_portlet.png)

Bước 5: Cấu hình lại "Kết quả tìm kiếm của Viễn Thông A Nội bộ " portlet

![](http://quachson.files.wordpress.com/2011/08/configure_portlet.png)

![](http://quachson.files.wordpress.com/2011/08/edit_collectionlocation.png)'

- Chỉnh sửa phần hiển thị kết quả.
+ Chỉnh sửa file ViewResult.jspf trong D:IBMWebSpherewp_profileinstalledAppswpnode1PA_SIAPI.earSearchAndBrowse.warjsphtml
+ Mở file ManageSearch.jsp trong cùng thư mục, thêm 1 khoảng trắng và save lên để nó tự động deploy lại.




