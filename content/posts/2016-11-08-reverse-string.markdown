---
author: quachson
comments: true
date: 2016-11-08 15:51:10+00:00
template: "post"
link: https://quachson.com/reverse-string/
slug: reverse-string
title: Reverse String (Đảo chuỗi)
wordpress_id: 1038
category: "Code Shop"
tags:
- Java
- "Code Shop"
description: "Trong thực tế thì dùng thư viện StringBuffer().reverse() là xong nhưng trong giải thuật thì cần bàn luận về thuật toán."
---

Bài toán đảo chuổi thực tế

```java
public String reverseCharacters(String value) {
    return new StringBuffer(value).reverse();
}
```
```md
Input: 12345
output: 54321
```

Bài toán trong giải thuật nếu input lá số thì .

```java
public int reverseCharacters(int n) {
    int reverse = 0;
    while (n != 0) {
        reverse = reverse * 10;
        reverse = reverse + n%10;
        n = n/10;
    }
    return reverse;
}
```