---
layout: post
title: Libraries in Java
date: 2019-10-29 12:41 +0530
---

# Collection

A Collection is a group of individual objects represented as a single unit. Java provides Collection Framework which defines several classes and interfaces to represent a group of objects as a single unit.

The Collection interface (java.util. Collection) and Map interface (java.util. Map) are the two main “root” interfaces of Java collection classes.

# Need for Collection Framework :

Before Collection Framework (or before JDK 1.2) was introduced, the standard methods for grouping Java objects (or collections) were Arrays or Vectors or Hashtables. All of these collections had no common interface.

Accessing elements of these Data Structures was a hassle as each had a different method (and syntax) for accessing its members:

# Advantages of Collection Framework:

1. Consistent API : The API has a basic set of interfaces like Collection, Set, List, or Map. All classes (ArrayList, LinkedList, Vector, etc) that implement these interfaces have some common set of methods.
2. Reduces programming effort: A programmer doesn’t have to worry about the design of Collection, and he can focus on its best use in his program.
3. Increases program speed and quality: Increases performance by providing high-performance implementations of useful data structures and algorithms.

``` 
             Collection                Map
         /     /    \      \            |
        /      /      \     \           |
     Set    List    Queue  Dequeue   SortedMap
     /
    /
 SortedSet 
            Core Interfaces in Collections

Note that this diagram only shows core interfaces.  

Collection : Root interface with basic methods like add(), remove(), 
             contains(), isEmpty(), addAll(), ... etc.
 
Set : Doesn't allow duplicates. Example implementations of Set 
      interface are HashSet (Hashing based) and TreeSet (balanced
      BST based). Note that TreeSet implements SortedSet.

List : Can contain duplicates and elements are ordered. Example
       implementations are LinkedList (linked list based) and
       ArrayList (dynamic array based)

Queue : Typically order elements in FIFO order except exceptions
        like PriorityQueue.  

Deque : Elements can be inserted and removed at both ends. Allows
        both LIFO and FIFO. 

Map : Contains Key value pairs. Doesn't allow duplicates.  Example
      implementation are HashMap and TreeMap. 
      TreeMap implements SortedMap.        

The difference between Set and Map interface is that in Set we 
have only keys, whereas in Map, we have key, value pairs.

```

# Collections DisJoint

java.util. Collections.disjoint() method is present in java.util. Collections class. It is used to check whether two specified collections are disjoint or not. More formally, two collections are disjoint if they have no elements in common.

``` java
// Java program to demonstrate working of 
// java.utils.Collections.disjoint() 

import java.util.*; 

public class DisjointDemo 
{ 
	public static void main(String[] args) 
	{ 
		// Let us create array list of strings 
		List<String> mylist1 = new ArrayList<String>(); 
		mylist1.add("practice"); 
		mylist1.add("code"); 
		mylist1.add("quiz"); 
		mylist1.add("geeksforgeeks"); 
		
		// Let us create vector of strings 
		List<String> mylist2 = new Vector<String>(); 
		mylist2.add("geeks"); 
		mylist2.add("geek"); 
		mylist2.add("for"); 
		mylist2.add("coder"); 
		
		// Let us create a vector 
		List mylist3 = new Vector(); 
		
		mylist3.add(1); 
		mylist3.add("practice");	 
		
		// Let us create a Set of strings 
		Set<String> mylist4 = new HashSet<String>(); 
		mylist4.add("practice"); 
		mylist4.add("code"); 
		mylist4.add("quiz"); 
		mylist4.add("geeksforgeeks"); 
		
		
		// Here we are using disjoint() method to check 
		// whether two collections are disjoint or not 
		System.out.println("is mylist1 disjoint to mylist2 : " + 
							Collections.disjoint(mylist1, mylist2)); 
		
		System.out.println("is mylist1 disjoint to mylist3 : " + 
							Collections.disjoint(mylist1, mylist3)); 
		
		System.out.println("is mylist1 disjoint to mylist4 : " + 
							Collections.disjoint(mylist1, mylist4)); 

	} 
} 

//Arrays Do not hav Disjoint Method

// Java program to demonstrate disjoint 
// method with arrays 

import java.util.*; 

public class DisjointDemo 
{ 
	public static void main(String[] args) 
	{ 
		// Let us create arrays of integers 
		Integer arr1[] = {10, 20, 30, 40, 50}; 
		Integer arr2[] = {60, 70, 80, 90, 100}; 
		Integer arr3[] = {50, 70, 80, 90, 100}; 
		Double arr4[] = {50.0, 60.0, 110.0}; 
		
		
		// Please refer below post for details of asList() 
		// https://www.geeksforgeeks.org/array-class-in-java/ 
		// Here we are using disjoint() method to check 
		// whether two arrays are disjoint or not 
		System.out.println("is arr1 disjoint to arr2 : " + 
						Collections.disjoint(Arrays.asList(arr1), Arrays.asList(arr2))); 
		
		System.out.println("is arr1 disjoint to arr3 : " + 
						Collections.disjoint(Arrays.asList(arr1), Arrays.asList(arr3))); 
		
		System.out.println("is arr1 disjoint to arr4 : " + 
						Collections.disjoint(Arrays.asList(arr1), Arrays.asList(arr4))); 

	} 
} 

```

