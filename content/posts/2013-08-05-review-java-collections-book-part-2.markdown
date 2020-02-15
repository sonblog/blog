---
author: admin
comments: true
date: 2013-08-05 17:08:20+00:00
layout: post
link: https://quachson.com/review-java-collections-book-part-2/
slug: review-java-collections-book-part-2
title: Review Java Collections Book part 2
wordpress_id: 889
categories:
- Java
tags:
- Java
- Java Colle
---

**II/ The Collections Framework**
1/ Special Collections Support.
2/ Array Algorithm Support.
3/ Custom Implements.
4/ Compatibility Issues.
5/ Advanced Usages.

**III/ Alternative Collection Libraries**
6/ JGL Libraries.
7/ util.concurrent.
8/ Colt.

**1/ Special Collections Support.**

**EMPTY_LIST**: Represents an empty immutable list.
EMPTY_MAP: Represents an empty immutable map.
EMPTY_SET: Represents an empty immutable set.
**binarySearch()**: Searches for element in list with binary search.
**copy()**: Copies elements between two lists.
enumeration(): Converts a collection to an enumeration.
** fill():** Fills a list with a single element.
** max()**: Searches for maximum value within the collection.
** min()**: Searches for minimum value within the collection.
**nCopies():** Creates an immutable list with multiple copies of an element
** reverse():** Reverses elements within list.
** reverseOrder():** Returns comparator for reversing order of comparable elements. (Đảo ngược thứ tự)
** shuffle():** **Randomly** reorders elements in list.
** singleton():** Returns an immutable set of one element.
** singletonList():** Returns an **immutable** list of **one element**.
** singletonMap():** Returns an immutable map of one element.
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

Empty Collections

[code]

List emptyList = Collections.unmodifiableList(new LinkedList());
// 2 câu lệnh cùng logic, nhưng dùng EMPTY_LIST sẽ nhanh hơn
List emptyList = Collections.EMPTY_LIST;
[/code]

[![SingletonList](http://quachson.files.wordpress.com/2013/08/singletonlist.png)](http://quachson.files.wordpress.com/2013/08/singletonlist.png)

[code]
String[] simple = {"One", "Two", "Three", "One", "Two", "Three", "One", "Two", "Three"};
List<String> list = new ArrayList<String>(Arrays.asList(simple));
List<String> oneList = new ArrayList<String>(1);
oneList.add("One");
list.removeAll(oneList);

System.out.println(list.toString());
[/code]

output

[code]
[One, Two, Three, One, Two, Three, One, Two, Three]
oneList: [One]
[Two, Three, Two, Three, Two, Three]
[/code]

**synchronizedCollection**

[code]
Map map = Collections.synchronizedMap(new HashMap(89));
Set set = map.entrySet();
synchronized(map) {
Iterator iter = set.iterator();
while (iter.hasNext()) {
System.out.println(iter.next());
}
}
[/code]

Notes: If you can avoid it, don't waste CPU cycles by converting an historical collection like a Vector into a thread−safe List. It's already thread−safe. While the code will still work, it will require an extra level of indirection for all method calls to ensure thread safety.

**binarySearch**: nhớ sort trước khi dùng

[code]

String simpsons[] = { "Bart", "Hugo", "Lisa", "Marge", "Homer", "Maggie", "Roy" };
// Convert to list
List<String> list = new ArrayList<String>(Arrays.asList(simpsons));
// Ensure list sorted
Collections.sort(list);
System.out.println("Sorted list: [length: " + list.size() + "]");
System.out.println(list);
// Search for element in list
int index = Collections.binarySearch(list, "Maggie");
System.out.println("Found Maggie @ " + index);
// Search for element not in list
index = Collections.binarySearch(list, "Jimbo Jones");
System.out.println("Didn't find 'Jimbo Jones' @ " + index);
// Insert
int newIndex = (-index) - 1;
System.out.println("Add 'Jimbo Jones' at index: " + newIndex);
list.add(newIndex, "Jimbo Jones");
System.out.println("With Jimbo Jones added: [length: " + list.size() + "]");
System.out.println(list);

[/code]

Output:

[code]

Sorted list: [length: 7]
[Bart, Homer, Hugo, Lisa, Maggie, Marge, Roy]
Found Maggie @ 4
Didn't find 'Jimbo Jones' @ -4
Add 'Jimbo Jones' at index: 3
With Jimbo Jones added: [length: 8]
[Bart, Homer, Hugo, Jimbo Jones, Lisa, Maggie, Marge, Roy]

[/code]

Nếu trong list có 2 phẩn tử trùng thì trả về LatestIndex
[Bart, Homer, Hugo, Lisa, Maggie, Maggie, Roy], ta tìm Maggie <---- index: **5, ko phải là 4**

**Min**, **Max**, **reverseOrder**

[code]

String simpsons[] = { "Bart", "Hugo", "Lisa", "Marge", "Homer", "Maggie", "Roy" };
List<String> list = Arrays.asList(simpsons);
System.out.println(list);
// Min should be Bart
System.out.println("min: " + Collections.min(list));
// Max should be Roy
System.out.println("max: " + Collections.max(list));
Comparator comp = Collections.reverseOrder();
// Reversed Min should be Roy
System.out.println("min: " + Collections.min(list, comp));
// Reversed Max should be Bart
System.out.println("max: " + Collections.max(list, comp));

[/code]

Output:

[code]

minMaxReverseOrder...
[Bart, Hugo, Lisa, Marge, Homer, Maggie, Roy]
min: Bart
max: Roy
min: Roy
max: Bart

[/code]

**Note:** If the collection is _**empty**_, NoSuchElementException is thrown when _**min**_() or _**max**_() are called.

_**Copy(dest, src)**_ : cũng giống với System.arraycopy() có một vài điểm chú ý khi dùng là

+ destination list phải dc khởi tạo

+ destination list length phải >= src list nếu ko sẽ bị _**IndexOutOfBoundsException**_

**Note for Copy:** The copy() method copies references between lists. If the underlying object changes, the change would be reflected in what both lists reference.





bbbb
