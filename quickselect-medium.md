---
title: 'QuickSelect - Medium'
date: 2015-01-14T20:36:00.001-08:00
draft: false
url: /2015/01/quickselect-medium.html
tags: 
- computer science
- algorithm
- medium
- interview question
---

> Problem : Given an unsorted array, find the kth smallest element.

  
The problem is called the [Selection problem](http://en.wikipedia.org/wiki/Selection_algorithm). It's been intensively studied and has a couple of very interesting algorithms that do the job. I'll be  describing an algorithm called [QuickSelect](http://en.wikipedia.org/wiki/Quickselect). The algorithm derives its name from QuickSort. You will probably recognise that most of the code directly borrows from QuickSort. The only difference being there is a single recursive call rather than 2 in QuickSort.  
  
The naive solution is obvious, simply sort the array \`O(nlogn)\` and return the kth element. Infact, you can partially sort it and use the Selection sort to get the solution in \`O(nk)\`  
  
An interesting side effect of finding the kth smallest element is you end up finding the k smallest elements. This also effectively gives you (n - k) largest elements in the array as well. These elements are not in any particular order though.  
  
The version I'm using uses a random pivot selection, this part of the algorithm usually decides how fast it will be. Ideally you should pick the median, but calculating median of an array is basically a selection problem itself! (where k = n/2)  
  
So we usually use the cheap route and pick a random pivot. We use the \`partition\` function from \`quickSort\`to separate the array into 2 subarrays. The left one will contain all elements less than or equal to the pivot value. The right one will have elements greater than pivot.  
  
At this point we check if the k lies within \[0,pivotIndex\] or \[pivotIndex,n\].  
We then recurse in that direction, ignoring the other subarray , it doesn't interest us anymore since it won't have our solution.  

  

  
  
Complexity: **O(nlogn)** on average.  

  

Theoretically, It is possible to do this in **O(n)**. But the implementation hides huge constants and complexities which doesn't make it worth the effort.