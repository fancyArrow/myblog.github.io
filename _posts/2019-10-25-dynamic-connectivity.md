---
layout: post
title: Dynamic Connectivity
date: 2019-10-25 17:56 +0530
---

# Dynamic Connectivity 

* Given a set of N objects

 - Union Command `union(0 , 7)` 
 - Find/Connected Query `connected(8 , 9) ? returns wheteher there      is a connection or not` 
 - Equivalence Relation - Reflexive , Symmetric , Transitive

 

``` java
 public class UF{
     void union(int p , int q)
     boolean connected(int p , int q)
 }
 ```

# Algorithm - Eager Algorithm

 - Integer Array
 - Interpretation - p and q are connected then they have the same    id
 - Find is Simple
 - Union - Change all the entries whose id is id[p] to id[q]

 

``` java
 int[] id;
 int pId = id[p];
 int qid = id[q];

 for ( i : 0 to id.length){
     if(id[i] == pid)
     id[i] = qid;
 }
```

N square algorithm

# Optimization

* Integer array id[]
* Each element contains it's parent
* Union Connect is Easy set the id of p's root to the id of q's   root
* Weighted Quick Union Always the smaller tree goes below
* Depth is always lg2 N
* Path Compression (Make Flat Trees)

