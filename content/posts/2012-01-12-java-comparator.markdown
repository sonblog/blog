---
author: admin
comments: true
date: 2012-01-12 08:11:10+00:00
template: "post"
link: https://quachson.com/java-comparator/
slug: java-comparator
title: Java Comparator
wordpress_id: 732
categories:
- Java
tags:
- Java
---

[code]

class Employee{
private int age;
private String name;

// get, set age, name
}

[/code]

[code]

class AgeComparator implements Comparator {
public int compare(Object emp1, Object emp2){

/*
* parameter are of type Object, so we have to downcast it
* to Employee objects
*/

int emp1Age = ((Employee)emp1).getAge();
int emp2Age = ((Employee)emp2).getAge();

if(emp1Age > emp2Age)
return 1;
else if(emp1Age < emp2Age)
return -1;
else
return 0;
}
}

[/code]

[code]

class NameComparator implements Comparator {

public int compare(Object emp1, Object emp2){
//parameter are of type Object, so we have to downcast it to Employee objects

String emp1Name = ((Employee)emp1).getName();
String emp2Name = ((Employee)emp2).getName();

//uses compareTo method of String class to compare names of the employee
return emp1Name.compareTo(emp2Name);
}
}

[/code]

[code]

public class JavaComparatorExample {

public static void main(String args[]){

//Employee array which will hold employees
Employee employee[] = new Employee[2];

//set different attributes of the individual employee.
employee[0] = new Employee();
employee[0].setAge(40);
employee[0].setName("Joe");

employee[1] = new Employee();
employee[1].setAge(20);
employee[1].setName("Mark");

System.out.println("Order of employee before sorting is");

for(int i=0; i < employee.length; i++){
System.out.println( "Employee " + (i+1) + " name :: " + employee[i].getName() + ", Age :: " + employee[i].getAge());
}

/*
Sort method of the Arrays class sorts the given array.
Signature of the sort method is,
static void sort(Object[] object, Comparator comparator)

IMPORTANT: All methods defined by Arrays class are static. Arrays class
serves as a utility class.
*/

//Sorting array on the basis of employee age by passing AgeComparator
Arrays.sort(employee, new AgeComparator());
System.out.println("nnOrder of employee after sorting by employee age is");

for(int i=0; i < employee.length; i++){
System.out.println( "Employee " + (i+1) + " name :: " + employee[i].getName() + ", Age :: " + employee[i].getAge());
}

//Sorting array on the basis of employee Name by passing NameComparator
Arrays.sort(employee, new NameComparator());

System.out.println("nnOrder of employee after sorting by employee name is");
for(int i=0; i < employee.length; i++){
System.out.println( "Employee " + (i+1) + " name :: " + employee[i].getName() + ", Age :: " + employee[i].getAge());
}

}

}

[/code]

OUTPUT of the above given Java Comparable Example would be :
_Order of employee before sorting is_
_Employee 1 name :: Joe, Age :: 40_
_Employee 2 name :: Mark, Age :: 20_
_Order of employee after sorting by employee age is_
_Employee 1 name :: Mark, Age :: 20_
_Employee 2 name :: Joe, Age :: 40_
_Order of employee after sorting by employee name is_
_Employee 1 name :: Joe, Age :: 40_
_Employee 2 name :: Mark, Age :: 20_


