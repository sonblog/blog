---
author: admin
comments: true
date: 2010-12-18 06:46:39+00:00
template: "post"
link: https://quachson.com/net-core-notes/
slug: net-core-notes
title: .NET Core notes
wordpress_id: 357
categories:
- .NET
tags:
- .NET
---

Build-in value types

System.SByte and sbyte         -128 t0 127
System.Byte and byte               0 to 255
System.Int16 and short            - 32768 to 32768
System.Int32 and int
System.UInt32 and uint
System.Int64 and long
System.Single and float
System.Double and double
System.Decimal and decimal          16 bytes

_System.Int32_ and _int_ are the same. It's alias (short form).

bool? a = null;
Nullable<bool> b = null;

**struct**

The _Cycle _structure can be easily **converted **from a** value type** to a **reference type** by **changing **the Structure/**struct **keywords to **Class**. If you make that change, instances of the Cycle **class **would be allocated on the **managed heap** rather than as **12 bytes on the stack** (4 bytes for each private integer field) and assignment between two Cycle vari- ables results in both variables pointing to the same instance. While the functionality is similar, structures are usually more efficient than classes. You should define a structure, rather than a class, if the type will perform better as a value type than a reference type. Specifically, structure types should meet all of these criteria:
- Represents a single value logically.
- Has an instance size that is less than 16 bytes.
- Is not frequently changed after creation.
- Is not cast to a reference type. (Casting is the process of converting between types.)

**Enumerations** : list of choices

enum Titles { Mr, Ms, Mrs, Dr };

Titles t = Titles.Dr;
Console.WriteLine("{0}.", t); // Displays "Dr."

Mục đích của enumerations là đơn giản hóa, tránh sai xót và đọc code dễ hiểu, ý nghĩa hơn. Giới hạn giá trị trong tập hợp.

**Reference **types store the address of their data, also known as a pointer, on the stack. The actual data to which that address refers is stored in an area of memory called the heap. The runtime manages the memory used by the heap through a process called garbage collection. Garbage collection recovers memory periodically, as needed, by disposing of items that are no longer referenced.

Strings of type System.String are **immutable **in the .NET Framework. That means any change to a string causes the runtime to create a new string and abandon the old one

The StringBuilder class to create dynamic (**mutable**) strings.

Forming Regular Expressions: Chapter 3.


