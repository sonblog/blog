---
author: admin
comments: true
date: 2012-02-11 06:02:57+00:00
layout: post
link: https://quachson.com/how-to-create-template-for-wp/
published: false
slug: how-to-create-template-for-wp
title: How to create template for wp
wordpress_id: 752
categories:
- wp
tags:
- wp
---

1/ Cách tạo template trong wp
- Copy nguyên thư mục vào D:xampphtdocswordpresswp-contentthemes
- Tạo 3 file trong thư mục: D:xampphtdocswordpresswp-contentthemesnhakhoadaiviet
+ screenshot.png kích thước 300x255
+ index.php giống file index.html (template)
+ style.css ( đã có sẵn khi tạo template)
- Vào phần admin của wp, Appearance/Themes sẽ thấy xuất hiện hình ảnh của template. Ta active
- Ra ngoài trang wp, refresh lại ta sẽ thấy chưa có hình ảnh, CSS và menu header của wp
- Edit index.php
+ header.php
+ <?php bloginfo('template_url');?>
+ footer.php

2/ Một số thuộc tính của wp
- bloginfo( 'name' ); - title, wp/admin/settings/general
- <html <?php language_attributes(); ?>>
- <meta charset="<?php bloginfo( 'charset' ); ?>" />
- <link rel="stylesheet" type="text/css" media="all" href="<?php bloginfo( 'stylesheet_url' ); ?>" /> - link tới file style.css
- <link rel="pingback" href="<?php bloginfo( 'pingback_url' ); ?>" /> hỗ trợ SEO, post bài, sau vài giây là search trên google có thể thấy
- <script type='text/javascript' src='<?php bloginfo('template_url');?>/js/fadeimages.js'></script> đường dẫn tới template
- wp_head(); wp_footer(); hiển thị menu ở top trang home
- wp_list_pages('title_li=') hiển thị danh sách các trang theo chiều ngang: abc des def deg

tham khảo thêm ở trang:` http://codex.wordpress.org/
`
