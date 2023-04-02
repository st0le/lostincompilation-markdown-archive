---
title: 'The 3n + 1 Problem - Easy'
date: 2013-04-20T20:50:00.000-07:00
draft: false
url: /2013/04/the-3n-1-problem-easy.html
tags: 
- computer science
- UVa
- algorithm
- online judge
- easy
---

Find the problem statement [here](http://uva.onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=36).  
  
The 3n + 1 problem is also known as [The Collatz Conjecture](http://en.wikipedia.org/wiki/Collatz_conjecture) in Mathematics. The problem is simple, you are given a positive integer 'n'. We perform the following operations.  
  
  

*   If n = 1, Stop
*   If n is even, n = n / 2
*   If n is odd, n = 3 \* n + 1

The problem statement asks to count the number of iterations we need to perform till we get to 1. (Note : 0 is a corner case.)

  

It's a Conjecture because it's still hasn't been proved that every number will end up at 1. 

  

I've decided to approach UVaOJ with C++ so that I can brush up my C++ skills. Here's my [solution](https://github.com/st0le/UVa/blob/master/100.cpp).

  

I've used recursion combined with memoization. Memoization is a type of dynamic programming. It's kind of a cache memory which stores solutions to already solved subproblems so that you don't need to solve them again.

  

Comments are welcome! Cheers.