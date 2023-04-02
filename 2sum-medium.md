---
title: '2SUM - Medium'
date: 2013-06-29T17:01:00.002-07:00
draft: false
url: /2013/06/2sum-medium.html
tags: 
- computer science
- algorithm
- medium
- interview question
---

>   
> Problem : Given an array with distinct elements. Find out if there exists an instance where sum of two distinct elements is equal to a given constant K. Say, A = \[1,2,3,4\], K = 7. Output should be 3,4

The naive solution for this problem is pretty trivial. Brute force every pair-sum and check if the sum is K. You could be a little smart about this. You initially sort the array O(nlogn) and iterate the array pairwise and quit when the sum exceeds K, you can quit the inner loop since the array is sorted the sum can only increase.  
  
For the rest of the article, I'll be assuming K = 0, this doesn't affect the solutions in any way and it's trivial to introduce a new variable into the code without major changes.  
  
Here's the code, should be easy to follow... I'll be using Java today.  
  
  
Now that the naive solution is out of the way, let's try and do some clever stuff. So notice we can afford to sort the array since the brute solution was already O(n^2) (which is the higher order term). Now a very big advantage of a sorted array is we can search it in O(logn), so instead of the inner loop doing a linear search for (K-A\[i\]), we perform a Binary Search. The solution now drops to O(nlogn).  
  

Now the obvious question is, Can this be done linearly? The answer is yes, but at the cost of some space. We introduce a hash set _h,_ while iterating we check if the hash set contains the value (K - A\[i\]). If it does, we return _A\[i\] and K - A\[i\]._ If it isn't present, we add _A\[i\]_ into the set and move to the next element. What we've essentially done is replace the O(logn) search of the previous algorithm with a O(1) membership check. The Time Complexity is now O(n) and Space Complexity is also O(n).  
  
The Code as follows.

If for some special case, we are already given a sorted array, then we can still solve this in linear time. The algorithm is pretty simple. I'll explain with an example. The code is self explanatory.  
  
We maintain two indices left and right. The left one points to the beginning of the array (ie the minimum element) and the right index is equal to the last element (ie the maximum element). Now we calculate _S_ where _S = A\[left\] + A\[right\]._ There are 3 cases.  
  
  

1.  S == K, which is the best case scenario. We found the pair (A\[left\], A\[right\]) whose sum = K
2.  S > K, Now if the sum is greater than K, then it means the right element is more than it should be. We want to reduce S, if we increment _left_, S will increase which doesn't help. If we decrement _right,_ the sum will decrease. Note, we don't decrement _left,_ the part of the array before _left_ has already been processed to not contain the solution.
3.  If S < K, as you can imagine, since S is lower than the required sum, we need to "add" more value to it, hence we increment _left. _

The process repeats till _left < right,_ at which point you can conclude there is no solution.

  

Let's take a short example, say the array is \[-10,-5,-2,0,1,2,3\], K = 0

  
  

1.  left = 0, right = 6, A\[left\] = -10, A\[right\] = 3, S = -7, Since S < 0, we increment _left_
2.  left = 1, right = 6, A\[left\] = -5, A\[right\] = 3, S= -2, Since S < 0, we increment _left_
3.  left = 2, right = 6, A\[left\] = -2, A\[right\] = 3, S = 1, Since S > 0, we decrement _right_
4.  left = 2, right = 5, A\[left\] = -2, A\[right\] = 2, S = 0, we found the solution.

Hopefully, that helps. Here's the code that implements the above. Again, this only works with a sorted array. The Complexity is Linear since at each iteration one element is eliminated.

  

  

  

You can find the entire source to the program [here](https://github.com/st0le/lost-in-compilation/blob/master/TwoSum.java)