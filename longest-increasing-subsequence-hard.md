---
title: 'Longest Increasing Subsequence - Hard'
date: 2013-06-08T01:47:00.000-07:00
draft: false
url: /2013/06/longest-increasing-subsequence-hard.html
tags: 
- hard
- computer science
- algorithm
- interview question
---

  

> Problem - Given an array of integers. Find the longest increasing subsequence in the array. Eg. \[42, 91, 46, 73, 75, 91, 95\]. The LIS for this array is 6 which is \[42,46,73,75,91,95\]. Note: Subsequence does not require the elements to be contiguous

  
As always, we begin with our naive solution which is a DFS/Bruteforce search trying every possible combination until we get the longest sequence. This is simply exhaustive and will explode on bigger arrays. Time Complexity : O(2^n) ~ Exponential  
  
Now, If you notice we repeatedly try a prefix subsequence repeatedly. This tells us, the problem is a good candidate for a dynamic programming algorithm.  
  
We define _lis\[0...L\]_, where L is the length of the array. We define _lis\[i\]_ as the length of longest increasing subsequence that ends at _i. _  
  

*   lis\[0\] = 1 { trivial since, the longest increasing sequence that ends at the start of the array contains just the first element, also true for the arr\[i\] where arr\[i\] is the smaller than preceding elements}
*   lis\[i\] = 1 + max( lis\[j = 0..i-1\] where A\[i\] > A\[j\] ) 

To calculate _lis\[i\],_ we have a new element A\[i\] which can be part of a new LIS by appending to an existing LIS ending at _j_ where j varies from 0 to i - 1 if and only if, A\[i\] > A\[j\]. If there is no such element, ie A\[i\] is smaller than A\[0..i-1\] therefore, lis\[i\] = 1  
To build back the LIS, we also store a _prev\[\]_ array, which holds the preceding index of the previous member of the LIS. The _prev_ for the first element will be marked as negative to indicate termination. We build the LIS backwards and finally reverse the sequence.  
  
Time Complexity : O(n^2)

  
  
I'll end this post here, but I will follow up with a O(nlogn) method which can be used to solve the problem as well. I will also describe the applications and some problems you can solve using LIS. Until next time.