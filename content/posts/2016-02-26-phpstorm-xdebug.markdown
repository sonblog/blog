---
author: quachson
comments: true
date: 2016-02-26 02:23:07+00:00
template: "post"
link: https://quachson.com/phpstorm-xdebug/
slug: phpstorm-xdebug
title: PhpStorm & XDEBUG
wordpress_id: 946
categories:
- PHP
tags:
- PHP
- phpstorm
- XDEBUG
---


	
  1. **Environment**:

	
    * Phpstorm 10

	
    * php-cgi: sudo apt-get install php-cgi




	
  2. **Setup:**



	
    * File/Settings/Languages & Frameworks/PHP


![Screenshot from 2016-02-25 14:40:22](https://quachson.files.wordpress.com/2016/02/screenshot-from-2016-02-25-144022.png)

![Screenshot from 2016-02-25 14:41:34](https://quachson.files.wordpress.com/2016/02/screenshot-from-2016-02-25-144134.png)

![Screenshot from 2016-02-25 14:42:27](https://quachson.files.wordpress.com/2016/02/screenshot-from-2016-02-25-144227.png)

[xdebug]
zend_extension="/usr/lib/php5/20121212/xdebug.so"
xdebug.remote_enable=true
xdebug.remote_port=9000
xdebug.profiler_enable=1
xdebug.remote_host=localhost
xdebug.profiler_output_dir="/home/quachson/tmp/xdebug"
xdebug.max_nesting_level=1000

![Screenshot from 2016-02-25 17:05:03](https://quachson.files.wordpress.com/2016/02/screenshot-from-2016-02-25-170503.png)

![Screenshot from 2016-02-25 14:44:43](https://quachson.files.wordpress.com/2016/02/screenshot-from-2016-02-25-144443.png)

![Screenshot from 2016-02-25 14:44:43](https://quachson.files.wordpress.com/2016/02/screenshot-from-2016-02-25-144443.png)



	
  3. **Install xdebug for chrome:**


![Screenshot from 2016-02-25 17:02:01](https://quachson.files.wordpress.com/2016/02/screenshot-from-2016-02-25-170201.png)


