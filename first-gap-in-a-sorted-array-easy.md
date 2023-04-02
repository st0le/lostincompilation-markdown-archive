---
title: 'First gap in a Sorted Array - Easy'
date: 2013-04-25T22:04:00.001-07:00
draft: false
url: /2013/04/first-gap-in-sorted-array-easy.html
tags: 
- computer science
- python
- algorithm
- easy
- interview question
---

> Problem : Given an array of integers in strictly increasing order (no duplicates), find the first number not present in the array. Eg. \[11,12,13,25,37,49\] The output should be 14.

Seems simple enough? Let's go with our intuition first and use a naive algorithm.  
  
Time Complexity : O(n)  
  
Notice, if we don't have any gaps, say \[11,12,13,14,15\] then the upper bound of the array is equal to the highest - lowest element in the array. (4 = 15 - 11). So we can check if there is a gap simply by checking if  

> high - low == arr\[high\] - arr\[low\]

Let's be clever about this fact and solve this in O(logn). We use our trusty Binary Search but instead of "finding" an element we're going to partition the array into two halves. We first check if the First Half is "complete", if it is, we find the gap in the second half else we check the first half. We keep doing this till we have just 2 elements left (which is trivial to solve).  
  
Here's a recursive algorithm for the same, the iterative is just as easy.  
  

  
Note: I've returned -1 when the array is "complete", I could've returned arr\[high\] + 1 for more correctness.