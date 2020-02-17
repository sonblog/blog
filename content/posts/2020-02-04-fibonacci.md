---
title: Fibonacci
date: 2020-08-19 22:40:32+00:00
template: "post"
draft: false
slug: "fibonacci"
category: "Code Shop"
tags:
  - "Code Shop"
description: "Fibonacci là gì ? Công thức tính fibonacci như thế nào ? Áp dụng vào Java viết thông thường hay đệ quy thì viết như thế nào ?"
---
Dãy Fibonacci là dãy vô hạn các số tự nhiên bắt đầu bằng hai phần tử 0 và 1 hoặc 1 và 1, các phần tử sau đó được thiết lập theo quy tắc mỗi phần tử luôn bằng tổng hai phần tử trước nó. Công thức truy hồi của dãy Fibonacci là:

![Công thức Fibonacci](https://github.com/sonblog/blog/blob/master/static/media/fibonacci.svg "Công thức fibonacci")

f(0) = 0

Dãy số fibonacci: 0, 1, 1, 2, 3, 5, 8, **13.** Con số 13 = 8 + 5 (tổng 2 số trước)
```md
n: f(n)
0: 0
1: 1
2: 1
3: 2
4: 3
5: 5
6: 8   
7: 13 = 8 + 5
```

Cách viết đệ quy
```java
  public static long fibonacci(int n) {
    if (n <= 1) return n;
    return fibonacci(n-1) + fibonacci(n-2);
}
```

Cách viết không đệ quy
```java
public static int fibonacci(int n) {		
	int first = 0;
	int next = 1;
	for (int i=1; i <= n; ++i ) {
		int sum = first + next;
		first = next;
		next = sum;
	}		
	return first;
}
```
