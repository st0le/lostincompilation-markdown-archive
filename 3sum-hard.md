---
title: '3SUM - Hard'
date: 2013-06-29T18:53:00.000-07:00
draft: false
url: /2013/06/3sum-hard.html
tags: 
- hard
- computer science
- algorithm
- interview question
---

  

> Problem - Given an Array of integers, A. Find out if there exists a triple (i,j,k) such that _A\[i\] + A\[j\] + A\[k\] == 0._

The [3SUM](http://en.wikipedia.org/wiki/3SUM) problem is very similar to the [2SUM](http://lostincompilation.blogspot.com/2013/06/2sum-medium.html) problem in many aspects. The solutions I'll be discussing are also very similar. I highly recommend you read the previous post first, since I'll explain only the differences in the algorithm from the previous post.  
  
Let's begin, We start with the naive algorithm. An O(n^3) solution with 3 nested loops each checking if the sum of the triple is 0. Since O(n^3) is the higher order term, we can sort the array in O(nlogn) and add a guard at the nested loops to prune of parts of the arrays. But the complexity still remains O(n^3).  
  
The code is pretty simple and similar to the naive algorithm of 2SUM.  
  
  

Moving on, we'll do the same thing we did in 2SUM, replace the inner-most linear search with a binary search. The Complexity now drops to O(n^2 logn)  
  
  

Now, the hash table method, this is strictly not the same as the previous problem, here we have to store the pair associated with the sum, hence I switch to a HashMap instead of a set. Also we need to store the pairs for each _i_ and clear the map when we pick a new starting element.  
  
  

 Note. This time we don't need the array to sorted. We can do it ourselves, since our overall complexity is going to be O(n^2), a sort call will only cost us O(nlogn) which is a lower order term.  
  
And now finally, we're going to use the _left-right _method (for lack of a better name).This time we keep one element as a constant and then for each element A\[i\], we run the 2SUM Linear Algorithm for A\[i+1...n\] That gives us a O(n^2) algorithm.  
  
  

The Entire source code can be found [here](https://github.com/st0le/lost-in-compilation/blob/master/ThreeSum.java).