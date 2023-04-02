---
title: 'Shortest Interval in k-sorted list - Hard'
date: 2013-09-20T20:39:00.001-07:00
draft: false
url: /2013/09/shortest-interval-in-k-sorted-list-hard.html
tags: 
- hard
- computer science
- algorithm
- interview question
---

> Given k-sorted array, find the minimum interval such that there is at least one element from each array within the interval. Eg. \[1,10,14\],\[2,5,10\],\[3,40,50\]. Output : 1-3

  
To solve this problem, we perform a k-way merge as described [here](http://lostincompilation.blogspot.com/2013/09/merge-k-sorted-lists-medium.html). At each point of 'popping' an element from an array. We keep track of the minimum and maximum head element (the first element) from all the k-lists. The minimum and maximum will obviously contain the rest of the header elements of the k-arrays. As we keep doing this, we find the smallest interval (max - min). That will be our solution. Here's a pictorial working of the algorithm.  
  

[![](http://3.bp.blogspot.com/-8wuQx4DEYng/Uj0RnkbztNI/AAAAAAAACrI/4XRcQTZ7adg/s320/merge.PNG)](http://3.bp.blogspot.com/-8wuQx4DEYng/Uj0RnkbztNI/AAAAAAAACrI/4XRcQTZ7adg/s1600/merge.PNG)

  

And here's the Python code. Time Complexity : O(nlogk)