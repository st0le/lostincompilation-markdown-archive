---
title: 'Merge k-sorted lists - Medium'
date: 2013-09-20T20:13:00.001-07:00
draft: false
url: /2013/09/merge-k-sorted-lists-medium.html
tags: 
- computer science
- algorithm
- medium
- interview question
---

  

> Problem - Given k-sorted lists, merge them into a single sorted list.

A daft way of doing this would be to copy all the list into a new array and sorting the new array. ie O(n log(n))  
  
The naive method would be to simply perform k-way merge similar to the auxiliary method in Merge Sort. But that is reduces the problem to a minimum selection from a list of k-elements. The Complexity of this algorithm is an abysmal O(nk).  
  
Here's how it looks in Python. We maintain an additional array called Index\[1..k\] to maintain the head of each list.

  
We improve upon this by optimizing the minimum selection process by using a familiar data structure, the Heap! Using a MinHeap, we extract the minimum element from a list and then push the next element from the same list into the heap, until all the list get exhausted.  
  
This reduces the Time complexity to O(nlogk) since for each element we perform O(logk) operations on the heap. An important implementation detail is we need to keep track of the origins of the elements of the heap, ie the list it came from and it's index. Therefore, I use a 3 member tuple (item, list-index, item-index) and push it onto the heap.  
  
Fortunately for us, Python has the heapq module for implementing a heap. So here's the code.

  
  
The entire code can be found [here](https://github.com/st0le/lost-in-compilation/blob/master/k_way_merge.py).