---
author: admin
comments: true
date: 2011-12-18 15:56:08+00:00
template: "post"
link: https://quachson.com/enable-browser-for-storm-bb-9530/
published: false
slug: enable-browser-for-storm-bb-9530
title: Enable Browser for Storm (BB 9530)
wordpress_id: 706
categories:
- BB Storm 9530
tags:
- BB Storm 9530
---

1> Bảo đảm là ứng dụng Browser được cài đặt trong máy. Để kiểm tra thì chạy Loader.exe của OS đã setup vào PC ( xem lại ở những bài trước đã viết ). Hệ điều hành của BlackBerry hiện đang dùng là v5.0.0.328.

2> Để enable Browser ta làm như sau:

- vào Option / Advanced Options / Service Book

- Show Keyboard và nhấn
!?123  4?2?
thì sẽ thấy hiện ra thông báo, còn không thấy gì hết là chưa làm dc.

3> Vào BlackBerry Desktop Software / Delete data / xóa Service book

4> Vào Restore trong BBD, restore , browse tới nơi chứa file Browser_via_TCP_all_network_beta_V1.1.ipd để cài đặt lại service book

5> Sau khi cài đặt xong thì icon Browser sẽ xuất hiện. Mở Browser lên thử, nếu có thông báo lỗi là chưa cấu hình thì vào Option /  Advanced Options / Browser / chọn Browser.

Lúc này đã hoàn tất quá trình cài đặt Browser cho Storm, để duyệt được web thì cellphone của bạn phải có đăng kỳ GPRS hay 3G.

Cách cấu hình GPRS như sau:

Option / Advanced Options /  TCP/IP

GPRS cho Mobi:

APN Settings Enabled - checked
APN: m-wap

APN Authentication Enabled
Username for APN:   mms
Password for APN:     mms

Sau đây là thông số cài đặt GPRS của Vinaphone, MobiFone, Viettel, VietNam Mobile, BeeLine.
<table cellpadding="0" cellspacing="1" border="0" >
<tbody >
<tr >

<td width="16%" align="center" height="25" >Thông số
</td>

<td width="16%" align="center" >Vinaphone
</td>

<td width="16%" align="center" >MobiFone
</td>

<td width="16%" align="center" >Viettel
</td>

<td width="16%" align="center" >VietNam Mobile
</td>

<td width="16%" align="center" >BeeLine
</td>
</tr>
<tr >

<td align="left" height="25" >Homepage
</td>

<td align="left" height="25" >Bất kỳ
</td>

<td align="left" height="25" >Bất kỳ
</td>

<td align="left" height="25" >Bất kỳ
</td>

<td align="left" height="25" >Bất kỳ
</td>

<td align="left" height="25" >Bất kỳ
</td>
</tr>
<tr >

<td align="left" height="25" >Security
</td>

<td align="left" height="25" >Off
</td>

<td align="left" height="25" >Off
</td>

<td align="left" height="25" >Off
</td>

<td align="left" height="25" >Off
</td>

<td align="left" height="25" >Off
</td>
</tr>
<tr >

<td align="left" height="25" >IP address
</td>

<td align="left" height="25" >10.1.10.46
</td>

<td align="left" height="25" >203.162.21.107
</td>

<td align="left" height="25" >192.168.233.10
</td>

<td align="left" height="25" >10.10.128.44
</td>

<td align="left" height="25" ><không nhập>
</td>
</tr>
<tr >

<td align="left" height="25" >Port
</td>

<td align="left" height="25" >8000 hoặc 9201
</td>

<td align="left" height="25" >8080 hoặc 9201
</td>

<td align="left" height="25" >8080 hoặc 9201
</td>

<td align="left" height="25" >8080
</td>

<td align="left" height="25" >8080 hoặc 9201
</td>
</tr>
<tr >

<td align="left" height="25" >Proxy
</td>

<td align="left" height="25" >Enable
</td>

<td align="left" height="25" >Enable
</td>

<td align="left" height="25" >Enable
</td>

<td align="left" height="25" >Enable
</td>

<td align="left" height="25" >Enable
</td>
</tr>
<tr >

<td align="left" height="25" >Bearer
</td>

<td align="left" height="25" >GPRS
</td>

<td align="left" height="25" >GPRS
</td>

<td align="left" height="25" >GPRS
</td>

<td align="left" height="25" >GPRS
</td>

<td align="left" height="25" >GPRS
</td>
</tr>
<tr >

<td align="left" height="25" >Username
</td>

<td align="left" height="25" >mms
</td>

<td align="left" height="25" >mms
</td>

<td align="left" height="25" ><không nhập>
</td>

<td align="left" height="25" ><không nhập>
</td>

<td align="left" height="25" ><không nhập>
</td>
</tr>
<tr >

<td align="left" height="25" >Password
</td>

<td align="left" height="25" >mms
</td>

<td align="left" height="25" >mms
</td>

<td align="left" height="25" ><không nhập>
</td>

<td align="left" height="25" ><không nhập>
</td>

<td align="left" height="25" ><không nhập>
</td>
</tr>
<tr >

<td align="left" height="25" >APN/GPRS access point
</td>

<td align="left" height="25" >m3-world
</td>

<td align="left" height="25" >m-wap
</td>

<td align="left" height="25" >v-wap hoặc v-internet
</td>

<td align="left" height="25" >wap hoặc internet
</td>

<td align="left" height="25" >internet
</td>
</tr>
</tbody>
</table>
Cấu hình cho phone, dĩ nhiên là SIM của bạn cũng đã được đăng ký GPRS.
