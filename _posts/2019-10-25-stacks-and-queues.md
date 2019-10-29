---
layout: post
title: Stacks And Queues
date: 2019-10-25 18:40 +0530
---

# Stacks and Queues

* Stack : LIFO
* Queue : FIFO# Stacks

 - push , pop , isEmpty()

 

``` java

 public class LinkedListStackOfStrings{
     private Node first = null;
     private class Node{
         String item;
         Node next;
     }
     public boolean isEmpty(){
         return first == null;
     }
     public void push(String item){
         Node OldFirst = first;
         first = new Node();
         first.tem = item;
         first.next = OldFirst;
     }
     public String pop(){
         String item = first.item;
         first = first.next;
         return item;
     }
 }

 ```

 ## Arrays Structures

 

``` java

public class FixedCapacityStackOfStrings{
    private String[] s;
    private int N = 0;
    public FixedCapacityStackOfStrings(int capacity){
        s = new String[capacity];
    }
    public boolean isEmpty(){
        return N == 0;
    }
    public void push(String item){
        s[N++] = item;
    }
    public String pop(){
        return s[--N];
    }
}
 ```

 > Overflow and UnderFlow Conditions need to be checked

 # Resizing-Array Implementation

    - If the Array Fills up Then We Double the Size# Queues
* LinkedList Implementation

`enqueue` -> Add to the beginning of the Queue
`dequeue` -> Remove the Bottom of the Queue

* Two pointers First and End

``` java

public class LinkedQueueOfStrings{
    private Node first,last;
    private class Node{
        String id;
        Node next;
    }
    public boolean isEmpty(){
        return first === null;
    }
    public void enqueue(String item){
        Node OldLast = last;
        last = new Node();
        last.id = item;
        last.next = null;
        if(isEmpty()){
            first = last;
        }
        else{
            oldLast.next = last;
        }
    }
    public String dequeue(){
        String item = first.item;
        first = first.next;
        if(isEmpty()){
            last = null;
        }
        return item;
    }
}

```

# Generics In JAVA

``` java
public class Stack<Item>{
    private Node first = null;
    private class Node{
        Item item;
        Node next;
    }

    // Following replace String everywhere with Item
}
```

# Iterator

``` java
public class Stack<Item> implements Iterable<Item>{
    public Iterator<Item> iterator(){
        return new ListIterator();
    }
    private class ListInterator implements Iterator<Item>{
        private Node current = first;
        public boolean hasNext(){
            return current != null;
        }
        public Item next(){
            Item item = current.item;
            current = current.next;
            return item;
        }
    }
}

```

# Java Libraries

-List Interface

``` java

//List Interface. java.util.List API 
public interface List<Item> implements Iterable<Item>
List();
boolean isEmpty();
void add(Item item);
Item get(int index);
Item remove(int index);
boolean contains(Item item);

```

# Dijkstra's Two Stack Algorithm for Arithmetic Evaluations

* Maintain Two Stacks `Value Stack` & `Operator Stack` 
* Left Parenthesis Igonre
* Right Paranthesis : pop operator and top two values from       value stack and one value from operator stack : push the   

  result of the appllying the operator to these values to those values  onto the operand stack and push the result back to the values stack

