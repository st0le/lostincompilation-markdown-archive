---
title: 'Minimum Hops - Medium '
date: 2013-06-19T19:32:00.002-07:00
draft: false
url: /2013/06/minimum-hops-medium.html
tags: 
- computer science
- algorithm
- medium
- interview question
---

> Problem: Given an array of positive non-zero integers. Find out the minimum hops required to traverse the array, if the value at an index denotes the maximum length you can hop from that index.

  

  

To perform a brute force solution, we can use a depth first search with pruning. This usually explodes with arrays of size greater than 50. But never the less, it's important to understand how it works.  
  
Following our dismal performance using DFS, we move on to the big guns, Dynamic Programming. We define _minHop\[i\]  _as the minimum hops you need from index _i_ to reach the end of the array.  
  
Therefore,  
  
minHop\[i\] = 1 { if arr\[i\] + i > len(arr) } needs just one hop, trivial.  
minHop\[i\] = 1 + min ( minHop\[i+1 : i+arr\[i\]\] ) { the minimum hop from my range which will reach the end of the array }  
  
We start with i = len(arr) - 1 and count down to _i  = 0_ . At which point minHop\[0\] will be the minimum hops required to reach the end of the array from index = 0.

So here we have an O(n^2) solution, at the expense of O(n) space. Until Next time.