---
layout: post
title: Symbol Table
date: 2019-10-26 13:28 +0530
---

# Symbol Tables

 - Insert a value with specified key
 - Given a key , search for the corresponding value.
 - Associative Array Abstraction

 

``` java
 public class ST<Key , Value>
 ST()
 void put(Key key , Value val)
 Value get(Key key)
 void delete(Key key)
 boolean contains(Key key)
 boolean isEmpty()
 int size()
 Iterable<Key> keys()
 ```

 - Values are not null
 - get method return null
 - put() overwrites old value

 # Symbol Table Test Client

``` java
public class FrequencyCounter{
    public static void main(String args[]){
        int milen = Integer.parseInt(args[0]);
    }
    ST<String , Integer> st = new ST<String , Integer>();
    while(!StdIn.isEmpty()){
        String word = StdIn.readString();
        if(word.length() < minLen)
            continue;
        if(!st.contains(word))
            st.put(word,1);
        else
            st.put(word , st.get(word) + 1);
    }
    String max = "";
    st.put(max , 0);
    for(String word : st.keys()){
        if(st.get(word) > st.get(max))
            max = word;
    }
    StdOut.println(max + " " + st.get(max));
}
```

# Implementation

* Maintain an unordered linked list of Key-Value Piars
* If not present add to front# Methods in HashMap

## Constructors

01. HashMap(): It is the default constructor which creates an instance of HashMap with initial capacity 16 and load factor 0.75.
02. HashMap(int initial capacity): It creates a HashMap instance with specified initial capacity and load factor 0.75.
03. HashMap(int initial capacity, float loadFactor): It creates a HashMap instance with specified initial capacity and specified load factor.
04. HashMap(Map map): It creates instance of HashMap with same mappings as specified map.

01. void clear(): Used to remove all mappings from a map.
02. boolean containsKey(Object key): Used to return True if for a specified key, mapping is present in the map.
03. boolean containsValue(Object value): Used to return true if one or more key is mapped to a specified value.
04. Object clone(): It is used to return a shallow copy of the mentioned hash map.
05. boolean isEmpty(): Used to check whether the map is empty or not. Returns true if the map is empty.
06. Set entrySet(): It is used to return a set view of the hash map.
07. Object get(Object key): It is used to retrieve or fetch the value mapped by a particular key.
08. Set keySet(): It is used to return a set view of the keys.
07. int size(): It is used to return the size of a map.

    Object put(Object key, Object value): It is used to insert a particular mapping of key-value pair into a map.

08. putAll(Map M): It is used to copy all of the elements from one map into another.
09. Object remove(Object key): It is used to remove the values for any particular key in the Map.
10. Collection values(): It is used to return a Collection view of the values in the HashMap.

``` java
// Java program to illustrate 
// Java.util.HashMap 

import java.util.HashMap; 
import java.util.Map; 

public class GFG { 
	public static void main(String[] args) 
	{ 

		HashMap<String, Integer> map 
			= new HashMap<>(); 

		print(map); 
		map.put("vishal", 10); 
		map.put("sachin", 30); 
		map.put("vaibhav", 20); 

		System.out.println("Size of map is:- "

						+ map.size()); 

		print(map); 
		if (map.containsKey("vishal")) { 
			Integer a = map.get("vishal"); 
			System.out.println("value for key"

							+ " \"vishal\" is:- "
							+ a); 

		} 

		map.clear(); 
		print(map); 
	} 

	public static void print(Map<String, Integer> map) 
	{ 
		if (map.isEmpty()) { 
			System.out.println("map is empty"); 
		} 

		else { 
			System.out.println(map); 
		} 
	} 
}
````

