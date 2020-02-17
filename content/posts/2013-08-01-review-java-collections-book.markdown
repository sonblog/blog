---
author: admin
comments: true
date: 2013-08-01 15:07:21+00:00
template: "post"
link: https://quachson.com/review-java-collections-book/
slug: review-java-collections-book
title: Review Java Collections Book part 1
wordpress_id: 809
categories:
- Java
tags:
- Java
- Java Collections
---

**I/ The Historical Collection Classes**
1/ Arrays. (Copy and Clone, Immutability, Reflection)
2/ The Vector and Stack (Immutability)
3/ The Enumeration Interface.
4/ The Dictionary, Hashtable, Properties classes.
5/ The BitSet classes.

**II/ The Collections Framework**
1/ Sets.
2/ Lists.
3/ Maps.
4/ Sorting.
5/ Special Collections Support.
6/ Array Algorithm Support.
7/ Custom Implements.
8/ Compatibility Issues.
9/ Advanced Usages.

**III/ Alternative Collection Libraries**
1/ JGL Libraries.
2/ util.concurrent.
3/ Colt.

**1/ Arrays**
**a/ Copy**
- System.arraycopy(Object src, int srcPos, Object dest, int destPos, int length);

[code]
public static int[] doubleArray(int original[]) {
int length = original.length;
int newArray[] = new int[length * 2];
System.arraycopy(original, 0, newArray, 0, length);
return newArray;
[/code]

- Clone

[code]
static int[] cloneArray(int original[]) {
return (int[])original.clone();
}
[/code]

b/ **Immutability**: final keyword
final static int array[] = {1, 2, 3, 4, 5}
with final keyword, you can not new array but assigning value for element of array  is OK.
**can**: array[0] = 10;
**cannot**: array = new int[100];

c/ **Reflection**: object.getClass();
- Class.isArray(); // true/false
- Class.getComponentType();
- Array.getLength(object);
- Array.newInstance(Clas<?> typeComponent, int length);

[code]
int array[] = (int[])Array.newInstance(int.class, 5);
int array[] = (int[])Array.newInstance(Integer.TYPE, 5);
// dimension
int dimensions[] = {5};
int array[] = (int[])Array.newInstance(int.class, dimensions);
int dimensions[] = {3, 4};
int array[][] = (int[][])Array.newInstance(int.class, dimensions);
[/code]

**Array Getter and Setter Methods**
GETTER METHODS SETTER METHODS
Array._get_(Object array, int index) _set_(Object array, int index, Object value)
_getBoolean_(Object array, int index) _setBoolean_(Object array, int index, boolean value)
_getByte_(Object array, int index) _setByte_(Object array, int index, byte value)
_getChar_(Object array, int index) _setChar_(Object array, int index, char value)
_getDouble_(Object array, int index) _setDouble_(Object array, int index, double value)
_getFloat_(Object array, int index) _setFloat_(Object array, int index, float value)
_getInt_(Object array, int index) _setInt_(Object array, int index, int value)
_getLong_(Object array, int index) _setLong_(Object array, int index, long value)
_getShort_(Object array, int index) _setShort_(Object array, int index, short value)

**2/ The Vector and Stack classes**

[![Vector-Stack](http://quachson.files.wordpress.com/2013/08/vector-stack.png)](http://quachson.files.wordpress.com/2013/08/vector-stack.png)
- **Vector**: type-safety, synchronized (thus run slower than ArrayList with not synchronized.)
+ List<String> vector = new Vector<String>(); // use all methods of List;
+ vector.add(); //  elements of vector can store NULL value
.Stack: FIFO has specific methods:
**a/ Copy as simple way**

[code]
Vector v = . . .;
String array[] = new String[v.size()];
array = (String[])v.toArray(array);
[/code]

**Copy as smart way**

[code]
Vector v = . . .;
String array[] = new String[v.size()];
v.<strong>copyInto</strong>(array);
[/code]

it will give you an array of the proper type, it doesn't require a cast, and it won't cause a created array to be discarded. Some runtime exceptions can be thrown from this operation. In the event that the destination array is too small, an ArrayIndexOutOfBoundsException will be thrown. If the elements of the vector are not assignment−compatible with the array, an ArrayStoreException will be thrown.

b/ **Immutability**: you may wish to make the vector read−only—this will prevent accidental changes to its contents.

[code]
Vector v = new Vector();
// fill vector
List l = Collections.unmodifiableList(v);
[/code]

**Collections.sort(v);**
- **Stack**: FILO
Stack<String> stack = new Stack<String>();
**a/ methods:**
+ _isEmpty_();  // true/false
+ _peek_():       // Fetches an element at the top
+ _pop_():        // Removes an element from the top.
+ _push_();      // Adds an element to the top of the stack.
+ _search_(Object element)    // Checks if an element is on the stack.

**3/ The Enumeration Interface.**
+ _hasMoreElements_()
+ _nextElement_()

[code]
for (Enumeration enum = . . .; enum.hasMoreElements(); ) {
    Object o = enum.nextElement();
    processObject(o);
}
[/code]

[code]
Collection col = . . .;
Enumeration enum = Collections.enumeration(col);
[/code]

**4/ The Dictionary, Hashtable, Properties classes.**

[![Dictionary-Hashtable-Properties](http://quachson.files.wordpress.com/2013/08/dictionary-hashtable-properties.png)](http://quachson.files.wordpress.com/2013/08/dictionary-hashtable-properties.png)

**Dictionary-Hashtable-Properties**

**Dictionary** is an abstract class with only abstract methods.

**Hashtable**:
+ Hashtable is _**synchronized**_, whereas HashMap is not. This makes HashMap better for non-threaded applications, as unsynchronized Objects typically perform better than synchronized ones.
+ Hashtable does not allow null keys or values. HashMap allows one null key and any number of null values.

When using the key−value pairs in a hash table, the keys are converted into an integer called a hash code by using a hashing algorithm. This hash code is then reduced—based upon the internal storage structure used by the hash table—to serve as an index into this structure (an array). For two equal elements, the hash code must be the same. Two elements are defined as equal if the equals() method returns true when they are compared. For two unequal elements, the hash code may be different or the same.
If the hash code is the same for unequal elements, it is called a collision. When there are many elements with the same hash code they cannot be stored in a single array element, which causes the degradation. Instead, they are stored in a linked list data structure.

Hashtable-linkedList: If there are multiple elements with the same index in the hash table, a linked list must be traversed to find the element with the specific key.
**+ Hashtable Immutability**

[code]
Hashtable h = new Hashtable();
// fill hash table
Map m = Collections.unmodifiableMap(h);
[/code]

**Properties class**: The Properties class represents yet another specialized Hashtable. Instead of being a collection of key−value
pairs of any object, it is customized such that both the keys and the values are only supposed to be strings.

**5/ The BitSet Class:**

[![BitSet](http://quachson.files.wordpress.com/2013/08/bitset.png)](http://quachson.files.wordpress.com/2013/08/bitset.png)
BitSetwith methods: and(), andNot(), or(), xor().
Element type: int

**II/ The Collections Framework**

[![Set_Collections](http://quachson.files.wordpress.com/2013/08/set_collections.png)](http://quachson.files.wordpress.com/2013/08/set_collections.png)
1/ **Set interface:** like List but a group of elements without duplicates.
Set_Collections

[code]
String elements[] = {"Irish Setter", "Poodle", "English Setter", "Gordon Setter", "Pug"};
Set set = new HashSet(Arrays.asList(elements));
[/code]

**2/ Lists**.

[![List](http://quachson.files.wordpress.com/2013/08/list.png)](http://quachson.files.wordpress.com/2013/08/list.png)
**ListLinkedList** provides quick insertions and deletions at positions other than the end.
- _addFirst_(): Adds an element to beginning of the list.
- _addLast_(): Adds an element to end of the list.
- _getFirst_(), getLast(), removeFirst(), removeLast()
- _listIterator_()

**ListIterator**
- _hasPrevious_(), _hasNext_()
- _next_(), _previous_() : Fetches the next/previous element of the iterator
- _nextIndex_(), _previousIndex_(): Returns the index of the next/previous element of the iterator.
Start at the first element.

[code]

ListIterator iter = list.listIterator();
    while (iter.hasNext()) {
    System.out.println(iter.next());
}

[/code]

Start at the end.

[code]
ListIterator iter = list.listIterator(list.size());
while (iter.hasPrevious()) {
    System.out.println(iter.previous());
}
[/code]

**3/ Maps**:

[![Table-Collections](http://quachson.files.wordpress.com/2013/08/table-collections.png)](http://quachson.files.wordpress.com/2013/08/table-collections.png)
Table-Collections

[code]
import java.util.*;

public class TreeMapDemo {

public static void main(String args[]) {
    // Create a hash map
    TreeMap tm = new TreeMap();
    // Put elements to the map
    tm.put("Zara", new Double(3434.34));
    tm.put("Mahnaz", new Double(123.22));
    tm.put("Ayan", new Double(1378.00));
    tm.put("Daisy", new Double(99.22));
    tm.put("Qadir", new Double(-19.08));

    // Get a set of the entries
    Set set = tm.entrySet();
    // Get an iterator
    Iterator i = set.iterator();
    // Display elements
    while(i.hasNext()) {
        Map.Entry me = (Map.Entry)i.next();
        System.out.print(me.getKey() + ": ");
        System.out.println(me.getValue());
    }
    System.out.println();
    // Deposit 1000 into Zara's account
    double balance = ((Double)tm.get("Zara")).doubleValue();
    tm.put("Zara", new Double(balance + 1000));
    System.out.println("Zara's new balance: " +  tm.get("Zara"));
}
} // class

[/code]

This would produce following result:

[code]

Ayan: 1378.0
Daisy 99.22
Mahnaz: 123.22
Qadir: -19.08
Zara: 3434.34
Zara's current balance: 4434.34

[/code]

- **Immutability**

[code]
SortedMap m = Collections.<em><strong>synchronizedSortedMap</strong></em>(new TreeMap(...));
[/code]

**4/ Sorting**.
**Interface Comparator vs Comparable**
@_**Comparable**_: allows you to specify how objects that you are implementing get compared.
@_**Comparator**_: provides a way for you to provide custom comparison logic for types that you have no control over.

Obviously, if you don't have control over a class (or you want to provide multiple ways to compare objects that you do have control over) then use Comparator.

**@Comparable**

[code]

package quachson.wordpress.collection.sorting;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class Employee implements Comparabl<Employee> {
    private int number;

    public Employee(int number) {
        this.number = number;
    }
    public int getNumber() {
        return number;
    }
    public void setNumber(int number) {
        this.number = number;
    }

    public int compareTo(Employee employee) {
        final int number = employee.getNumber();
        if (this.number == number) {
            return 0;
        }
        // tang dan
        if (this.number &lt; number)  {
            return -1;
        }
        return 1;
    }

     public static void main(String args[]) {
         System.out.println("Hello");
         List<Employee> list = new ArrayList<Employee>();
         list.add(new Employee(5));
         list.add(new Employee(1));
         list.add(new Employee(7));

         for (Employee employee : list) {
             System.out.println(employee.getNumber());
         }

         Collections.sort(list);
         System.out.println("----------------------------------------");
         for (Employee employee : list) {
             System.out.println(employee.getNumber());
         }
     }
}
[/code]

@**Comparator**:

[code]
package quachson.wordpress.collection.sorting;
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

public class EmployeeComparator implements Comparator<Employee> {

public EmployeeComparator() {
}

public static void main(String[] args) {
     System.out.println("Hello Comparator");
     List<Employee> list = new ArrayList<Employee>();
     list.add(new Employee(5));
     list.add(new Employee(5));
     list.add(new Employee(1));
     list.add(new Employee(7));

     for (Employee employee : list) {
          System.out.println(employee.getNumber());
     }

     Collections.sort(list, new EmployeeComparator());
     System.out.println("-------------------------------------");
     for (Employee employee : list) {
         System.out.println(employee.getNumber());
     }
}

@Override
public int compare(Employee o1, Employee o2) {
    final int number1 = o1.getNumber();
    final int number2 = o2.getNumber();

    if (number1 == number2) {
        return 0;
    }
    // giam dan
    if (number1 &gt; number2) {
        return -1;
    }
    return 1;
}
} // end class
[/code]

**5/ Special Collections Support**.
_**EMPTY_LIST:**_ Represents an empty immutable list.
EMPTY_MAP: Represents an empty immutable map.
EMPTY_SET: Represents an empty immutable set.
binarySearch(): Searches for element in list with binary search.
copy(): Copies elements between two lists.
enumeration(): Converts a collection to an enumeration.
fill() Fills a list with a single element.
max() Searches for maximum value within the collection.
min() Searches for minimum value within the collection.
nCopies() Creates an immutable list with multiple copies of an element
reverse() Reverses elements within list.
reverseOrder() Returns compartor for reversing order of comparable elements.
shuffle() Randomly reorders elements in list.
singleton() Returns an immutable set of one element.
singletonList() Returns an immutable list of one element.
singletonMap() Returns an immutable map of one element.
sort() Reorders the elements in a list.
synchronizedCollection() Creates a thread−safe collection.
synchronizedList() Creates a thread−safe list.
synchronizedMap() Creates a thread−safe map.
synchronizedSet() Creates a thread−safe set.
synchronizedSortedMap() Creates a thread−safe sorted map.
synchronizedSortedSet() Creates a thread−safe sorted set.
unmodifiableCollection() Creates a read−only collection.
unmodifiableList() Creates a read−only list.
unmodifiableMap() Creates a read−only map.
unmodifiableSet() Creates a read−only set.
unmodifiableSortedMap() Creates a read−only sorted map.
unmodifiableSortedSet() Creates a read−only sorted set.
