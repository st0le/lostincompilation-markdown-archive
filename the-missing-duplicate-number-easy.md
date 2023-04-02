---
title: 'The Missing Duplicate Number - Easy'
date: 2013-04-13T19:13:00.000-07:00
draft: false
url: /2013/04/the-missing-duplicate-number-easy.html
tags: 
- computer science
- algorithm
- easy
- interview question
---

> Problem : Given an array of integers of odd length such that each element is repeated twice except for one. Find the non-repeating element. Eg. For array \[3,2,1,5,1,2,3\] the solution is 5.

  

A tiny variation of the question which doesn't really change the answer is as follows.

  

> Problem : Given an array of integers of odd length such that each element is repeated even number of times except for one element. Eg. For array \[1,5,5,1,2,2,4,4,4\] the solution is 4.

  

Let's begin with the naive solution, we use a Hash Table to keep track of the frequencies of my each element in the array. Finally, we find the element in the Hash Table with the odd frequency which is the solution required. The space and time complexity is O(n).

  

We'll try and reduce the space complexity. This is one of those questions which will be solved using our trusty Xor operator. You should know X ^ X = 0 and also Xor is Commutative and associative. ie X ^ Y is Y ^ X.

  

Therefore, (X ^ Y) ^ X is the same as (X ^ X) ^ Y => 0 ^ Y => Y

  

So if we run an Xor operation over the array elements, all the even repeated elements cancel each other and the odd repeated element remains. I won't post the code. [Here's](http://stackoverflow.com/a/4530530) another explanation I posted on Stackoverflow.