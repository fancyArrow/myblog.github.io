---
layout: post
title: Applications of Binary Trees
date: 2019-10-28 12:05 +0530
---

# Intersection among geometric objects

* Range Search And Range Count
* id rabge count : How many keys between lo and hi
* Range Count

``` java
public int size(Key lo , Key hi){
    if(contains(hi))
        return rank(hi) - rank(lo) + 1;
    else
        return rank(hi) - rank(lo);
}
```

* Range Search

 - Modification of the elemntary search operation

 # Intersection among line segment 

  + Brute Force - Quadratic 
  + *Sweep Line Algorithm*
  + Verical Line sweeps from left to right
  + X coordinates define events
  + h-segment (left endpoint) : insert y - coordinate into BST
  + right endpoint - remove the point
  + when we hit a vertical line - Range Search for its y - co-ordinates

  # KD - Trees
   - Extension of ordered symbol-table to 2d keys
   - All operations like (insert , search , range search , range count)
   - Find the points in a rectangle
   - Recursivley partion plane into two half planes

## Count BST nodes that lie in a given range

Given a Binary Search Tree (BST) and a range, count number of nodes that lie in the given range.

The idea is to traverse the given binary search tree starting from 
root. For every node being visited, check if this node lies in range, 
if yes, then add 1 to result and recur for both of its children. If 
current node is smaller than low value of range, then recur for right 
child, else recur for left child.

``` java
// Java code to count BST nodes that   
// lie in a given range   
class BinarySearchTree {   
  
    /* Class containing left and right child   
    of current node and key value*/  
    static class Node {   
        int data;   
        Node left, right;   
  
        public Node(int item) {   
            data = item;   
            left = right = null;   
        }   
    }   
  
    // Root of BST   
    Node root;   
  
    // Constructor   
    BinarySearchTree() {   
        root = null;   
    }   
      
    // Returns count of nodes in BST in   
    // range [low, high]   
    int getCount(Node node, int low, int high)   
    {   
        // Base Case   
        if(node == null)   
            return 0;   
  
        // If current node is in range, then   
        // include it in count and recur for   
        // left and right children of it   
        if(node.data &gt;= low && node.data &lt;= high)   
            return 1 + this.getCount(node.left, low, high)+   
                this.getCount(node.right, low, high);   
                  
        // If current node is smaller than low,   
        // then recur for right child   
        else if(node.data &lt; low)   
            return this.getCount(node.right, low, high);   
          
        // Else recur for left child   
        else  
            return this.getCount(node.left, low, high);       
    }   
  
    // Driver function   
    public static void main(String[] args) {   
        BinarySearchTree tree = new BinarySearchTree();   
          
        tree.root = new Node(10);   
        tree.root.left     = new Node(5);   
        tree.root.right     = new Node(50);   
        tree.root.left.left = new Node(1);   
        tree.root.right.left = new Node(40);   
        tree.root.right.right = new Node(100);   
        /* Let us constructed BST shown in above example   
        10   
        / \   
    5     50   
    /     / \   
    1     40 100 */  
    int l=5;   
    int h=45;   
    System.out.println("Count of nodes between [" + l + ", "  

                    + h+ "] is " + tree.getCount(tree.root,   

                                                l, h));   
    }   
}   
// This code is contributed by Kamal Rawal

```

## Return the Keys that lie in the range

The idea is to use the inorder traversal, as inorder traversal of a BST gives the keys in sorted order.

Algorithm:

1. If value of root’s key is greater than k1, then recursively call in left subtree.
2. If value of root’s key is in range, then print the root’s key.
3. If value of root’s key is smaller than k2, then recursively call in right subtree.

``` java
// Java program to print BST in given range 

// A binary tree node 
class Node { 

	int data; 
	Node left, right; 

	Node(int d) { 
		data = d; 
		left = right = null; 
	} 
} 

class BinaryTree { 
	
	static Node root; 
	
	/* The functions prints all the keys which in the given range [k1..k2]. 
	The function assumes than k1 < k2 */
	void Print(Node node, int k1, int k2) { 
		
		/* base case */
		if (node == null) { 
			return; 
		} 

		/* Since the desired o/p is sorted, recurse for left subtree first 
		If root->data is greater than k1, then only we can get o/p keys 
		in left subtree */
		if (k1 < node.data) { 
			Print(node.left, k1, k2); 
		} 

		/* if root's data lies in range, then prints root's data */
		if (k1 <= node.data && k2 >= node.data) { 
			System.out.print(node.data + " "); 
		} 

		/* If root->data is smaller than k2, then only we can get o/p keys 
		in right subtree */
		if (k2 > node.data) { 
			Print(node.right, k1, k2); 
		} 
	} 
	

	public static void main(String[] args) { 
		BinaryTree tree = new BinaryTree(); 
		int k1 = 10, k2 = 25; 
		tree.root = new Node(20); 
		tree.root.left = new Node(8); 
		tree.root.right = new Node(22); 
		tree.root.left.left = new Node(4); 
		tree.root.left.right = new Node(12); 

		tree.Print(root, k1, k2); 
	} 
} 

// This code has been contributed by Mayank Jaiswal 

```

