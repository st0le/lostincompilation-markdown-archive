---
title: 'Subset Sum Problem - Medium'
date: 2013-06-04T14:52:00.001-07:00
draft: false
url: /2013/06/subset-sum-problem-medium.html
tags: 
- computer science
- algorithm
- medium
- interview question
---

  

> Problem : Given a set of integers A, find out if there is a subset of A which add up to a particular integer K.

  
Formally called the [Subset Sum Problem](http://en.wikipedia.org/wiki/Subset_sum_problem), we are given an NP-Complete problem. To solve this, we have to exhaustively search every subset and verify if they add up to an integer K.  
  
Let's begin with a Brute force DFS search, we're going to construct subsets incrementally until the sum exceeds K. The elements are assumed sorted in the increasing order.  
  

  
So we perform a DFS trying to perform every combination of the elements in the set. The recursive function either will include an element in the sum or exclude it. The guard prunes off DFS paths that exceed the sum required.  
  
There is an efficient method for this, using Dynamic Programming. Essentially, we start with a single element, add the next element together to get the new sums possible. These new sums will be the input for the next iteration. I'll explain with an example, say we have {a,b,c}  
  
  

*   You start with a set, lets call it _partial\_sums_ = {0}. For each element in the _partial\_sums_ we add _a_ to the set. So after one iteration we have {0,0+a} ie {0,a}
*   Now for _b_, repeat the procedure. This gives us _partial\_sums_ =  {0,a,b,a+b}
*   Finally, _c_ gives us {0,a,b,c,a+c,b+c,a+b+c}
*   Note : if any sum exceeds K we don't need to add it to the set (assuming the initial set was sorted, since the sum can only increase.)

Here's the solution implemented.

  

  
Here's the complete [gist](https://gist.github.com/st0le/5632403)