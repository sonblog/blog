---
author: hanson
draft: false
date: 2018-01-05 14:31:24+00:00
template: "post"
link: https://quachson.com/nhung-nguyen-tac-co-ban-nhat-trong-java/
slug: nhung-nguyen-tac-co-ban-nhat-trong-java
title: Những nguyên tắc cơ bản nhất trong Java
wordpress_id: 1446
category: "Java"
tags: 
- "Java"
description: "Cách viết code java như thế nào là hiệu quả"
---

1. Khi `constructor()` có quá nhiều parameters thì nên dùng `Builder pattern`. (vì quá đơn giản nên ko cần ví dụ link tham khảo)

2. Nên dùng `try-with-resources` của java 7 hơn là `try-finally`

```java
// Không nên:
static String firstLineOfFile(String path) throws IOException {
   BufferedReader br = new BufferedReader(new FileReader(path));
   try {
      return br.readLine();
   } finally {
      br.close();
   }
}
```
```java
// Nên:
static String firstLineOfFile(String path) throws IOException {
   try (BufferedReader br = new BufferedReader(new FileReader(path))) {
      return br.readLine();
   }
}
```

```java
// Không Nên:
static void copy(String src, String dst) throws IOException {
   InputStream in = new FileInputStream(src);
   try {
      OutputStream out = new FileOutputStream(dst);
      try {
         byte[] buf = new byte[BUFFER_SIZE];
         int n;
         while ((n = in.read(buf)) = 0)
            out.write(buf, 0, n);
      } finally {
         out.close();
      }
   } finally {
      in.close();
   }
 }
```

```java
// Nên:
static void copy(String src, String dst) throws IOException { 
   try (InputStream in = new FileInputStream(src); 
        OutputStream out = new FileOutputStream(dst)) { 
      byte[] buf = new byte[BUFFER_SIZE]; 
      int n; 
      while ((n = in.read(buf)) = 0)
         out.write(buf, 0, n); 
   } 
}
```

3. Nếu có override `equals()` thì phải luôn luôn override `hashCode()` : mình thường hay dùng Eclipse generate code cho hashCode method, review lại cần thì edit lại một ít.

4. Luôn luôn override `toString()` cho bean hay `POJO`, vì mỗi khi ghi log hay debug dễ dàng hơn, vẫn. dùng Eclipse generate.

5. Làm thế nào để tạo `immutable class`: thường hay thấy mọi người chém gió với nhau là StringBuilder vs StringBuffer, StringBuilder vs String, hay là tạo immutable class thế nào. Immutable class là 1 class sau khi dc khởi tạo thì giá trị của class không thay đổi nên những gì làm thay đổi giá trị của class thì nên bỏ như setter chẳng hạn.

```md
1. remove Setter method.
2. final class: không cho class dc extend 
3. final private fields, thì phải có constructor full parameters để khởi tạo.
4. Chắc chắc những Getter method không phải thay đổi giá trị, lưu ý những fields kiểu Date hay kiểu Object thì nên clone trước để bảo đảm giá trị không bị reference.
```
```java
public final class FinalClassExample {
   private final int id;
   private final String name;
   private final Date birthDate;
   private final Map<String, String> testMap;

   public FinalClassExample(int id, String name, Date birthDate, Map<String, String> testMap) {    // (3)
      this.id = id;
      this.name = name;

      birthDate = birthDate.clone();   // (4)
      //
      Map<String, String> tempMap = new HashMap<>();
      String key;
      Iterator<String> it = testMap.keySet().iterator();
      while (it.hasNext()) {
         key = it.next();
         tempMap.put(key, testMap.get(key));
      }
      this.testMap=tempMap;
   }

   public int getId() {
      return id;
   }

   public String getName() {
      return name;
   }

   public Date getBirthDate() {
      return birthDate.clone(); 
   }

   public Map<String, String> getTestMap() {
      // need to clone like code in constructor.
   }
}
```

6. `Interface` vs `Abstract`, `Composition` vs `Inheritance`, `has-a` vs `is-a`. Là những khái niệm cơ bản. Mình thì mình thích Interface, Composition hơn gì độ uyển chuyển.

7. `Constant` thì nên dùng `class`, không dùng interface

```java
// Không Nên:
public interface PhysicalConstants {
   // Avogadro's number (1/mol)
   static final double AVOGADROS_NUMBER = 6.022_140_857e23;
   
   // Boltzmann constant (J/K)
   static final double BOLTZMANN_CONSTANT = 1.380_648_52e-23; 
   
   // Mass of the electron (kg)
   static final double ELECTRON_MASS = 9.109_383_56e-31;
}
```
```java
// Nên:
public class PhysicalConstants {
   private PhysicalConstants();      // không cho khởi tạo.

   // Avogadro's number (1/mol)
   static final double AVOGADROS_NUMBER = 6.022_140_857e23;
   
   // Boltzmann constant (J/K)
   static final double BOLTZMANN_CONSTANT = 1.380_648_52e-23; 
   
   // Mass of the electron (kg)
   static final double ELECTRON_MASS = 9.109_383_56e-31;
}
```

8. if....return thì không cần else nữa, minh review code projects nào cũng gặp kiểu viết như vậy, thật là không nên. Nếu if else nhiều quá thì xem xem có thể chuyển sang switch case dc ko.

9. Dùng `enums` thay thế cho int constants. Có rất nhiều lợi ích.

```java
// Không nên:

   // The int enum pattern - severely deficient!
   public static final int APPLE_FUJI         = 0;
   public static final int APPLE_PIPPIN       = 1;
   public static final int APPLE_GRANNY_SMITH = 2;

   public static final int ORANGE_NAVEL  = 0;
   public static final int ORANGE_TEMPLE = 1;
   public static final int ORANGE_BLOOD  = 2;
```

