---
title: 'Find Increasing Triplet Subsequence - Medium'
date: 2013-09-20T18:39:00.004-07:00
draft: false
url: /2013/09/find-increasing-triplet-subsequence.html
tags: 
- computer science
- algorithm
- medium
- interview question
---

  

> Problem - Given an integer array A\[1..n\], find an instance of i,j,k where 0 < i < j < k <= n and A\[i\] < A\[j\] < A\[k\].

  
Let's start with the obvious solution, bruteforce every three element combination until we find a solution.  
  
Let's try to reduce this by searching left and right for each element, we search left for an element smaller than the current one, towards the right an element greater than the current one. When we find an element that has both such elements, we found the solution. The complexity of this solution is O(n^2).  
To reduce this even further, One can simply apply the [longest increasing subsequence](http://lostincompilation.blogspot.com/2013/06/longest-increasing-subsequence-hard.html) algorithm and break when we get an LIS of length 3. But the best algorithm that can find an LIS is [O(nlogn) with O( n ) space](http://lostincompilation.blogspot.com/2013/06/longest-increasing-subsequence-part-2.html).  
  
An O(nlogn) algorithm seems like an overkill! Can this be done in linear time?  
  
**The Algorithm:**  
We iterate over the array and keep track of two things.  

*   The minimum value iterated over (min)
*   The minimum increasing pair (a,b) where min <= a < b

When we encounter an element, say _v,_  that is greater than the increasing pair we return _(a,b,v)._

Here's my Python implementation to make my point.  
  

Until next time, Cheers!
---
### Comments:
#### Good job, I really like the way you explained. For...
[Unknown](https://www.blogger.com/profile/03412156521022627981 "noreply@blogger.com") - <time datetime="2013-10-30T21:46:45.897-07:00">Oct 3, 2013</time>

Good job, I really like the way you explained. For the last implementation, I think you should change to "elif b == None or b >= v" otherwise it will fail on \[3,2,4,4\]
<hr />
#### It has to fail for \[3,2,4,4\]...The question clearl...
[st0le](https://www.blogger.com/profile/15083108270235504315 "noreply@blogger.com") - <time datetime="2013-11-01T14:52:48.747-07:00">Nov 5, 2013</time>

It has to fail for \[3,2,4,4\]...The question clearly states the triple should be strictly increasing.
<hr />
