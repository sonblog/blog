---
title: Multi-tenancy là gì
date: 2020-03-06 22:30:00+00:00
template: "post"
draft: false
slug: "multi-tencancy-la-gi"
category: "Design System"
tags:
  - "Java"
  - "Design System"
description: "Multi-Tenancy là gì, cách thiết kế hệ thống cho multi-tenancy như thế nào, cách tổ chức database ra sao, cách bảo mật dữ liệu như thế nào để user của cty này không thế thấy dữ liệu của công ty khác, ..."
---
##**Multi-tenancy là gì ?**
Multi-Tenancy is a single instance of software that serves multiple customers privately.

Hiểu đơn giản Multi-Tenancy là một hệ thống web application có nhiều khách hàng cùng sử dụng nhưng dữ liệu giữa các khách hàng hoàn tập độc lập, khách hàng này không thể truy cập vào dữ liệu của khách hàng kia.

Một vài ví dụ như là: 
Hệ thống chấm công, trả lương hay khai báo thuế cho tổng công ty có nhiều công ty con, công ty con có nhiều nhân viên và khách hàng, dữ liệu là độc lập, CEO, nhân viên trong hội đồng quản trị có thể thấy dữ liệu của tất cả công ty con, còn nhân viên trong cty con thì không được phép thấy dự liệu của những công ty khác nhưng dùng chung 1 hệ thống (website)

##**Thiết kế database như thế nào ?**
###Cách 1:
Cho tất cả data vào chung 1 table, thêm cột company_id làm khoá ngoại để biết users, data thuộc công ty nào.

**Ưu Điểm:** Dễ thực hiện

**Khuyết Điêm:**
  * Chung 1 table, dữ liệu sẽ nhanh chóng phìng ra to
  * Dễ sai xót nếu query nhầm company_id hay sai  

###Cách 2:
Dùng schema, mỗi 1 công ty là 1 schema (chứa nhiều tables, trong postgres có hỗ trợ)

###Cách 3:
Mỗi công ty là 1 database độc lập 


Tham khảo: 
* 

