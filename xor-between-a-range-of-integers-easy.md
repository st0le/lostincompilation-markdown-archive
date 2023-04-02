---
title: 'XOR between a Range of Integers - Easy'
date: 2013-04-12T16:11:00.003-07:00
draft: false
url: /2013/04/xor-between-range-of-integers.html
tags: 
- computer science
- algorithm
- easy
- interview question
---

>   
> Problem : Given two integers a and b (a <= b ). Find the value of a ^ (a+1) ^ ... (b-1) ^ b. (^ is the xor operator).

  
This will be a short post. It's pretty trivial once you understand the pattern. I'd first refer you to [this post](http://onlyalgorithms.blogspot.com/2013/04/the-missing-number.html) first. In the alternate solutions, I've described how you can obtain the value of 1 ^ 2 ^ 3 .... ^ N.  
  
Therefore, our solution simply applies that concept.  
  
xor(b) ^ xor(a - 1) where xor function is implemented in Python as follows  
  
For Python, this will work for negative integers as well, since the mod operator always returns a positive integer. For other languages, make sure you make appropriate changes to the xor() function. Until next time...