---
title: 'The 2 Missing Duplicate Numbers - Medium'
date: 2013-05-27T21:34:00.001-07:00
draft: false
url: /2013/05/the-2-missing-duplicate-numbers-medium.html
tags: 
- computer science
- algorithm
- medium
- interview question
---

  
This is a slightly trickier version of [The Missing Duplicate Number](http://lostincompilation.blogspot.com/2013/04/the-missing-duplicate-number-easy.html). Instead of one single missing number, we have 2.  
  

> Problem : Given an array of Integers. Each number is repeated even number of times. Except 2 numbers which occur odd number of times. Find the two numbers Ex. \[1,2,3,1,2,3,4,5\] The Output should be 4,5.

  
  
The naive solution is similar to the previous solution. Use a hash table to keep track of the frequencies and find the elements that occur an odd number of times. The algorithm has a Time and Space Complexity of O(n).  
  
Say those two required numbers are _a_ and _b_  
If you remember the previous post, we used the XOR over all the elements to find the required element. If we do the same here, we get a value _xor_ which is actually _a ^ b._  
  
So how can we use this? We know that _a_ and _b_ are different, so their xor is not zero. Infact their XOR value has its bit set for all its dissimilar bits in both _a_ and _b. (eg. _1101 ^ 0110 = 0011).  
  
It's important to notice here that each bit set in _xor_ corresponds to either _a_ or _b,_ but not both. So we isolate a single bit from _xor_  , say _mask,_ and run the original XOR algorithm only for those number whose bit  is set the same as _mask._ This list of elements will either have _a_ or _b._ depending on whether the bit was set due to _a_ or _b._ So the xor algorithm will return one of the numbers,say _xor\_1_. To obtain the other we simply _xor ^ xor\_1._  
_Example:_  
\[1,2,3,4,5,1,2,3\]  
  
xor = 1 ^ 2 ^ 3 ^ 4 ^ 5 ^ 1 ^ 2 ^3 = 1 _**( = 4 ^ 5)**_  
Notice, 4 = 0100  and 5 = 0101 , xor = 0001.  
  
In this case, since there's just one bit set, xor itself is the mask.  
Now, we calculate xor\_1. Ie XOR all number whose (v & mask) != 0  
  
xor\_1 = 1 ^ 3 ^ 5 ^ 1 ^ 3 = 5  
xor\_2 = xor ^ xor\_1 = 1 ^ 5 = 4  
  
We obtain (4,5) which occurred odd number of times.