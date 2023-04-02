---
title: 'Maximizing the Difference - Medium'
date: 2013-05-17T22:42:00.000-07:00
draft: false
url: /2013/05/maximizing-difference-medium.html
tags: 
- computer science
- algorithm
- medium
- interview question
---

> Problem : Given an array A of integers, maximize A\[j\] - A\[i\] such that 0 <= i < j < len(A).

  
A very interesting problem, as always lets begin with a naive solution.  
  
Clearly, the solution has quadratic time complexity. Now, step back and look at the solution. Essentially what we are doing is iterating over the array, splitting the array into two parts. From the first part we always pick the lowest element, (clearly since that will give us the maximum difference). Since we already know the minimum element we encountered, we simply need to check if the difference with the new element improves upon the earlier solution. This idea can be implemented in Linear Time. Here's how.  
  
  
**Update**: So I just discovered this problem is called the Single Sell Profit problem. It's been discussed quite thoroughly by templatetypedef [here](http://stackoverflow.com/a/7086577/216517). It includes 4 solutions (including this one).