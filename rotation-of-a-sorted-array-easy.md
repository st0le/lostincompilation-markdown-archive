---
title: 'Rotation of a Sorted Array - Easy'
date: 2013-05-10T22:04:00.001-07:00
draft: false
url: /2013/05/rotation-of-sorted-array-easy.html
tags: 
- computer science
- algorithm
- easy
- interview question
---

  

> Problem : A Sorted Array is rotated by a certain number of elements, find the point of rotation. 

  
  
 Example, For \[3,4,5,1,2\] , since \[1,2\] was rotated to the back, point of rotation is 3. And of course, for a sorted array the point of rotation can be assumed 0.  
  
Naive Solution: This is pretty obvious Linear Solution, simply scan the array for a pair a\[i\] > a\[i+1\]. If we find it, _i_ is the point of rotation, if there's no such pair, then _i = 0_ clearly.  
  
Time Complexity : O(n)  
Binary Search Variant: Using a variation of Binary Search method, we can find the rotation point in O(logn) steps. At each iteration we compare the _middle_ element of the list with the _right_ (or left) element. For a rotated array, _arr\[left\] > arr\[right\]_, so every time we pick a middle element, the point of rotation can lie on either side of _mid_.  
  
If _arr\[mid\] > arr\[right\]_, it means the rotation point is in the second half of the array. So we move _left_ to _mid._ If _arr\[mid\] <= arr\[right\]_ then the rotation point lies in the first half of the array.