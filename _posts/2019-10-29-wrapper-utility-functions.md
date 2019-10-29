---
layout: post
title: Wrapper Utility Functions
date: 2019-10-29 17:00 +0530
---
**Utility methods of Wrapper classes:**T
he objective of 
Wrapper class is to define several utility methods which are required 
for the primitive types. There are 4 utility methods for primitive type 
which is defined by Wrapper class:

1. **valueOf() method : **We can use valueOf() method to create Wrapper object for given primitive or String. There are 3 types of valueOf() methods:

    - **Wrapper valueOf(String s) : **Every wrapper class except Character class contains a static valueOf() method to create Wrapper class object for given String.  
**Syntax:**  

**public static Wrapper valueOf(String s);**

 
```java
// Java program to illustrate valueof()  

   

class GFG {   

public static void main(String[] args)  
{
Integer I = Integer.valueOf("10");         

System.out.println(I);  
Double D = Double.valueOf("10.0");
System.out.println(D);         

Boolean B = Boolean.valueOf("true");  

System.out.println(B);  

// Here we will get RuntimeException  
Integer I1 = Integer.valueOf("ten");  
}  
}      
Output: 
10
10.0
true
Exception in thread "main" java.lang.NumberFormatException: For input string: "ten"
```
- **Wrapper valueOf(String s, int radix) :** Every 
Integral Wrapper class Byte, Short, Integer, Long) contains the 
following valueOf() method to create a Wrapper object for the given 
String with specified radix. The range of the radix is 2 to 36.  
**Syntax:**

**public static Wrapper valueOf(String s, int radix)**

 
``` java
// Java program to illustrate valueof() 
class GFG {  
public static void main(String[] args)  
{ 
Integer I = Integer.valueOf("1111",2);  

System.out.println(I);  
Integer I1 = Integer.valueOf("1111",4);  

System.out.println(I1);  
}  

}      
Output: 

15
85
```
- **Wrapper valueOf(primitive p) :** Every Wrapper class 
including Character class contains the following method to create a 
Wrapper object for the given primitive type.
**Syntax:** 

**public static Wrapper valueOf(primitive p);**

```java

// Java program to illustrate valueof()  
class GFG {  

public static void main(String[] args)
{  
Integer I = Integer.valueOf(10);  
Double D = Double.valueOf(10.5);  
Character C = Character.valueOf('a');
System.out.println(I); 
System.out.println(D);  
System.out.println(C); 

}  

}      
Output: 

10
10.5
a
```
2. **xxxValue() method:** We can use xxxValue() methods to
 get the primitive for the given Wrapper Object. Every number type 
Wrapper class( Byte, Short, Integer, Long, Float, Double) contains the 
following 6 methods to get primitive for the given Wrapper object:

    1. public byte byteValue()
    2. public short shortValue()
    3. public int intValue()
    4. public long longValue()
    5. public float floatValue()
    6. public float doubleValue()

 
```java
// Java program to illustrate bytevalue()  
class GFG { 
public static void main(String[] args) 
{  
Integer I = new Integer(130); 
System.out.println(I.byteValue());  
System.out.println(I.shortValue()); 
System.out.println(I.intValue());  
System.out.println(I.longValue());  
System.out.println(I.floatValue());  
System.out.println(I.doubleValue());  
}  

}

Output: 

-126
130
130
130
130.0
130.0
```
3. **parseXxx() method :** We can use parseXxx() methods to convert String to primitive. There are two types of parseXxx() methods:

- **primitive parseXxx(String s) :** Every Wrapper class 
except character class contains the following parseXxx() method to find 
primitive for the given String object.  
**Syntax:**

**public static primitive parseXxx(String s);**

 
```java
// Java program to illustrate parseXxx() 
class GFG {  

public static void  main(String[] args)  
{  
int i = Integer.parseInt("10");  

double d = Double.parseDouble("10.5");  

boolean b = Boolean.parseBoolean("true");         

System.out.println(i);         

System.out.println(d);         

System.out.println(b);  

}  

}      
Output: 

10
10.5
true
```
- **parseXxx(String s, int radix) :**
 Every Integral type Wrapper class (Byte, Short, Integer, Long) contains
 the following parseXxx() method to convert specified radix String to 
primitive.
**Syntax:**   

**public static primitive parseXxx(String s, int radix);**

 
```java
// Java program to illustrate parseXxx()  

   

class GFG {  
public static void main(String[] args)  
{  
int i = Integer.parseInt("1000",2);
long l = Long.parseLong("1111", 4);  
System.out.println(i);  
System.out.println(l);  
}  

}      
Output: 

8
85
```

4. **toString() method:**We can use toString() method to convert Wrapper object or primitive to String. There are few forms of toString() method:

    - **public String toString() :** Every wrapper class contains the following toString() method to convert Wrapper Object to String type.  
**Syntax:**

**public String toString();**

 ```java

// Java program to illustrate toString()    

class GFG {   
public static void main(String[] args)  
{  

Integer I = new Integer(10); 
String s = I.toString(); 
System.out.println(s);  
}  

}      
Output: 

10
```
- **toString(primitive p) :** Every Wrapper class including Character class contains the following static toString() method to convert primitive to String.  
**Syntax:**

**public static String toString(primitive p);**

 
```java
// Java program to illustrate toString() 
class GFG {  
public static void main(String[] args) 

{  
String s = Integer.toString(10); 
System.out.println(s);  

String s1 = Character.toString('a'); 
System.out.println(s1); 
}  

}      
Output: 

10
a
```
 - **toString(primitive p, int radix) : **Integer and Long classes contains the following toString() method to convert primitve to specified radix String.
**Syntax:** 

**public static String toString(primitive p, int radix);**
