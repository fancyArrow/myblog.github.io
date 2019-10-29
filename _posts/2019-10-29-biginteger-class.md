---
layout: post
title: BigInteger Class
date: 2019-10-29 17:13 +0530
---
BigInteger class is used for mathematical operation which involves very big integer calculations that are outside the limit of all available primitive data types.

For example factorial of 100 contains 158 digits in it so we can’t store it in any primitive data type available. We can store as large Integer as we want in it. There is no theoretical limit on the upper bound of the range because memory is allocated dynamically but practically as memory is limited you can store a number which has Integer. MAX_VALUE number of bits in it which should be sufficient to store mostly all large values.

Below is an example Java program that uses BigInteger to compute Factorial.

``` java
// Java program to find large factorials using BigInteger 
import java.math.BigInteger; 
import java.util.Scanner; 

public class Example 
{ 
	// Returns Factorial of N 
	static BigInteger factorial(int N) 
	{ 
		// Initialize result 
		BigInteger f = new BigInteger("1"); // Or BigInteger.ONE 

		// Multiply f with 2, 3, ...N 
		for (int i = 2; i <= N; i++) 
			f = f.multiply(BigInteger.valueOf(i)); 

		return f; 
	} 

	// Driver method 
	public static void main(String args[]) throws Exception 
	{ 
		int N = 20; 
		System.out.println(factorial(N)); 
	} 
} 

```

``` java

Now below is given a list of simple statements in primitive arithmetic and its analogous statement in terms of BigInteger objects.

Declaration

int a, b;                
BigInteger A, B; 

Initialization:

 
a = 54;
b = 23;
A  = BigInteger.valueOf(54);
B  = BigInteger.valueOf(37); 

And for Integers available as string you can initialize them as:

A  = new BigInteger(“54”);
B  = new BigInteger(“123456789123456789”); 

Some constant are also defined in BigInteger class for ease of initialization :

A = BigInteger.ONE;
// Other than this, available constant are BigInteger.ZERO 
// and BigInteger.TEN 
Mathematical operations:
int c = a + b;
BigInteger C = A.add(B); 

Other similar function are subtract() , multiply(), divide(), remainder()
But all these function take BigInteger as their argument so if we want these operation with integers or string convert them to BigInteger before passing them to functions as shown below:

String str = “123456789”;
BigInteger C = A.add(new BigInteger(str));
int val  = 123456789;
BigInteger C = A.add(BigInteger.valueOf(val)); 

```
# Methods of BigInteger Class:
* BigInteger abs(): This method returns a BigInteger whose value is the absolute value of this BigInteger.
* BigInteger add(BigInteger val): This method returns a BigInteger whose value is (this + val).
* BigInteger and(BigInteger val): This method returns a BigInteger whose value is (this & val).
* BigInteger andNot(BigInteger val): This method returns a BigInteger whose value is (this & ~val).
* int bitCount(): This method returns the number of bits in the two’s complement representation of this BigInteger that differ from its sign bit.
* int bitLength(): This method returns the number of bits in the minimal two’s-complement representation of this BigInteger, excluding a sign bit.
* byte byteValueExact(): This method converts this BigInteger to a byte, checking for lost information.
* BigInteger clearBit(int n): This method returns a BigInteger whose value is equivalent to this BigInteger with the designated bit cleared.
* int compareTo(BigInteger val): This method compares this BigInteger with the specified BigInteger.
* BigInteger divide(BigInteger val): This method returns a BigInteger whose value is (this / val).
* BigInteger[] divideAndRemainder(BigInteger val): This method returns an array of two BigIntegers containing (this / val) followed by (this % val).
* double doubleValue(): This method converts this BigInteger to a double.
* boolean equals(Object x): This method compares this BigInteger with the specified Object for equality.
* BigInteger flipBit(int n): This method returns a BigInteger whose value is equivalent to this BigInteger with the designated bit flipped.
* float floatValue(): This method converts this BigInteger to a float.
* BigInteger gcd(BigInteger val): This method returns a BigInteger whose value is the greatest common divisor of abs(this) and abs(val).
* int getLowestSetBit(): This method returns the index of the rightmost (lowest-order) one bit in this BigInteger (the number of zero bits to the right of the rightmost one bit).
* int hashCode(): This method returns the hash code for this BigInteger.
* int intValue(): This method converts this BigInteger to an int.
* int intValueExact(): This method converts this BigInteger to an int, checking for lost information.
* boolean isProbablePrime(int certainty): This method returns true if this BigInteger is probably prime, false if it’s definitely composite.

