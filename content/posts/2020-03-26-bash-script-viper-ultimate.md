---
title: Bash Script - Mouse Viper Ultimate
date: 2020-03-26 10:30:00+00:00
template: "post"
draft: false
slug: "bash-mouse"
category: "Bash"
tags:
  - "Bash"
  - "DevOps"
description: "Nhớ ngày xưa hồi lớp 6, nhập môn tin học là học về MS-DOS về mấy lệnh command line như, dir, cd, md, rd. Bash script dùng cho Unix, Linux."
---
Bash script là những tập lệnh chạy trên Unix, Linux. Khi nào thì cần viết script
- Khi một câu lệnh dài, phải nhớ thì tạo script để lưu lại đỡ phải nhớ.
- Khi phải gõ một câu lệnh lặp đi lặp lại nhiều lần như là `git pull` mà một project có tới 20 cái repositories.

Mới tìm hiểu nên cũng chỉ tìm hiểu ở mức cơ bản.

Một file bash script sẽ có đuôi là `.sh`. Ví dụ hello.sh
```bash
#!/usr/bin/env bash
NAME="Quach"
echo "Hello $NAME!"
```
Và có quyền thực thi 
```sh
$ sudo chmod u+x ./hello.sh
```
Để thực thi `hello.sh`
```sh
$ ./hello.sh
```
#### Câu 1 #### 
Muốn dùng `git pull` cho tất cả thư mục thì viết script như thế nào.

**Ý tưởng:**
- Lấy tất cả các thư mục hiện có lưu vào trong mảng
- Duyệt qua mảng ta có được tên thư mục, thực hiện lệnh git pull  

**Thực hiện:**
Đặt tên file là pull_all.sh
```bash
for i in */; do
    echo
    date    
    echo "----git pull $i"    		
	git -C $i pull	
done
```

#### Câu 2 #### 
Muốn xem những threads java đang chạy là những threads nào để mình kill nó
```sh
$ jps -v
```
Muốn kill 1 threads thì làm sao 
```sh
$ kill -9 12123
```

#### Câu 3 #### 
Muốn xem những ports nào đang chạy 
```sh
$ lsof -nP -iTCP:$PORT | grep LISTEN
```

**Create a Symbolic Link**
```sh
$ ln -s /path/to/file /path/to/link
```

**Remove Link**
```sh
$ ls -l 
$ unlink link
```

**Check running postgres**
```sh
$ ps auxwww | grep postgres
```




Tham khảo:
- https://devhints.io/bash


Note **28-03-2020**: 
- Mới tậu 1 con chuột không dây Razer Viper Ultimate. Ngon, dùng bao phê.
- Mới thay pin, màn hình, bàn phím cho con Mac.
