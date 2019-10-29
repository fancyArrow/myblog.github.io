---
layout: post
title: Priority Queues
date: 2019-10-26 11:02 +0530
---

# Priority Queues

## API and Elementary Implemenetations

* Priority Queue
* Remove largest or smallest# Binary Heaps
* Trees Completeley Balanced except lower level
* Array representation of a heap- ordered complete binary tree

## Heap Ordered Binary Tree

* Keys in Nodes
* Parent's Key no is smaller than children's keys.

* Array's Representation
1. Largest key is a[1]
2. Parent of Node at k is at k/2;
3. Children of node at k are at 2k and 2k+1

* Heap Order Restoration
* Exchnage key in child with key in parent
* Repeat untill order is restored
* Whene children is Larger than Parent

``` java
private void swim(int k ){
    while(k > 1 && less(k/2 , k){
        exch(k , k/2);
        k = k/2;
    }
}
```

# Insert

``` java
public void insert(Key x){
    pq[++N] = x;
    swim(N);
}
```

# sink Operation

* When the Parent's key becomes Smaller than Children
* Exchange key in parent with key in larger child

``` java
private void sink(int k){
    while(2*k <= N){
        int j = 2 *k;
        if(j < N && less(j , j+1)){
            j++;
        }
        if(!less(k , j)){
            break;
        }
        exch(k , j);
        k = j;
    }
}
```

# Del Max

``` java
public Key delMax(){
    Key max = pq[1];
    exch(1 , N--);
    sink(1);
    pq[N+1] = null;
    return max;
}
```

# Complete Java Priority Queue Using Binary Heap Data Structure

``` java
public class MaxPQ<Key extends Comparable <Key>>{
    private Key[] pq;
    private int N;
    public MaxPQ(int capacity){
        pq = (Key[]) new Comaparble[capacity +1];
    }
    public boolean isEmpty(){
        return N==0;
    }
    public void insert(Key key){
        /* same as above */
    }
    public Key delMax(){
        // same as above
    }
    private void swim(int k){

    }
    private void sink(int k){

    }
    private boolean less(int i , int j){
        return pq[i].compareTo(pq[j]) < 0
    }
    private void exh(int i , int j){
        Key t = pq[i];
        pq[i] = pq[j];
        pq[j] = t;
    }
}
```

* Clients cannot change keys from a PQ
* Immutable Data Types : String , Integer , Double , Color , Vector , Transaction , Point2D
* Mutable : StringBuilder , Counter , Java Array , Stack , Counter# Heap Sort

 - Create a max Heap
 - Repeatedly remove the maximum Key
 # Java code for Heap SOrt using Bottom Up Approach
 ```java 
 public class Heap{

     public static void sort(Comparable[] pq){
         int N = pq.length;
         for(int k = N/2 ; k >= 1 ; k--){
             sink(pq , k , N);
         }
         while(N > 1){
             exch(pq , 1 , N);
             sink(pq , 1 , --N);
         }
     }
     //other functions same as before

 }
 

``` 
  # Priority Queue In java
   - PriorityQueue(): Creates a PriorityQueue with the default initial capacity (11) that orders its elements according to their natural ordering.
   - PriorityQueue(Collection<E> c): Creates a PriorityQueue containing the elements in the specified collection.
   - PriorityQueue(int initialCapacity): Creates a PriorityQueue with the specified initial capacity that orders its elements according to their natural ordering.
   - PriorityQueue(int initialCapacity, Comparator<E> comparator): Creates a PriorityQueue with the specified initial capacity that orders its elements according to the specified comparator.
   - PriorityQueue(PriorityQueue<E> c): Creates a PriorityQueue containing the elements in the specified priority queue.
   - PriorityQueue(SortedSet<E> c): Creates a PriorityQueue containing the elements in the specified sorted set.
 ```java
// Java program to demonstrate working of priority queue in Java 
import java.util.*; 

class Example 
{ 
	public static void main(String args[]) 
	{ 
		// Creating empty priority queue 
		PriorityQueue<String> pQueue = 
						new PriorityQueue<String>(); 

		// Adding items to the pQueue using add() 
		pQueue.add("C"); 
		pQueue.add("C++"); 
		pQueue.add("Java"); 
		pQueue.add("Python"); 

		// Printing the most priority element 
		System.out.println("Head value using peek function:"

										+ pQueue.peek()); 

		// Printing all elements 
		System.out.println("The queue elements:"); 
		Iterator itr = pQueue.iterator(); 
		while (itr.hasNext()) 
			System.out.println(itr.next()); 

		// Removing the top priority element (or head) and 
		// printing the modified pQueue using poll() 
		pQueue.poll(); 
		System.out.println("After removing an element" + 
						"with poll function:"); 
		Iterator<String> itr2 = pQueue.iterator(); 
		while (itr2.hasNext()) 
			System.out.println(itr2.next()); 

		// Removing Java using remove() 
		pQueue.remove("Java"); 
		System.out.println("after removing Java with" + 
						" remove function:"); 
		Iterator<String> itr3 = pQueue.iterator(); 
		while (itr3.hasNext()) 
			System.out.println(itr3.next()); 

		// Check if an element is present using contains() 
		boolean b = pQueue.contains("C"); 
		System.out.println ( "Priority queue contains C " + 
							"or not?: " + b); 

		// Getting objects from the queue using toArray() 
		// in an array and print the array 
		Object[] arr = pQueue.toArray(); 
		System.out.println ( "Value in array: "); 
		for (int i = 0; i<arr.length; i++) 
		System.out.println ( "Value: " + arr[i].toString()) ; 
	} 
} 

 ```