``` java
// A Java program to check if a number is prime using 
// inbuilt function 
import java.util.*; 
import java.math.*; 

class CheckPrimeTest 
{ 
	//Function to check and return prime numbers 
	static boolean checkPrime(long n) 
	{ 
		// Converting long to BigInteger 
		BigInteger b = new BigInteger(String.valueOf(n)); 

		return b.isProbablePrime(1); 
	} 

	// Driver method 
	public static void main (String[] args) 
						throws java.lang.Exception 
	{ 
	long n = 13; 
	System.out.println(checkPrime(n)); 
	} 
} 

```

* long longValue(): This method converts this BigInteger to a long.
* long longValueExact(): This method converts this BigInteger to a long, checking for lost information.
* BigInteger max(BigInteger val): This method returns the maximum of this BigInteger and val.
* BigInteger min(BigInteger val): This method returns the minimum of this BigInteger and val.
* BigInteger mod(BigInteger m): This method returns a BigInteger whose value is (this mod m).
* BigInteger modInverse(BigInteger m): This method returns a BigInteger whose value is (this-1 mod m).
* BigInteger modPow(BigInteger exponent, BigInteger m): This method returns a BigInteger whose value is (thisexponent mod m).
* BigInteger multiply(BigInteger val): This method returns a BigInteger whose value is (this * val).
* BigInteger negate(): This method returns a BigInteger whose value is (-this).
* BigInteger nextProbablePrime(): This method returns the first integer greater than this BigInteger that is probably prime.
* BigInteger not(): This method returns a BigInteger whose value is (~this).
* BigInteger or(BigInteger val): This method returns a BigInteger whose value is (this | val).
* BigInteger pow(int exponent): This method returns a BigInteger whose value is (thisexponent).
* static BigInteger probablePrime(int bitLength, Random rnd): This method returns a positive BigInteger that is probably prime, with the specified bitLength.
* BigInteger remainder(BigInteger val): This method returns a BigInteger whose value is (this % val).
* BigInteger setBit(int n): This method returns a BigInteger whose value is equivalent to this BigInteger with the designated bit set.
* BigInteger shiftLeft(int n): This method returns a BigInteger whose value is (this << n).
* BigInteger shiftRight(int n): This method returns a BigInteger whose value is (this >> n).
* short shortValueExact(): This method converts this BigInteger to a short, checking for lost information.
* int signum(): This method returns the signum function of this BigInteger.
* BigInteger sqrt(): This method returns the integer square root of this BigInteger.
* BigInteger[] sqrtAndRemainder(): This method returns an array of two BigIntegers containing the integer square root s of this and its remainder this – s*s, respectively.
* BigInteger subtract(BigInteger val): This method returns a BigInteger whose value is (this – val).
* boolean testBit(int n): This method returns true if and only if the designated bit is set.
* byte[] toByteArray(): This method returns a byte array containing the two’s-complement representation of this BigInteger.
* String toString(): This method returns the decimal String representation of this BigInteger.
* String toString(int radix): This method returns the String representation of this BigInteger in the given radix.
* static BigInteger valueOf(long val): This method returns a BigInteger whose value is equal to that of the specified long.
* BigInteger xor(BigInteger val): This method returns a BigInteger whose value is (this ^ val).