```java 
   // Nên: 
   public enum Apple { FUJI, PIPPIN, GRANNY_SMITH } 
   public enum Orange { NAVEL, TEMPLE, BLOOD } 
```
```md
Lợi ích: 
1/ Đối tượng hoá và có thể dùng switch ...case. 
2/ An toàn về kiểu và giá trị, giống như constants không thể gõ nhầm dc. 
3/ Dùng Enum.valueOf để validate dễ dàng. 
4/ Có lưu xuống database thì nhìn cũng rõ nghĩa hơn là những con số.
```

10. Collection nên dùng interface và diamond operator <>, code review projects nào cũng gặp.

```java
// Không nên:
ArrayList<String> item = new ArrayList<String>();
```

```java
// Nên:
List<String> item = new ArrayList<>();
```

11. Nếu project đang dùng java 8 thì nên dùng `lambdas`.

```java
// Không nên
// Anonymous class instance as a function object - lỗi thời rồi!
   Collections.sort(words, new Comparator<String>() {
      public int compare(String s1, String s2) {
          return Integer.compare(s1.length(), s2.length());
      }
});
```
```java
// Nên:
// Lambda expression as function object (replaces anonymous class)     
Collections.sort(words,
                  <span class="_4yxo">(s1, s2) -> Integer.compare(s1.length(), s2.length()</span>));  

// Có thể viết theo một cách khác
Collections.sort(words, comparingInt(String::length));

// Hoặc 
words.sort(comparingInt(String::length));  
```

**12. Nên dùng method references lambdas**, nếu dùng method references để viết mà code chổ đó đọc khó hiểu quá thì nên dùng kiểu lambdas thường. Quan trọng là viết code cho người đọc và dễ maintain.
https://docs.oracle.com/javase/tutorial/java/javaOO/methodreferences.html
https://www.codementor.io/eh3rrera/using-java-8-method-reference-du10866vx

**13. Nên viết Unit Test.**

**14. DRY (Don't repeat yourself) Principle:** chổ nào thấy codes lặp lại 2 lần thì nên viết method để dùng chung.

**15. Dùng varargs cẩn thận.**

```java
// Không nên:    
static int min(int... args) {
   if (args.length == 0) { 
      throw new IllegalArgumentException("Too few arguments"); 
   }
   int min = args[0];
   for (int i = 1; i < args.length; i++) {
      if (args[i] < min) {
         min = args[i];
      }
   }
   return min; 
} 

// Sẽ bị lỗi khi không truyền parameters nào.
```

```java
// Nên: 
static int min(int firstArg, int... remainingArgs) {
   int min = firstArg;
   for (int arg : remainingArgs) {
      if (arg < min) {      
         min = arg;
      }
   }
   return min; 
} 
// Cho nên mới cần Unit Test.
```

**16. Nên return empty collections or arrays, không nên return null.** Nhớ dùng `Collections.emptyList()` vì nó là `Singleton`.

```java
// Không Nên:
public List<Cheese> getCheeses() {
   final List<Cheese> cheeseInStock = .....;
   return cheesesInStock.isEmpty() ? null : new ArrayList<>(cheesesInStock);
} 
```

```java
// Nên:
public List<Cheese> getCheeses() {
   final List<Cheese> cheeseInStock = .....;
   return cheesesInStock.isEmpty() ? Collections.emptyList() : 
                                    new ArrayList<>(cheesesInStock);
} 
```

**17. Cộng chuỗi String số lần > 3** thì nên cân nhắc có nên dùng `StringBuilder` hay `StringBuffer` nhé. Nếu đang dùng Thread cần thread-safe thì dùng StringBuffer, còn ko thì dùng StringBuilder. Còn lấy mấy lý do nguỵ biện như làm biếng viết hay giờ mấy cấu hình server khủng rồi, nhanh chậm vài miliseconds giây thì cũng ko ảnh hưởng thì miễn bàn hen. Ở đây đang nói về học thuật và nguyên tắc.

**18.** https://stackify.com/best-practices-exceptions-java/

**19.** Nên viết java doc, document những exposed API nhất là những micro services thì bắt buôc phải có, nếu dc thì document luôn soapui hay export postman.

**20. Keep methods small and focused:** nếu 1 method có quá nhiều code thì nên `extract method` đó ra thành nhiều method nhỏ.

**21. Nên sử dụng thư viện hơn là tự viết**. 2017 là năm của functional programming rồi.

**22. Tuyệt đối tránh dùng float, double để tính toán tỉ giá, thành tiền hay tiền tệ**. hay trong thiết kế database cũng vây, phải dùng BigDecimal, int, long.

```java
System.out.println(1.03 - 0.42);

Output:   0.6100000000000001 
```

**23. Có bao nhiều loại Exception** 

Checked Exception: (FileNotFoundException) 

Unchecked Exception: (NullPointerException, ... ) 

Error: thrown bởi JVM (OutOfMemoryError)
Runtime Exception.
https://www.w3resource.com/java-tutorial/types-of-exception.php

**24. GroupingBy**, Nên dùng Map thay thế cho for, duyệt qua loop if find first return

```java
.collect(Collectors.toList());

// Group by id and a object
Map<Long, ClientEntity> idAndClientMap = entities.stream().collect(Collectors.toMap(c -> c.getId(), Function.identity()));

// Group by id and object list
Map<Long, List<ClientEntity>> idAndClientsMap = entities.stream().collect(Collectors
                .groupingBy(c -> c.getId(), Collectors.mapping(Function.identity(), Collectors.toList())));
```
Khi put vào map nhở kiểm tra value phải khác null

Map<Long, List<Long>> map;

map.put(1L, khác null);                

