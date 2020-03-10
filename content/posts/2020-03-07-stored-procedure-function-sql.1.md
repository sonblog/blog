---
title: Stored procedure and function in SQL
date: 2020-03-07 12:30:00+00:00
template: "post"
draft: false
slug: "stored-procedure-function-sql"
category: "Database"
tags:
  - "Database"
description: "Stored procedure và function trong SQL là gì ? Những tiện ích và ứng dụng trong những trường hợp nào ?"
---
##**Stored procedure là gì ?**
Stored Procedures are pre-compiled objects which are compiled for the first time and its compiled format is saved, which executes (compiled code) whenever it is called.

Function sẽ được gọi trong Stored procedures và hỗ trợ 2 loại phổ biến là: Transact-SQL và PL/SQL.

Hai công ty độc quyền về T-SQL đó là Microsoft và Sybase cho nên Database của họ cũng dùng T-SQL.
T-SQL: SQL Server, Sybase
PL/SQL: Oracle, Postgres

**Ưu Điểm:**
- Giảm lượng truy xuất của ứng dụng lên database
- Tăng tốc hiệu xuất ứng dụng
- Code nằm ở database, nên nhiều ứng dụng có thể sử dụng chung

**Khuyết Điểm:**
- Ít developers biết viết ngôn ngữ này
- Khó để quản lý versions và debug
- Không thể portable sang những database khác như MySQL hay Microsoft SQL Server (T-SQL) vì nó dùng ngôn ngữ khác.


##**Function là gì ?**
A function is compiled and executed every time whenever it is called. A function must return a value and cannot modify the data received as parameters.

Hàm thì bắt buộc phải có giá trị trả về và không thể thay đổi tham số.

