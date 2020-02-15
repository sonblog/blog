---
author: admin
comments: true
date: 2012-06-10 04:57:39+00:00
layout: post
link: https://quachson.com/10-things-to-do-after-installing-ubuntu-12-04/
slug: 10-things-to-do-after-installing-ubuntu-12-04
title: 10 Things to Do After Installing Ubuntu 12.04
wordpress_id: 780
categories:
- Ubuntu
tags:
- Ubuntu
---

1/ Install cinnanmon 1.4

Open terminal ( Ctrl + Alt + t )

[code]
$ sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
$ sudo apt-get update
$ sudo apt-get install cinnamon
[/code]

- restart
![](http://quachson.files.wordpress.com/2012/06/ubuntu-login.png)
![](http://quachson.files.wordpress.com/2012/06/login-cinnamon.png)

2/ Install ibus-unikey for type vietnamese

[code]
$ sudo apt-get install ibus-unikey
$ im-switch -s ibus
[/code]

- Logout then login.

- Applications / System Tools / System Settings / Language Support /Keyboard input method system: Ibus

- Application / System Tools / Preferences / Keyboard Input Method

++ General: checked all checkbox

++ Input method: Add Vietnamese - Unikey.

Use Ctrl + space for active / deactive

3/ Install Meld Diff Viewer from Ubuntu Software Centre

Compare and Meld your files.

4/ Install Synaptic Package Manager from Ubuntu Software Centre

5/ Install ant, maven end jdk 1.6.23

[code]

$ sudo apt-get install ant1.7

$ sudo apt-get install maven2

[/code]
