---
layout: post
title: Binary Search Tree
date: 2019-10-26 14:20 +0530
---

# Binary Search Tree

 - A BST is a binary tree in symmetric order
 - A binary tree

  1. Empty
  2. Node + left link + right link
  3. two disjoint binary trees (left and right)
* Symmetric Tree

 1. Each node has a key and every node's key is
 2.larger than all keys in it's left subtree
 2. Smaller than all keys in it's right subtree

 # Node
 

``` java
private class Node{
    private Key key;
    private Value val;
    private Node left , right;
    //private int count;
    public Node(Key key , Value val){
        this.key = key;
        this.val = val;
    }
}
```

# BST Implementation

``` java
public class BST<Key extends Comparable<Key> , Value>{
    private Node root;
    private class Node{
       //same as above
    }
    public void put(Key key , Value val){
         root = put(root, key ,val;)       
    }
    private Node put (Node x , Key key , Value val){
        if(x == null)
            return new Node(key , val)
        int cmp = key.compareTo(x.key);
        if( cmp < 0){
            x.left = put(x.left , key , val);
        }
        else if( cmp > 0){
            x.right = put(x.right , key , val);
        }
        else
            x.val = val;
        //x.count = 1 + size(x.left) + size(x.right);
        return x;
    }
    public Value get(Key key){
      Node x = root;
      while(x != null){
          int cmp = key.compareTo(x.key);
          if(cmp < 0)
            x = x.left;
          else if (cmp > 0){
              x = x.right;
          }
          else{
              return x.val;
          }
          return null;
      }
    }
    //Hibbard Deletion
    public void delete(Key key){
        //set its value is null
        //leave key in tree to guide searches (but dont'c consider it in search)
        root = delete(root, key);        
    }
    private Node delete(Node x , Key key){
        if(x == null)
            return null;
        int cmp = key.compareTo(x.key);
        if(cmp < 0)
            x.left = delete(x.left , key);
        else if(cmp > 0)
            x.right = delete(x.right , key);
        else{
            if(x.right == null)
                return x.left;
            if(x.left == null)
                return x.right;
            Node t = x;
            x = min(t.right);
            x.right = deleteMin(t.right);
            x.left = t.left;
        }
        x.count = size(x.left) + size(x.right) + 1;
        return x;
    }
    public void deleteMin(){
        root = deleteMin(root);
    }
    private Node deleteMin(Node x){
        if(x.left == null)
            return x.right;
        x.left = deleteMin(x.left);
        x.count = 1 + size(x.left) + size(x.right);
        return x;
    }
    public Iterable<Key> iterator(){
        Queue<Key> q = new Queue<Key>();
        inorder(root , q);
        return q;
    }
    private void inorder(Node x , Queue<Key> q){
        if(x == null)
            return;
        inorder(x.left , q);
        q.enqueue(x.key);
        inorder(x.right , q);
    }
    public Key floor(Key key){
        Node x = floor(root, key);
        if(x == null)
            return null;
        return x.key;
    }
    private Node floor(Node x , Key key){
        if(x == null)
            return null;
        int cmp = key.compareTo(x.key);
        if(cmp == 0)
            return x;
        if (cmp < 0)
            return floor(x.left , key);
        Node t = floor(x.right , key);
        if(t != null){
            return t;
        }
        else
            return x;
    }
    public int size(){
        return size(root);
    }
    private int size(Node x){
        if(x == null)
            return 0;
        return x.count;
    }
    public int rank (Key key){
        return rank(Key key , Node x);
    }
    private int rank(Rank rank , Node x){
        if(x == null)
            return 0;
        int cmp = key.compareTo(x.key);
        if(cmp < 0)
            return rank (key , x.left);
        else if(cmp > 0){
            return 1 + size(x.left) + rank(key , x.right);
        }
        else
            return size(x.left);
    }
}
//cost is 1 + depth
//tree shape depends on the order of input
//Minimum
//Maximum
//rank -> In each node , we store the number of nodes in the //subtree rooted at that node , to implement size() , return the //count at node
//select
```

