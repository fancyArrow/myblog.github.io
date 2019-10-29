---
layout: post
title: Advanced Binary Search Trees
date: 2019-10-27 14:37 +0530
---

# 2-3 Search Tree

* Allow 1 or 2 keys per node
* left(less) + middle(between) + more(right)
* 2 node : one key , two children
* 3 node : two keys , three children# Red Black Trees Left Leaning Trees
* Represent 2-3 Trees as a BST.
* Use internal left leaning links as a glue for 3-node
* No Node has two red links connected to it
* Every Path from root to null link has the same number of black links
* Red Links lean left# Search is the same as for elementary BST (ignore colour)

``` java
public Val get(Key key){
    Node x = root;
    while(x != null){
        int cmp = key.comapreTo(x.key);
        if(cmp < 0 )
            x = x.left;
        else if (cmp > 0)
            x = x.right;
        else
            return x.val;
    }
    return null;
}
//Most other ops (ceiling ,selection ) are also identical
```

# Red Black Tree Representation

* Each Node is poinyted to by precisely one link(from it's parent)
* can encode color of links in nodes

``` java
private static final boolean RED = true;
private static final boolean BLACK = false;
private class Node{
    Key key;
    Value val;
    Node left , right;
    boolean colour; // colour of parent link
}
private boolean isRed(Node x){
    if(x == null)
        return false;
    return x.colour == RED;
}
```

# Left Rotation : Orient a temporarily right leaning red link to lean left

``` java
private Node rotateLeft(Node x){
    assert isRed(h.right);
    Node x = h.right;
    h.right = x.left;
    x.left = h;
    x.colour = h.colour;
    h.colour = RED;
    return x;
}
```

# Right Rotation : Orient a left leaning red link to lean right temporarily

``` java
private Node rotateRight(Node h){
    assert isRed(h.left);
    Node x = h.left;
    h.left = x.right;
    x.right = h;
    x.colour = h.colour;
    h.colour = RED;
    return x;
}
```

# Colour FLip : Recolour to split a temporary 4-node

``` java
private void flipColours(Node h){
    assert isRed(h.right);
    assert isRed(h.left);
    assert !isRed(h);
    h.colour = RED;
    h.left.colour = BLACK;
    h.right.colour = BLACK;
}
```

# Standard Insert Code That Handles All Cases

``` java
private Node put(Node h , Key key , Value val){
    if(h == null)
        return new Node(key , val ,RED);
    int cmp = key.compareTo(h.key);
    if(cmp < 0) h.left = put(h.left , key ,val);
    else if(cmp > 0) h.right = put(h.right , key , val);
    else h.val = val;
    if(isRed(h.right) && !isRed(h.left))
        h = rotateLeft(h);
    if(isRed(h.left) && isRed(h.left.left))
        h = rotateRight(h);
    if(isred(h.left) && isRed(h.right))
        flipcolours(h);

    return h;
}
```

