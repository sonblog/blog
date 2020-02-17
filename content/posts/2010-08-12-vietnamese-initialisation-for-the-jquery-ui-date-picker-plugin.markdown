---
author: admin
comments: true
date: 2010-08-12 02:12:20+00:00
template: "post"
link: https://quachson.com/vietnamese-initialisation-for-the-jquery-ui-date-picker-plugin/
slug: vietnamese-initialisation-for-the-jquery-ui-date-picker-plugin
title: Vietnamese initialisation for the jQuery UI date picker plugin
wordpress_id: 298
categories:
- Javascript
- JQuery
tags:
- javascript
- jQuery
---

`
1
2	$(function() {
3
4	        $.datepicker.regional['vi'] = {
5	                closeText: 'Đóng',
6	                prevText: '<Trước',
7	                nextText: 'Tiếp>',
8	                currentText: 'Hôm nay',
9	                monthNames: ['Tháng Một', 'Tháng Hai', 'Tháng Ba', 'Tháng Tư', 'Tháng Năm', 'Tháng Sáu',
10	                'Tháng Bảy', 'Tháng Tám', 'Tháng Chín', 'Tháng Mười', 'Tháng Mười Một', 'Tháng Mười Hai'],
11	                monthNamesShort: ['Tháng 1', 'Tháng 2', 'Tháng 3', 'Tháng 4', 'Tháng 5', 'Tháng 6',
12	                'Tháng 7', 'Tháng 8', 'Tháng 9', 'Tháng 10', 'Tháng 11', 'Tháng 12'],
13	                dayNames: ['Chủ Nhật', 'Thứ Hai', 'Thứ Ba', 'Thứ Tư', 'Thứ Năm', 'Thứ Sáu', 'Thứ Bảy'],
14	                dayNamesShort: ['CN', 'T2', 'T3', 'T4', 'T5', 'T6', 'T7'],
15	                dayNamesMin: ['CN', 'T2', 'T3', 'T4', 'T5', 'T6', 'T7'],
16	                weekHeader: 'Tu',
17	                dateFormat: 'dd/mm/yy',
18	                firstDay: 0,
19	                isRTL: false,
20	                showMonthAfterYear: false,
21	                yearSuffix: ''};
22	        $.datepicker.setDefaults($.datepicker.regional['vi']);
23            $("#datepicker").datepicker();
24	});
25    
26 
27    
`

Source: [http://project.websitebaker2.org/browser/branches/2.8.x/wb/include/jquery/i18n/jquery.ui.datepicker-vi.js?rev=1332](http://project.websitebaker2.org/browser/branches/2.8.x/wb/include/jquery/i18n/jquery.ui.datepicker-vi.js?rev=1332)
