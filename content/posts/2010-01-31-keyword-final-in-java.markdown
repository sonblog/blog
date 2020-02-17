---
author: admin
comments: true
date: 2010-01-31 02:13:01+00:00
template: "post"
link: https://quachson.com/keyword-final-in-java/
slug: keyword-final-in-java
title: Keyword "final" in java
wordpress_id: 32
categories:
- Java
tags:
- Java
---

final: “This cannot be changed.”

final: data, method and class

final data: constant. Blank final, only use for constructor
Class A {
final int i;
public A() {
i = 10;
}
}

// Arrays:
final int[] a = { 1, 2, 3, 4, 5, 6 };
can: for(int i=0; i<a.length; i++) { a[i]++; }
can not: a = new int[3];

// Object
Class Value {
int i;
}

Class FinalClass {
public final Value v2 = new Value();
public static final Value v3 = new Value();
public static void main() {
FinalClass finalClass = new FinalClass();
finalClass.v2.i ++; // yes
// finalClass.v2 = new Value(); can not
// finalClass v3 = new Value(); can not
}
}

Final arguments: inside the method you cannot change what the argument handle points to:
class Gizmo {
public void spin() {}
}

public class FinalArguments {
void with(final Gizmo g) {
//! g = new Gizmo(); // Illegal -- g is final
g.spin();
}
void without(Gizmo g) {
g = new Gizmo(); // OK -- g not final
g.spin();
}
// void f(final int i) { i++; } // Can't change
// You can only read from a final primitive:
int g(final int i) { return i + 1; }
public static void main(String[] args) {
FinalArguments bf = new FinalArguments();
bf.without(null);
bf.with(null);
}
}

Final methods:
- The first is to put a “lock” on the method to prevent any inheriting class from changing its meaning and cannot be overridden.
- The second reason for final methods is efficiency. If you make a method final, you are allowing the compiler to turn any calls to that method into inline calls.

Final Classes: don’t want to inherit from this class