# Line Sweep

## Given n line segments, find if any two segments intersect

We have discussed the problem to detect if[ two given line segments intersect or not](https://www.geeksforgeeks.org/check-if-two-given-line-segments-intersect/). In this post, we extend the problem. Here we are given n line segments and we need to find out if any two line segments intersect or not.

**Naive Algorithm** A naive solution to solve this problem is to check every pair of lines and check if the pair intersects or not.[We can check two line segments in O(1) time](https://www.geeksforgeeks.org/check-if-two-given-line-segments-intersect/). Therefore, this approach takes O(n)
**Sweep Line Algorithm:** We can solve this problem in **O(nLogn)**
 time using Sweep Line Algorithm. The algorithm first sorts the end 
points along the x axis from left to right, then it passes a vertical 
line through all points from left to right and checks for intersections.
 Following are detailed steps.

1. Let there be n given lines. There must be 2n end 

points to represent the n lines. Sort all points according to x 
coordinates. While sorting maintain a flag to indicate whether this 
point is left point of its line or right point.

2. Start from the leftmost point. Do following for every point - If the current point is a left point of its line 

segment, check for intersection of its line segment with the segments 
just above and below it. And add its line to _active_ line 
segments (line segments for which left end point is seen, but right end 
point is not seen yet). Note that we consider only those neighbors 
which are still active.

* If the current point is a right point, remove its 

line segment from active list and check whether its two active neighbors
 (points just above and below) intersect with each other.

The step 2 is like passing a vertical line from all points starting 
from the leftmost point to the rightmost point. That is why this 
algorithm is called Sweep Line Algorithm. The Sweep Line technique is 
useful in many other geometric algorithms like [calculating the 2D Voronoi diagram ](http://cgm.cs.mcgill.ca/~mcleish/644/Projects/DerekJohns/Sweep.htm)

**What data structures should be used for efficient implementation?**  

In step 2, we need to store all active line segments. We need to do following operations efficiently:  

a) Insert a new line segment  

b) Delete a line segment  

c) Find predecessor and successor according to y coordinate values  

The obvious choice for above operations is Self-Balancing Binary Search 
Tree like AVL Tree, Red Black Tree. With a Self-Balancing BST, we can do
 all of the above operations in O(Logn) time.

Also, in step 1, instead of sorting, we can use min heap data structure.
 Building a min heap takes O(n) time and every extract min operation 
takes O(Logn) time (See [this](http://courses.csail.mit.edu/6.006/spring11/lectures/lec24.pdf)).

**PseudoCode:**  

The following pseudocode doesn’t use heap. It simply sort the array.

**sweepLineIntersection(Points[0..2n-1]):

1. Sort Points[] from left to right (according to x coordinate)

2. Create an empty Self-Balancing BST T. It will contain all active line Segments ordered by y coordinate.

// Process all 2n points

``` java

3. for i = 0 to 2n-1

// If this point is left end of its line 
if(Points[i].isLeft) 
       T.insert(Points[i].line()) 
// Insert into the tree// Check if this points intersects with its predecessor and successor
if ( doIntersect(Points[i].line(), T.pred(Points[i].line()) )
         return true
if ( doIntersect(Points[i].line(), T.succ(Points[i].line()) )
         return true
else 
// If it's a right end of its line
// Check if its predecessor and successor intersect with each other
if ( doIntersect(T.pred(Points[i].line(), T.succ(Points[i].line()))
         return true
T.delete(Points[i].line())  // Delete from tree
return False
```

# Interval Search Trees

 - Insert an interval (lo , hi)
 - Search for an Interval (lo , hi)
 - Delete an Interval (lo , hi)
 - Interval Intersection Query : Given an interval (lo , hi) find all intervals or one interval in data structire that intersects (lo , hi)

  + Use left endpoint as BST key
  + Store max Endpoint in subtree rooted at node
  + To insert an interval (lo , hi)
  1. Insert into BST using lo as key
  2. Update max in each node on search path
  + Interval Search
  1. If interval in node intersetc query interval return it
  + else if left subtree is null go right
  + else if max endpoint in left subtree is less than lo go right
  + else go left

  

``` java
  Node x = root;
  while(x != null){
      if(x.interval.instersects(lo , hi))
        return x.interval;
      else if(x.left == null)
        x = x.right;
      else if (w.left.max < lo)
        x = x.right;
    else
        x = x.left;
  }
  return null;
  ```

 # Rectangle Intersection

  + Find all intersections among a set of N orthognal rectangles

   1. Sweep vertical line from left to right
   - x-coordinates of left and right endpoints define events
   - Maintain a set of rectangles that interset the sweep line in an interval search tree (using y intervals of the rectangle)
   - Left endpoint : Interval search for y -interval of the rectang; e 
   Insert the y -interval
   - Right endpoint : remove y-interval

