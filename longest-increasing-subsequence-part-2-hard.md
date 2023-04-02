---
title: 'Longest Increasing Subsequence - Part 2 - Hard'
date: 2013-06-24T17:36:00.001-07:00
draft: false
url: /2013/06/longest-increasing-subsequence-part-2.html
tags: 
- hard
- computer science
- algorithm
- interview question
---

As promised, this is the follow up to the first posted earlier that there was a more efficient algorithm for finding the longest increasing subsequence, better than the O(n^2) DP solution we came up with.  
  
It's not easy to understand, but once you get what the variables mean, it seems pretty straight forward. We'll be implementing another DP solution, similar to the previous one, except with an additional data structure that'll reduce the overall complexity to O(nlogn).  
  
The wikipedia seems no help. The explanation is contrived and not easy to visualize. Hope this post will clear a lot of doubts. So we need 3 arrays for solving an instance of LIS.  
  
M\[i\] - where M\[i\] is the minimum ending element of a increasing subsequence of length _i._ This is the key part of the new algorithm. Unlike the earlier solution where we kept the longest length discovered at index _i_ , we store an Array which holds the minimum value of a subsequence of length _i._  
I\[i\] - where _M\[i\] = A\[I\[i\]\]_ simply put, its the index of M\[i\] in the input Array. The length will be the same as M\[i\]. Both increase in size together. To define it, I\[i\] is the index of the minimum ending element of an increasing subsequence of length _i. _  
P\[i\] - where P\[i\] is the index of the previous member of the longest subsequence. It's for reconstructing the subsequence. You don't need this, if you're only interested in the length of the subsequence.  
  
Initially, M\[0\] = 0 (or Integer.MIN\_VALUE) and I\[0\] = -1 because a zero length subsequence is kind of a null set.  
  
So the algorithm goes like this  
  
  

1.   For i = 0 to n - 1
2.  j = binarySearch(M, A\[i\]) #Such that M\[j-1\] < A\[i\] < M\[j\]
3.  M\[j\] = A\[i\]
4.  I\[j\] = i
5.  P\[i\] = I\[j-1\] #The index of the subsequence of the length j 

Very well, what does it all mean, though?

  

Ok, so lets understand the motivation behind the _M\[\]_ array. Whenever we have a new element A\[i\], we try to "place it" at the end of  the longest increasing subsequence we have encountered yet without breaking the increasing property. But where do I place it?  Since A\[i\] is the last element we have seen so far, there is no other place but the end of the known subsequences. If you decide to insert A\[i\] into an earlier position, though the subsequence will be legal, it wouldn't be optimal.  The M\[\] array is basically keeping track of _len(M)_ increasing subsequences at any time. So A\[i\] can be appended to one of them, the best one is the subsequence of length j where M\[j-1\] < A\[i\] < M\[j\].  
  
Clearly, we can't extend the subsequence of length j since _M\[j\] > A\[i\]_ (it wouldn't be increasing otherwise). We could insert A\[i\] into a subsequence of length k < j, but that wouldn't be the optimal one. So instead we're going to modify the existing subsequence of length j so that the last element is _A\[i\]_ instead of a previously occurring element. At this point we're going to assign M\[j\] = A\[i\].  What this effectively means is that, we have discovered a increasing subsequence of length j that ends with A\[i\]. If we ever wanted to extend a subsequence ie, insert M\[j+1\] it has to be at least M\[j\] (ie A\[i\])

  

Notice when we're inserting or replacing elements in _M\[\]_  we are creating a sorted array. So we can run a binary search on the array. Here's the O(logn) component of the algorithm.

  

Assigning _I\[j\] = i_, is pretty straightforward, we simply remember the index of the new element in _M\[\]. _

_P\[i\] = I\[j - 1\]_, this requires an explanation. Remember the _P\[\]_ array holds the index of the previous member of the increasing subsequence. So if I have just inserted/replaced the last element of a subsequence of length _j_, the previous element is the last element of the optimal increasing subsequence of length _j - 1,_ which is conveniently _I\[j - 1\]._ Finally we simply backtrack the P array to obtain the subsequence in reverse order.

  

  

Full source code [here.](https://github.com/st0le/lost-in-compilation/blob/master/longest_increasing_subsequence.py)