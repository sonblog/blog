---
author: quachson
comments: true
date: 2016-02-25 02:59:02+00:00
template: "post"
link: https://quachson.com/php-xdebug/
slug: php-xdebug
title: PHP & XDEBUG
wordpress_id: 932
categories:
- PHP
tags:
- PHP
- XDEBUG
---


	
  * Environment: Ubuntu with LAMP (Apache, PHP, MySql)

	
  * Install xdebug:


[code language="bash"]
sudo apt-get install php5-dev php-pear
sudo apt-get install php5-xdebug
sudo php5enmod xdebug
sudo /etc/init.d/apache2 restart
[/code]



	
  * Find path xdebug.so


[code language="bash"]
find /usr/lib -name 'xdebug.so'
[/code]


<blockquote> /usr/lib/php5/20121212/xdebug.so</blockquote>





	
  * Find path php.ini


[code language="bash"]
find / -name 'php.ini'
[/code]


<blockquote>/etc/php5/apache2/php.ini</blockquote>





	
  * Add these lines into php.ini

    
    zend_extension=<span class="code-string">"</span><span class="code-string"><em>/usr/lib/php5/20121212/xdebug.so</em>"</span>
    xdebug.remote_enable=<span class="code-digit">1</span>
    xdebug.remote_handler=dbgp
    xdebug.remote_mode=req
    xdebug.remote_host=localhost
    xdebug.remote_port=<span class="code-digit">9000</span>




	
  * Restart apache


[code language="bash"]
sudo /etc/init.d/apache2 restart
[/code]

	
  * Check xdebug


Create phpinfo.php with content:

<?php

phpinfo();

?>

Install in local, a recommended configuration of php.ini

	
  * max_execution_time = 1000 ( timeout php execute)

	
  * memory_limit = 512M

	
  * post_max_size = 100M

	
  * upload_max_filesize = 100M