# Java.util. Collections.rotate() Method

java.util. Collections.rotate() method is present in java.util. Collections class. It is used to rotate the elements present in the specified list of Collection by a given distance.

``` java
Syntax:
public static void rotate(List< type > list, int distance)
Parameters : 
list - the list to be rotated.
distance - the distance to rotate the list. 
type - Type of list to be rotated. Examples of 
       types are Integer, String, etc.
Returns :
NA
Throws:
UnsupportedOperationException - if the specified list or 
its list-iterator does not support the set operation.
```

There are no constraints on distance value. It may be zero, negative, or greater than list.size(). After calling this method, the element at index i will be the element previously at index (i – distance) mod list.size(), for all values of i between 0 and list.size()-1, inclusive.

``` java
// Java program to demonstrate working of 
// java.utils.Collections.rotate() 

import java.util.*; 

public class RotateDemo 
{ 
	public static void main(String[] args) 
	{ 
		// Let us create a list of strings 
		List<String> mylist = new ArrayList<String>(); 
		mylist.add("practice"); 
		mylist.add("code"); 
		mylist.add("quiz"); 
		mylist.add("geeksforgeeks"); 

		System.out.println("Original List : " + mylist); 

		// Here we are using rotate() method 
		// to rotate the element by distance 2 
		Collections.rotate(mylist, 2); 

		System.out.println("Rotated List: " + mylist); 
	} 
} 

//for arrays
// Java program to demonstrate rotation of array 
// with Collections.rotate() 
import java.util.*; 

public class RotateDemo 
{ 
	public static void main(String[] args) 
	{ 
		// Let us create an array of integers 
		Integer arr[] = {10, 20, 30, 40, 50}; 

		System.out.println("Original Array : " + 
								Arrays.toString(arr)); 
		
		// Please refer below post for details of asList() 
		// https://www.geeksforgeeks.org/array-class-in-java/ 
		// rotating an array by distance 2 
		Collections.rotate(Arrays.asList(arr), 2); 
		
		System.out.println("Modified Array : " + 
								Arrays.toString(arr)); 
	} 
} 

```

# Abstract Collection

The AbstractCollection class in Java is a part of the Java Collection Framework and implements the Collection interface. It is used to implement an unmodifiable collection, for which one needs to only extend this AbstractCollection Class and implement only the iterator and the size methods.

``` 
java.lang.Object
 ↳ java.util
    ↳ Class AbstractCollection<E>
```

# Example Code

``` java
// Java code to illustrate AbstractCollection 

import java.util.*; 
import java.util.AbstractCollection; 

public class GFG { 
	public static void main(String[] args) 
	{ 
		// Create an empty collection 
		AbstractCollection<Object> 
			abs = new ArrayList<Object>(); 

		// Use add() method to add 
		// elements in the collection 
		abs.add("Welcome"); 
		abs.add("To"); 
		abs.add("Geeks"); 
		abs.add("4"); 
		abs.add("Geeks"); 

		// Displaying the Collection 
		System.out.println("AbstractCollection: "

						+ abs); 

	} 
} 

```

# Methods

*  add(E e): This method ensures that this collection contains the specified element (optional operation).
* addAll(Collection c): This method Adds all of the elements in the specified collection to this collection (optional operation).
* clear(): This method removes all of the elements from this collection (optional operation).
* contains(Object o): This method returns true if this - collection contains the specified element.
* containsAll(Collection c): This method returns true if this collection contains all of the elements in the specified collection.
* isEmpty(): This method returns true if this collection contains no elements.
* iterator(): This method returns an iterator over the elements contained in this collection.
* remove(Object o): This method removes a single instance of the specified element from this collection, if it is present (optional operation).
* size(): This method returns the number of elements in this collection.
* toArray(): This method returns an array containing all of the elements in this collection.
* toArray(T[] a): This method returns an array containing all of the elements in this collection; the runtime type of the returned array is that of the specified       array.
* toString​(): This method returns a string representation of this collection.

