---
title: Tìm hiểu thêm về JWT
date: 2020-03-08 12:30:00+00:00
template: "post"
draft: false
slug: "jwt-design"
category: "Design System"
tags:
  - "Design System"
description: "Khi làm việc với JWT gặp phải rất nhiều vấn đề như: Thời gian hết hạn nên để ngắn hay để dài, ..."
---
##**Câu hỏi**
Khi làm việc về JWT thì gặp một số câu hỏi như sau:
1. Thời gian hết hạn của JWT là ngắn hay là dài, thấy login vào facebook 1 lần và dùng mãi mãi luôn, ít khi nào thấy hết hạn, nếu để ngắn hạn thì phải dùng refresh token và những ưu điểm gì ?
2. Có nên lưu token vào database hay không, nếu lưu thì mỗi lần kiểm tra phải truy xuất vào database thời gian sẽ chậm. JWT dã hỗ trợ kiểm tra token ?
3. 

##**Giải quyết**
#### Câu 1 #### 
Thời gian hết hạn của JWT là ngắn hay là dài, thấy login vào facebook 1 lần và dùng mãi mãi luôn, ít khi nào thấy hết hạn, nếu để ngắn hạn thì phải dùng refresh token và những ưu điểm gì ? 

Ngắn hay dài thì tuỳ thuộc vào người thiết kế ra nó thiên về chức năng hay là bảo mật 
  * Nếu thiên về bảo mật, dùng refresh token nhưng sẽ làm cho ứng dụng dễ gây phiền hà người sử dụng 
  * Nếu thiên về chức năng, ứng dụng sẽ dễ bị tấn công, nếu bạn bị tấn công kiểu middle man thì dùng refresh token cũng chết như thường thôi, nên nếu có dùng public wifi, máy cty hay công cộng thì nhớ logout hệ thống sau khi sử dụng.

#### Câu 2 #### 
Có nên lưu token vào database hay không, nếu lưu thì mỗi lần kiểm tra phải truy xuất vào database thời gian sẽ chậm. JWT dã hỗ trợ kiểm tra token ?
